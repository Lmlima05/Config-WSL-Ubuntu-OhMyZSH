# Instalação e Configuração do WSL com Zsh e Oh My Zsh

Como toda vez perco um tempo quando vou subir um novo ambiente, decidi Salvar aqui para facilitar.
Este guia fornece um passo a passo para instalar e configurar o WSL (Windows Subsystem for Linux) com o Zsh e Oh My Zsh.

## Instalação do WSL

### Instalar o WSL:
```sh
wsl --install
```

### Atualizar para a versão mais recente:
```sh
wsl --update
```

### Instalar uma versão específica do Ubuntu (exemplo: 22.04):
```sh
wsl --install -d Ubuntu-22.04
```

## Configuração do Zsh e Oh My Zsh

### Atualizar os pacotes do sistema:
```sh
sudo apt update && sudo apt upgrade -y
```

### Instalar o Zsh:
```sh
sudo apt install zsh -y
```

### Definir o Zsh como shell padrão:
```sh
chsh -s $(which zsh)
```
*OBS: Será necessário fazer logout e escolher a opção correta.*

### Instalar Oh My Zsh:
Oh My Zsh é um framework open-source para gerenciar configurações do Zsh.

#### Instalar dependências:
```sh
sudo apt install curl git -y
```

#### Instalar Oh My Zsh:
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Plugins do Zsh

### Instalar o gerenciador de plugins Zinit:
```sh
bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

### Adicionar plugins ao Zsh:
Abra o arquivo de configuração do Zsh:
```sh
code ~/.zshrc
```
Ou:
```sh
nano ~/.zshrc
```

Adicione ao final do arquivo:
```sh
zinit light zdharma-continuum/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
```

## Instalação de Fontes Nerd Fonts (para ícones)

### Criar diretório para fontes:
```sh
mkdir -p ~/.fonts
```

### Baixar a fonte:
```sh
wget -P ~/.fonts 'https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/BitstreamVeraSansMono.zip'
```

### Instalar dependência para extrair os arquivos:
```sh
sudo apt install unzip -y
```

### Extrair a fonte:
```sh
unzip ~/.fonts/BitstreamVeraSansMono.zip -d ~/.fonts
```

### Instalar outra fonte recomendada:
```sh
sudo apt install fonts-firacode -y
```

### Configurar a fonte no terminal:
Após a instalação, configure a fonte no terminal do Windows (Windows Terminal, VS Code, etc.).
Para instalar no Windows, acesse o diretório de fontes no WSL:
```sh
\\wsl$
```
Em seguida, copie e instale as fontes manualmente.

## Instalação do Tema Powerlevel10k

### Clonar o repositório do tema:
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
```

### Adicionar o tema ao Zsh:
```sh
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

### Alterar a configuração do tema no `.zshrc`:
Abra o arquivo de configuração:
```sh
code ~/.zshrc
```
Altere a linha do tema:
```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

### Configurar ou reconfigurar o Powerlevel10k:
```sh
p10k configure
```
Caso não esteja reconhecendo os ícones na configuração do terminal e terminal do vscode executar os passos abaixo. 

Terminal Windows da Microsoft (a novidade): Abra Configurações ( Ctrl+,), clique no perfil selecionado em Perfis ou em Padrões , clique em Aparência e defina a Fonte como MesloLGS NF.

Visual Studio Code : Abra Arquivo → Preferências → Configurações (PC) ou Código → Preferências → Configurações (Mac), digite terminal.integrated.fontFamilyna caixa de pesquisa na parte superior da aba Configurações e defina o valor abaixo como MesloLGS NF. Consulte [esta captura de tela](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/389133fb8c9a2347929a23702ce3039aacc46c3d/visual-studio-code-font-settings.jpg) para ver como deve ficar ou veja [este problema](https://github.com/romkatv/powerlevel10k/issues/671) para obter informações extras.

---

Com esse guia, você terá um ambiente WSL configurado com Zsh, Oh My Zsh, plugins útis e um tema moderno para melhorar sua experiência no terminal! 🚀

