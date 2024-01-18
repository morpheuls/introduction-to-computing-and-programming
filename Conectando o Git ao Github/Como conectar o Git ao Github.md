# **Configuração do Git e Conexão com o GitHub no Ubuntu e Windows**

Este guia fornece instruções passo a passo para configurar o Git no Ubuntu, no Windows e conectar-se ao GitHub usando uma chave SSH.

## **1. Usando Linux Ubuntu** 

### **1.1. Instalação do Git no Ubuntu**
```bash
sudo apt-get update
sudo apt-get install git
git --version  # Verifica a instalação do Git
```

### **1.2. Configurar Git**
Configure seu nome de usuário e email para identificação em seus commits.

```bash
git config --global user.name "seu nome"
git config --global user.email "seu-email@dominio.com"
```
### **1.2.1 Configurar Git**
Verificar o nome de usuário e email salvos.
```bash
git config --global user.name
```
```bash
git config --global user.email
```
### **1.3. Gerar Chave SSH**
Gere uma nova chave SSH para se conectar com o GitHub.
```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@dominio.com"
# Pressione Enter para padrão e opcionalmente defina uma senha
```
OBS: Uma chave SSH é a credencial de acesso para o protocolo de rede SSH (shell seguro). Esse protocolo de rede segura autenticado e criptografado é usado para comunicação remota entre máquinas em rede aberta não segura.

### **1.4. Adicionar a Chave SSH ao Agente SSH**
Inicialize e adicione sua chave SSH ao agente SSH.
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
OBS: O SSH (Secure Shell) é um protocolo usado para acessar servidores remotos de forma segura. Ao trabalhar com Git e GitHub, por exemplo, a SSH é frequentemente utilizada para estabelecer uma conexão segura entre sua máquina local e o repositório remoto no GitHub.

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
### **1.6. Testar Conexão SSH com GitHub**
Verifique se a configuração de SSH está correta.
```bash
ssh -T git@github.com
```

### **1.7. Clonar Repositório via SSH**
Clone um repositório usando SSH.
```bash
git clone git@github.com:usuario/repositorio.git
```

### **1.8. Trabalhar com o Repositório**
Faça alterações, confirme e envie para o GitHub.
```bash
git add .
git branch -M main
git commit -m "mensagem do commit"
git push origin main
```

### **1.9. Ferramentas Adicionais e Dicas**
- github.dev: Para alterações complexas direto no navegador.
- GitHub Desktop ou VS Code: Para uma interface gráfica do Git.

## **2. Usando Windows**

### **2.1. Instalação do Git no Windows**
Visite o site oficial [git-scm.com](https://git-scm.com/) e baixe a versão mais recente do Git para Windows. Durante a instalação, certifique-se de marcar a opção que permite ao Git rodar no prompt de comando do Windows.

### **2.2. Configurar Git**
Abra o Git Bash (instalado com o Git) e configure seu nome de usuário e email para identificação nos seus commits.
```bash
git config --global user.name "seu nome"
git config --global user.email "seu-email@dominio.com"
```

### **2.3.Gerar Chave SSH**
Ainda no Git Bash, gere uma nova chave SSH para se conectar com o GitHub.
```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@dominio.com"
# Pressione Enter para padrão e opcionalmente defina uma senha
```

### **2.4. Adicionar a Chave SSH ao Agente SSH**
Adicione a chave SSH gerada ao agente SSH.
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

### **2.5. Adicionar Chave SSH ao GitHub**
Copie a chave SSH gerada para a área de transferência.
```bash
clip < ~/.ssh/id_rsa.pub
# No GitHub, vá para Settings > SSH and GPG keys > New SSH key e cole a chave
```

### **2.6. Testar Conexão SSH com GitHub**
Teste a conexão SSH com o GitHub para verificar a configuração.
```bash
ssh -T git@github.com
```

### **2.7. Clonar Repositório via SSH**
Use o Git Bash para clonar um repositório usando SSH.
```bash
git clone git@github.com:usuario/repositorio.git
```

### **2.8. Trabalhar com o Repositório**
Faça alterações locais nos arquivos, adicione ao Git, faça um commit e envie para o GitHub.
```bash
git add .
git commit -m "mensagem do commit"
git push origin main
```

### **2.9. Ferramentas Adicionais e Dicas**
- GitHub Desktop: Para uma interface gráfica de usuário para Git no Windows.
- VS Code: Editor de código com suporte integrado para Git.


## **3. Conclusões e Referências**
Este guia abrangente oferece um caminho claro para configurar o Git tanto no Ubuntu quanto no Windows, além de conectar-se ao GitHub usando chaves SSH. Estes passos são fundamentais para estabelecer um fluxo de trabalho eficiente em desenvolvimento de software e colaboração em projetos de código aberto ou privados.

### **3.1. Conclusões:**
- 1. **Flexibilidade e Importância do Git**: A configuração do Git e a conexão com o GitHub são habilidades essenciais para desenvolvedores modernos. O Git permite um controle de versão robusto e flexível, enquanto o GitHub facilita a colaboração e o compartilhamento de código.
- 2. **Chave SSH para Segurança**: Usar chaves SSH para se conectar ao GitHub proporciona uma camada adicional de segurança. Isso evita a necessidade de inserir credenciais repetidamente, mantendo uma conexão segura.
- 3. **Ferramentas e Integrações**: Ferramentas como GitHub Desktop e VS Code melhoram a experiência do usuário, oferecendo interfaces gráficas intuitivas e integrações úteis para gerenciamento de código.

### **3.2. Referências:**
- Documentação Oficial do Git: [Git Documentation](https://git-scm.com/doc). Acesso em 13/01/2024.
- Documentação Oficial do GitHub: [GitHub Docs](https://docs.github.com/). Acesso em 13/01/2024.
- Tutorial de SSH e Git: [GitHub SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh). Acesso em 13/01/2024.
- O que é chave SSH do Git?:[atlassian](https://www.atlassian.com/br/git/tutorials/git-ssh). Acesso em 18/01/2024.

Este guia é uma compilação de melhores práticas e recomendações derivadas dessas fontes confiáveis. Ele visa simplificar o processo de configuração e uso do Git e GitHub, tornando-o acessível tanto para iniciantes quanto para usuários experientes.

Lembre-se de que a prática constante e a exploração de recursos adicionais são chaves para se tornar proficientes no uso do Git e GitHub. É bom sempre estar atualizado com as últimas atualizações e práticas recomendadas dessas ferramentas consultando sempre as devidas documentações e suas comunidades.

Made with 💜 by @morpheuls

