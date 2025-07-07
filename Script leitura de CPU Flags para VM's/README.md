# 🧪 Diagnóstico de Virtualização VT-x/EPT para VMware + EVE-NG

Este documento fornece um script pronto para verificar se o seu sistema está configurado corretamente para usar **virtualização aninhada** com o **VMware Workstation** — essencial para rodar o EVE-NG e simular redes Cisco, Fortinet, etc.

---

## 📌 O que o script verifica:

- Se a **virtualização está habilitada na BIOS** (`VirtualizationFirmwareEnabled`)
- Se o processador suporta **EPT/SLAT** (Extended Page Tables)
- Se está rodando sob o VMware
- Indicações para correções caso algo esteja desabilitado

---

## ▶️ Como usar:

1. **Abra o PowerShell como Administrador**
2. **Cole ou execute o script abaixo**
3. Analise as respostas: tudo deve aparecer como ✅

---

## 💻 Script PowerShell

```powershell
# Verifica se o script está sendo executado como Administrador
if (-NOT ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) {
    Write-Host "[❌] Por favor, execute como Administrador!" -ForegroundColor Red
    exit
}

Write-Host "`n🔍 Verificando suporte à virtualização via CPU flags..." -ForegroundColor Cyan

# Coleta os dados da CPU via Win32_Processor
$cpu = Get-WmiObject Win32_Processor

# Mostra algumas flags relevantes
Write-Host "`n[🧠] Nome do processador: $($cpu.Name)"
Write-Host "[🧩] Flags de virtualização:"

# Verifica se suporta VMX
if ($cpu.VirtualizationFirmwareEnabled -eq $true) {
    Write-Host "[✅] Virtualization Firmware: Ativado na BIOS"
} else {
    Write-Host "[❌] Virtualization Firmware: DESATIVADO ou não visível pelo sistema" -ForegroundColor Yellow
}

# Verifica se está rodando sob um Hypervisor
if ($cpu.SecondLevelAddressTranslationExtensions -eq $true) {
    Write-Host "[✅] SLAT (EPT): Suportado"
} else {
    Write-Host "[❌] SLAT (EPT): Não suportado ou não visível" -ForegroundColor Yellow
}

# Adicional - Verifica se está rodando sob ambiente virtual
$isVirtual = Get-WmiObject -Class Win32_ComputerSystem | Select-Object -ExpandProperty Model
if ($isVirtual -match "VMware") {
    Write-Host "[ℹ️] Esta máquina está rodando dentro do VMware."
}

Write-Host "`n[✔️] Diagnóstico concluído."
```

---

## 💡 Dica final

Se o script mostrar ❌ em alguma parte, revise:

- BIOS/UEFI: ative `Intel VT-x`, `VT-d`, `EPT`, `SVM`
- Desative Hyper-V:
  ```powershell
  bcdedit /set hypervisorlaunchtype off
  ```
- Desative o **Isolamento de Núcleo**:
  ```
  Configurações > Segurança do Windows > Segurança do dispositivo > Isolamento de núcleo
  ```
