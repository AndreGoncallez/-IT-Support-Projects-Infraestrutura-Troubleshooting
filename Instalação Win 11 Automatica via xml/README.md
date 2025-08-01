# Passo a Passo: Criando uma Imagem Personalizada do Windows com Instalação Automatizada

Esse guia vai ensinar você a criar uma imagem personalizada do Windows com instalação automatizada, ideal para técnicos, empresas ou quem formata computadores com frequência.

## 🛠️ Etapa 1: Baixe a ISO do Windows
Primeiro, baixe uma ISO oficial do Windows:

- [Windows 11 ISO](https://lnkd.in/gXhwJg2d)
- [Windows 10 ISO](https://lnkd.in/g-baVkSx)

**⚠️** Certifique-se de baixar a versão que corresponde à sua chave (Home, Pro, etc.).

## 🖥️ Etapa 2: Acesse o Gerador de XML
Acesse o site do **Schneegans Unattend Generator** para criar seu arquivo XML personalizado:

- [Schneegans Unattend Generator](https://lnkd.in/gbAzgsSf)

## 🧩 Etapa 3: Preencha o Formulário Passo a Passo

### General Settings
- **Language**: pt-BR (ou en-US, se preferir inglês)
- **Time Zone**: E. South America Standard Time (para Brasil)
- **Computer Name**: Exemplo: `PC-CLIENTE`
- Marque as seguintes opções:
  - [✔️] Accept EULA
  - [✔️] Skip OOBE
  - [✔️] Prevent Local Account Setup (se quiser conta offline)

### User Account
- **User Name**: Exemplo: `admin`
- **Password**: Defina uma senha para o usuário administrador.
- Marque:
  - [✔️] Add to Administrators

### Product Key
- **Product Key**: Digite a chave do Windows se você tiver. Caso contrário, deixe em branco para pular.

### Disk Configuration
- Marque [✔️] **Wipe Disk and Use Entire Disk** (isso irá apagar tudo no disco e usar o espaço inteiro).
- Se preferir, personalize as partições conforme necessário.

### Remove Appx Packages (Opcional)
- Se desejar, marque os aplicativos nativos para remover automaticamente, como **Xbox**, **OneDrive**, etc.

### RunOnce (Scripts Pós-Instalação) (Opcional)
- Adicione scripts que serão executados após a instalação do Windows. Exemplo:
  ```bash
  Start-Process -FilePath "https://lnkd.in/gPpmh4GR" -Wait
💾 Etapa 4: Gere o Arquivo XML
Role até o final da página e clique em Download XML.

O arquivo será baixado com o nome unattend.xml.

🔌 Etapa 5: Monte o Pendrive Bootável
Ferramenta recomendada: Rufus
Baixe o Rufus.

Conecte um pendrive com pelo menos 8 GB de espaço.

Selecione a ISO do Windows que você baixou.

Escolha Image option: "Standard Windows installation".

Selecione o formato GPT + UEFI (ou MBR + BIOS, dependendo do seu PC).

Clique em Start para iniciar a criação do pendrive bootável.

📁 Etapa 6: Copie o Arquivo unattend.xml para o Pendrive
Após criar o boot, abra o pendrive.

Copie o arquivo unattend.xml para a raiz do pendrive.

Renomeie o arquivo para:

autounattend.xml (é importante que o nome seja exatamente esse).

🚀 Etapa 7: Instale o Windows Automaticamente
Insira o pendrive no computador onde deseja instalar o Windows.

Dê boot pelo pendrive (geralmente pressionando F12, F9 ou DEL ao ligar o PC).

O Windows será instalado automaticamente, sem necessidade de interações, com as configurações, conta e idioma já definidos.

✅ Resultado
Você agora tem uma instalação personalizada do Windows com as seguintes características:

Instalação rápida: Não é necessário clicar em nada.

Configuração padronizada: Todos os PCs terão a mesma configuração.

Prático: Ideal para técnicos ou empresas que precisam realizar várias formatações.

Dicas:
Se você for personalizar mais a instalação, como adicionar programas ou remover mais aplicativos, basta editar o arquivo autounattend.xml manualmente.

css
Copiar
Editar

Agora o **README.md** está completo, com todas as etapas organizadas de forma clara e objetiva. Esse formato vai ajudar a seguir o passo a passo de forma fluida. Se precisar de algo mais, é só avisar!
