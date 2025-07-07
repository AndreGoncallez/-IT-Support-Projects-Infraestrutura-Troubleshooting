# 🧪 Diagnóstico de Virtualização VT-x/EPT para VMware + EVE-NG

Este documento fornece um utilitário pronto para verificar se o seu sistema está configurado corretamente para usar **virtualização aninhada** com o **VMware Workstation** — essencial para rodar o EVE-NG e simular redes Cisco, Fortinet, etc.

---

## 📌 O que o script verifica:

- Se a **virtualização está habilitada na BIOS** (`VirtualizationFirmwareEnabled`)
- Se o processador suporta **EPT/SLAT** (Extended Page Tables)
- Se está rodando sob o VMware
- Indicações para correções caso algo esteja desabilitado

---

## 📥 Download do script

👉 Baixe o pacote completo (.zip) com o script PowerShell e instruções .txt:


---

## ▶️ Como usar:

1. **Extraia o arquivo `.zip`**
2. Clique com o botão direito no arquivo `diagnostico_virtualizacao.ps1`
3. Escolha **Executar com PowerShell como administrador**
4. Analise os resultados — tudo deve aparecer como ✅

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

---
