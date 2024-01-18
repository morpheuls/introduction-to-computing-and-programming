
<div id='configuração-do-git-e-conexão-com-o-github-no-ubuntu-e-windows'>
  
# **Configuração do Git e Conexão com o GitHub no Ubuntu e Windows**

<div/>

Este guia fornece instruções passo a passo para configurar o Git no Ubuntu, no Windows e conectar-se ao GitHub usando uma chave SSH.
### **Índice**

- [Configuração do Git e Conexão com o GitHub no Ubuntu e Windows](#configuração-do-git-e-conexão-com-o-github-no-ubuntu-e-windows)
  * [1. Usando Linux Ubuntu](#1-Usando-Linux-Ubuntu)
    + [1.1. Instalação do Git no Ubuntu](#11-instalação-do-git-no-ubuntu)
    + [1.2. Configurar Git](#12-configurar-git)
    + [1.2.1 Verificar nome de usuário e email](#121-Verificar-usuario-e-email)
    + [1.3. Gerar Chave SSH](#13-gerar-chave-ssh)
    + [1.4. Adicionar a Chave SSH ao Agente SSH](#14-adicionar-a-chave-ssh-ao-agente-ssh)
    + [1.5. Adicionar Chave SSH ao GitHub](#15-adicionar-chave-ssh-ao-github)
    + [1.6. Testar Conexão SSH com GitHub](#16-testar-conexão-ssh-com-github)
    + [1.7. Clonar Repositório via SSH](#17-clonar-repositório-via-ssh)
    + [1.8. Trabalhar com o Repositório](#18-trabalhar-com-o-repositório)
    + [1.9. Ferramentas Adicionais e Dicas](#19-ferramentas-adicionais-e-dicas)
  * [2. Usando Windows](#2-usando-windows)
    + [2.1. Instalação do Git no Windows](#21-instalação-do-git-no-windows)
    + [2.2. Configurar Git](#22-configurar-git)
    + [2.3. Gerar Chave SSH](#23-gerar-chave-ssh)
    + [2.4. Adicionar a Chave SSH ao Agente SSH](#24-adicionar-a-chave-ssh-ao-agente-ssh)
    + [2.5. Adicionar Chave SSH ao GitHub](#25-adicionar-chave-ssh-ao-github)
    + [2.5.1 Caso o comando clip não funcione](#251-caso-o-comando-clip-não-funcione)
    + [2.6. Testar Conexão SSH com GitHub](#26-testar-conexão-ssh-com-github)
    + [2.7. Clonar Repositório via SSH](#27-clonar-repositório-via-ssh)
    + [2.8. Trabalhar com o Repositório](#28-trabalhar-com-o-repositório)
    + [2.9. Ferramentas Adicionais e Dicas](#29-ferramentas-adicionais-e-dicas)
  * [3. Conclusões e Referências](#3-conclusões-e-referências)
    + [3.1. Conclusões](#31-conclusões)
    + [3.2. Referências](#32-referências)

<div id='1-Usando-Linux-Ubuntu'>

## **1. Usando Linux Ubuntu** 
Estaremos usando a distribuição Linux Ubuntu 22.04, foi testado também na distruibuição ZorinOS 16 e provalvemente funcionará nas demais.E também usamos o Windows 10 e 11.

<div/>

<div id='11-instalação-do-git-no-ubuntu'>

### **1.1. Instalação do Git no Ubuntu**
```bash
sudo apt-get update
sudo apt-get install git
git --version  # Verifica a instalação do Git
```
OBS: Para estabelecer uma conexão eficiente entre o Git e o GitHub, é essencial possuir uma conta no GitHub. Isso é necessário porque durante a configuração do Git, você precisará associar o mesmo endereço de e-mail registrado na sua conta do GitHub. Essa associação é crucial para garantir uma comunicação segura e autenticada entre o seu sistema local e os repositórios remotos no GitHub.

<div/>
  
<div id='12-configurar-git'>
  
### **1.2. Configurar Git**
Configure seu nome de usuário e email para identificação em seus commits.

```bash
git config --global user.name "seu nome"
git config --global user.email "seu-email@dominio.com"
```

<div/>
  
<div id='121-Verificar-usuario-e-email'>
  
### **1.2.1 Verificar nome de usuário e email**
Verificar o nome de usuário e email salvos no git.
```bash
git config --global user.name
```
```bash
git config --global user.email
```

<div/>
  
<div id='13-gerar-chave-ssh'>
  
### **1.3. Gerar Chave SSH**
Gere uma nova chave SSH para se conectar com o GitHub.
```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@dominio.com"
# Pressione Enter para padrão e opcionalmente defina uma senha
```
OBS: Uma chave SSH é a credencial de acesso para o protocolo de rede SSH (shell seguro). Esse protocolo de rede segura autenticado e criptografado é usado para comunicação remota entre máquinas em rede aberta não segura.

<div/>

<div id='14-adicionar-a-chave-ssh-ao-agente-ssh'>
  
### **1.4. Adicionar a Chave SSH ao Agente SSH**
Inicialize e adicione sua chave SSH ao agente SSH.
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
OBS: O SSH (Secure Shell) é um protocolo usado para acessar servidores remotos de forma segura. Ao trabalhar com Git e GitHub, por exemplo, a SSH é frequentemente utilizada para estabelecer uma conexão segura entre sua máquina local e o repositório remoto no GitHub.

<div/>
  
<div id='15-adicionar-chave-ssh-ao-github'>
  
### **1.5. Adicionar Chave SSH ao GitHub**
Copie sua chave SSH e adicione-a ao seu perfil do GitHub.
```bash
cat ~/.ssh/id_rsa.pub | xclip -selection clipboard
# Cole no GitHub em Settings > SSH and GPG keys > New SSH key
```
OBS: Deve se ter instalado o xclip
```bash
sudo apt install xclip
```

<div/>

<div id='16-testar-conexão-ssh-com-github'>
  
### **1.6. Testar Conexão SSH com GitHub**
Verifique se a configuração de SSH está correta.
```bash
ssh -T git@github.com
```

<div/>

<div id='17-clonar-repositório-via-ssh'>
  
### **1.7. Clonar Repositório via SSH**
Clone um repositório usando SSH.
```bash
git clone git@github.com:usuario/repositorio.git
```

<div/>
  
<div id='18-trabalhar-com-o-repositório'>
  
### **1.8. Trabalhar com o Repositório**
Faça alterações, confirme e envie para o GitHub.
```bash
git add .
git branch -M main
git commit -m "mensagem do commit"
git push origin main
```

<div/>
  
<div id='19-ferramentas-adicionais-e-dicas'>
  
### **1.9. Ferramentas Adicionais e Dicas**
- github.dev: Para alterações complexas direto no navegador.
- GitHub Desktop ou VS Code: Para uma interface gráfica do Git.
  
<div/>
  
<div id='2-usando-windows'>
  
## **2. Usando Windows**

<div/>
  
<div id='21-instalação-do-git-no-windows'>
  
### **2.1. Instalação do Git no Windows**
Visite o site oficial [git-scm.com](https://git-scm.com/) e baixe a versão mais recente do Git para Windows. Durante a instalação, certifique-se de marcar a opção que permite ao Git rodar no prompt de comando do Windows.

<div/>
  
<div id='22-configurar-git'>
  
### **2.2. Configurar Git**
Abra o Git Bash (instalado com o Git) e configure seu nome de usuário e email para identificação nos seus commits.
```bash
git config --global user.name "seu nome"
git config --global user.email "seu-email@dominio.com"
```

<div/>
  
<div id='23-gerar-chave-ssh'>
  
### **2.3.Gerar Chave SSH**
Ainda no Git Bash, gere uma nova chave SSH para se conectar com o GitHub.
```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@dominio.com"
# Pressione Enter para padrão e opcionalmente defina uma senha
```

<div/>
  
<div id='24-adicionar-a-chave-ssh-ao-agente-ssh'>
  
### **2.4. Adicionar a Chave SSH ao Agente SSH**
Adicione a chave SSH gerada ao agente SSH.
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

<div/>
  
<div id='25-adicionar-chave-ssh-ao-github'>
  
### **2.5. Adicionar Chave SSH ao GitHub**
Copie a chave SSH gerada para a área de transferência.
```bash
clip < ~/.ssh/id_rsa.pub
# No GitHub, vá para Settings > SSH and GPG keys > New SSH key e cole a chave
```
OBS: Pode-se usar o comando type mas não abordaremos neste tutorial.

<div/>
  
<div id='251-caso-o-comando-clip-não-funcione'>
  
### **2.5.1 Caso o comando clip não funcione**
Abra o arquivo manualmente:
- Navegue até a pasta .ssh localizada no seu diretório de usuário (geralmente em C:\Users\[SeuNomeDeUsuário]\.ssh).
- Encontre o arquivo id_rsa.pub.
- Abra-o com um editor de texto, como o Bloco de Notas.
Copie o conteúdo manualmente:
- Uma vez aberto, selecione todo o texto (geralmente começa com ssh-rsa) e copie-o usando Ctrl+C.

Cole a chave no GitHub:
- Vá para o GitHub, acesse as configurações da sua conta.
- Navegue até "SSH and GPG keys".
- Clique em "New SSH key" ou "Add SSH key".
- Cole a chave copiada no campo apropriado e salve.

Obs: como uma alternativa para usuários de Windows que desejam uma experiência semelhante ao Unix, o Cygwin pode ser utilizado. O Cygwin é um conjunto de ferramentas de software livre desenvolvidas inicialmente pela Cygnus Solutions, que permite que as várias versões do Microsoft Windows simulem um ambiente de sistema Unix. Esta pode ser uma opção valiosa para quem prefere trabalhar em um ambiente Unix-like no Windows. Para saber mais sobre o projeto Cygwin o link estará nas referências bem como o que é Unix.
OBS2: Nas referências também se encontram alguns comandos para o terminal do Windows.

<div/>
  
<div id='26-testar-conexão-ssh-com-github'>
  
### **2.6. Testar Conexão SSH com GitHub**
Teste a conexão SSH com o GitHub para verificar a configuração.
```bash
ssh -T git@github.com
```

<div/>
  
<div id='27-clonar-repositório-via-ssh'>
  
### **2.7. Clonar Repositório via SSH**
Use o Git Bash para clonar um repositório usando SSH.
```bash
git clone git@github.com:usuario/repositorio.git
```

<div/>
  
<div id='28-trabalhar-com-o-repositório'>
  
### **2.8. Trabalhar com o Repositório**
Faça alterações locais nos arquivos, adicione ao Git, faça um commit e envie para o GitHub.
```bash
git add .
git commit -m "mensagem do commit"
git push origin main
```

<div/>
  
<div id='29-ferramentas-adicionais-e-dicas'>
  
### **2.9. Ferramentas Adicionais e Dicas**
- GitHub Desktop: Para uma interface gráfica de usuário para Git no Windows.
- VS Code: Editor de código com suporte integrado para Git.
  
<div/>

<div id='3-conclusões-e-referências'>
  
## **3. Conclusões e Referências**
Este guia abrangente oferece um caminho claro para configurar o Git tanto no Ubuntu quanto no Windows, além de conectar-se ao GitHub usando chaves SSH. Estes passos são fundamentais para estabelecer um fluxo de trabalho eficiente em desenvolvimento de software e colaboração em projetos de código aberto ou privados.

<div/>
  
<div id='31-conclusões'>
  
### **3.1. Conclusões:**
- 1. **Flexibilidade e Importância do Git**: A configuração do Git e a conexão com o GitHub são habilidades essenciais para desenvolvedores modernos. O Git permite um controle de versão robusto e flexível, enquanto o GitHub facilita a colaboração e o compartilhamento de código.
- 2. **Chave SSH para Segurança**: Usar chaves SSH para se conectar ao GitHub proporciona uma camada adicional de segurança. Isso evita a necessidade de inserir credenciais repetidamente, mantendo uma conexão segura.
- 3. **Ferramentas e Integrações**: Ferramentas como GitHub Desktop e VS Code melhoram a experiência do usuário, oferecendo interfaces gráficas intuitivas e integrações úteis para gerenciamento de código.
OBS: em caso de dúvidas consultar as refêrencias.    
<div/>
  
<div id='32-referências'>
  
### **3.2. Referências:**
- Documentação Oficial do Git: [Git Documentation](https://git-scm.com/doc). Acesso em 13/01/2024.
- Documentação Oficial do GitHub: [GitHub Docs](https://docs.github.com/). Acesso em 13/01/2024.
- Tutorial de SSH e Git: [GitHub SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh). Acesso em 13/01/2024.
- O que é chave SSH do Git?: [Atlassian: O que é chave SSH do Git?](https://www.atlassian.com/br/git/tutorials/git-ssh). Acesso em 18/01/2024.
- Cygwin: [Cygwin](https://www.cygwin.com/). Acesso em 18/01/2024.
- UNIX E LINUX: [UNIX E LINUX](http://www.inf.ufsc.br/~j.barreto/cca/sisop/unixe.htm). Acesso em 18/01/2024.
- CMD: dicas para trabalhar no prompt do Windows: [Alura: CMD: dicas para trabalhar no prompt do Windows](https://www.alura.com.br/artigos/cmd-dicas-para-trabalhar-no-prompt-do-windows?utm_term=&utm_campaign=%5BSearch%5D+%5BPerformance%5D+-+Dynamic+Search+Ads+-+Artigos+e+Conte%C3%BAdos&utm_source=adwords&utm_medium=ppc&hsa_acc=7964138385&hsa_cam=11384329873&hsa_grp=111087461203&hsa_ad=687448474447&hsa_src=g&hsa_tgt=dsa-843358956400&hsa_kw=&hsa_mt=&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=Cj0KCQiAtaOtBhCwARIsAN_x-3L5RDbKJ3gdKQysiJvYArB1MbsCmHQZtM_1yqIVCbFJ3NazodMuTmYaAqkqEALw_wcB). Acesso em 18/01/2024.
- GitHub Desktop. [Documentação do GitHub Desktop](https://docs.github.com/pt/desktop). Acesso em 18/01/2024.
- IDE Visual Studio Code.[Visual Studio Code](https://code.visualstudio.com/). Acesso em 18/01/2024.
  
<div/>
Este guia é uma compilação de melhores práticas e recomendações derivadas dessas fontes confiáveis. Ele visa simplificar o processo de configuração e uso do Git e GitHub, tornando-o acessível tanto para iniciantes quanto para usuários experientes.

Lembre-se de que a prática constante e a exploração de recursos adicionais são chaves para se tornar proficientes no uso do Git e GitHub. É bom sempre estar atualizado com as últimas atualizações e práticas recomendadas dessas ferramentas consultando sempre as devidas documentações e suas comunidades.

Made with 💜 by @morpheuls
<!--Backup revisado ok!-->
