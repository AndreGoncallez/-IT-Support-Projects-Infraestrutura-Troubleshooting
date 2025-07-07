# 📘 Guia de Uso do arquivo unattend.xml para instalação automatizada do Windows 11

---

## 🎯 Objetivo

Este guia explica como usar um arquivo `unattend.xml` para automatizar a instalação do Windows 11, pulando etapas manuais como a criação de conta Microsoft, configuração de região e aceitação da licença.

---

## 🛠️ Passo a passo para uso do unattend.xml

### 1. Preparar o pendrive de instalação

- Crie um pendrive bootável com a ISO do Windows 11 usando ferramentas como Rufus ou Media Creation Tool.

### 2. Inserir o arquivo unattend.xml

- Copie o arquivo `unattend.xml` para a raiz do pendrive ou para a pasta `sources` dentro do pendrive de instalação.

### 3. Iniciar a instalação

- Dê boot pelo pendrive no computador alvo.
- A instalação do Windows 11 detectará automaticamente o arquivo `unattend.xml` e aplicará as configurações definidas.

### 4. O que o unattend.xml faz durante a instalação?

| Item                             | Descrição                                                                                       |
|---------------------------------|------------------------------------------------------------------------------------------------|
| Formata o disco e cria partições | Apaga dados existentes e cria partições adequadas para o Windows                              |
| Escolhe a imagem para instalação | Seleciona qual edição do Windows será instalada (ex: Pro, Home)                               |
| Aceita automaticamente a licença | Evita a tela de termos de licença durante a instalação                                       |
| Cria usuário local               | Cria uma conta local com nome e senha definidos                                              |
| Pula criação de conta Microsoft  | Ignora a necessidade de criar ou conectar conta Microsoft                                   |
| Configura fuso horário e região  | Define idioma, fuso horário e configurações regionais para o Brasil                          |
| Desativa o OOBE interativo       | Evita telas iniciais de configuração após a instalação (como escolha de privacidade)         |
| Define senha para Administrador  | Cria e define a senha para a conta Administrador                                            |
