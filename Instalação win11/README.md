# 🖥️ Instalação do Windows 11 Offline + Verificação de Requisitos

> Guia técnico completo para instalação do Windows 11 **sem conexão com a internet** e validação dos requisitos mínimos em máquinas corporativas ou pessoais.

---

## 📌 Objetivo

Este guia auxilia técnicos e profissionais de suporte a:

- Instalar o **Windows 11** de forma **offline** (sem exigência de conexão ou conta Microsoft).
- Validar se o equipamento atende aos **requisitos mínimos de hardware e compatibilidade**.

---

## ✅ Requisitos Mínimos para Windows 11

| Componente | Requisito Mínimo |
|-----------|------------------|
| Processador | 1GHz, 2 ou mais núcleos, 64 bits, compatível com Windows 11 |
| RAM        | 4 GB |
| Armazenamento | 64 GB ou mais |
| Firmware   | UEFI com Secure Boot |
| TPM        | Versão 2.0 obrigatória |
| Placa Gráfica | Compatível com DirectX 12 ou posterior com driver WDDM 2.0 |
| Tela       | > 9” com resolução HD (720p) |
| Conexão    | Conexão com internet só é obrigatória para contas Microsoft, mas pode ser contornada |

---

## 🔍 Como Verificar a Compatibilidade

1. **Ferramenta oficial da Microsoft:**
   - Baixe a [Verificação de Integridade do PC](https://aka.ms/GetPCHealthCheckApp).
   - Execute e aguarde o diagnóstico.

2. **Alternativa com script PowerShell:**
   ```powershell
   Get-WmiObject -Class Win32_ComputerSystem
   Get-WmiObject -Class Win32_Processor
   Get-TPM
   ```
   > Últil para inventário técnico em redes ou auditorias manuais.

---

## 💾 Instalação do Windows 11 Offline (Sem Internet)

### ⚖️ Passo a Passo

1. **Baixe a ISO do Windows 11:**
   - Acesse: [https://www.microsoft.com/pt-br/software-download/windows11](https://www.microsoft.com/pt-br/software-download/windows11)

2. **Crie um Pendrive Bootável com Rufus:**
   - [Download do Rufus](https://rufus.ie/)
   - Selecione a opção:  
     ✅ **“Remover requisito de conta Microsoft”**  
     ✅ **“Remover conexão obrigatória com a internet”**  
     ✅ “Remover verificação de TPM e Secure Boot” (se necessário)

3. **Configure o Boot no Setup (BIOS):**
   - Pressione `DEL`, `F2`, `F12` ou `ESC` no boot.
   - Selecione o pendrive na ordem de boot.
   - Certifique-se de que **Secure Boot** está habilitado, e **CSM** desabilitado.

4. **Siga a instalação normalmente:**
   - Escolha “Instalar agora”.
   - Na tela de conta Microsoft, pressione `Shift + F10`, abra o prompt e digite:
     ```cmd
     oobe\bypassnro
     ```
   - O sistema será reiniciado e passará para o modo offline/local.
   - Agora você poderá criar uma **conta local** sem conexão.

---

## ⚠️ Observações Importantes

- Algumas versões recentes do Windows 11 **bloqueiam o modo offline**. O Rufus com opção de remoção de requisitos resolve isso.
- O **modo bypass** também funciona com `oobe\` comandos como:
  ```cmd
  oobe\BypassMSA
  ```
- Manter o pendrive atualizado é recomendado para compatibilidade com drivers modernos.

---

## 🛠️ Ferramentas Úteis

| Ferramenta | Finalidade | Link |
|-----------|------------|------|
| Rufus     | Criar pendrive bootável e remover restrições | [rufus.ie](https://rufus.ie) |
| Verificador de Compatibilidade | Requisitos Windows 11 | [Baixar](https://aka.ms/GetPCHealthCheckApp) |
| Ventoy    | Multiboot USB | [ventoy.net](https://www.ventoy.net) |
| ProduKey  | Backup de chaves de licença | [nirsoft.net](https://www.nirsoft.net/utils/product_cd_key_viewer.html) |

---

## 📄 Licenciamento e Ativação

- Durante a instalação offline, é possível pular a chave do produto.
- Após a instalação, ative com uma chave original ou vinculada à conta Microsoft posteriormente.

---

