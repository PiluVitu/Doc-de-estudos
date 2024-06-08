 Instale o WSL

```powershell
wsl --install
```

> **REINICIE O PC DEPOIS DESSA INSTALAÇÃO** 

## Defina suas credênciais 

## Atualize suas dependências 

```bash 
sudo apt update && sudo apt upgrade
```

[Instalar o WSL | Microsoft Learn](https://learn.microsoft.com/pt-br/windows/wsl/install)

# ZSH 

```bash 
sudo apt install zsh
```

![](Pasted%20image%2020240315151906.png)

## Oh My ZSH

```bash
sh -c "$(curl -fsSL [https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh](https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh "https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh"))"
```

## Plugins para o Oh My ZSH

- Execute o seguinte comando no terminal
```bash 
git clone [https://github.com/zsh-users/zsh-autosuggestions.git](https://github.com/zsh-users/zsh-autosuggestions.git "https://github.com/zsh-users/zsh-autosuggestions.git") $ZSH_CUSTOM/plugins/zsh-autosuggestions && git clone [https://github.com/zsh-users/zsh-syntax-highlighting.git](https://github.com/zsh-users/zsh-syntax-highlighting.git "https://github.com/zsh-users/zsh-syntax-highlighting.git") $ZSH_CUSTOM/plugins/zsh-syntax-highlighting && git clone [https://github.com/zdharma-continuum/fast-syntax-highlighting.git](https://github.com/zdharma-continuum/fast-syntax-highlighting.git "https://github.com/zdharma-continuum/fast-syntax-highlighting.git") ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting && git clone --depth 1 -- [https://github.com/marlonrichert/zsh-autocomplete.git](https://github.com/marlonrichert/zsh-autocomplete.git "https://github.com/marlonrichert/zsh-autocomplete.git") $ZSH_CUSTOM/plugins/zsh-autocomplete
```

- Adicione no seu .zshrc os seguintes plugins
```zshrc
plugins=(git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-autocomplete)
```

[GitHub - ohmyzsh/ohmyzsh: 🙃 A delightful community-driven (with 2,200+ contributors) framework for managing your zsh configuration. Includes 300+ optional plugins (rails, git, macOS, hub, docker, homebrew, node, php, python, etc), 140+ themes to spice up your morning, and an auto-update tool so that makes it easy to keep up with the latest updates from the community.](https://github.com/ohmyzsh/ohmyzsh?tab=readme-ov-file#using-oh-my-zsh)

# Resetar TERMINAL

```bash
source /home/vinicius/.zshrc
```

> Você pode fazer um alias no .zshrc e colocar esse código lá
# NVM 

```bash 
curl -o- [https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh](https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh "https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh") | bash
```

## Instale a versão lst mais recente 

```bash 
nvm install --lts
```

[GitHub - nvm-sh/nvm: Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions](https://github.com/nvm-sh/nvm?tab=readme-ov-file#long-term-support)

# PNPM

```bash
curl -fsSL [https://get.pnpm.io/install.sh](https://get.pnpm.io/install.sh "https://get.pnpm.io/install.sh") | sh -
```

## Alias Pn
```zshrc
alias pn=pnpm
```

## Comand Line Complete
### Acesse o bash Sudo e digite:

```bash
pnpm install-completion zsh
```

[Motivation | pnpm](https://pnpm.io/7.x/motivation)

# CLI GITHUB

## Instalar o CLI

```bash 
sudo mkdir -p -m 755 /etc/apt/keyrings && wget -qO- [https://cli.github.com/packages/githubcli-archive-keyring.gpg](https://cli.github.com/packages/githubcli-archive-keyring.gpg "https://cli.github.com/packages/githubcli-archive-keyring.gpg") | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \ && sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \ && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] [https://cli.github.com/packages](https://cli.github.com/packages "https://cli.github.com/packages") stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \ && sudo apt update \ && sudo apt install gh -y
```

## Logar no GitHub

```bash
gh auth login
```

## Atualizar  CLI

```bash 
sudo apt update sudo apt install gh
```

[Manual | GitHub CLI](https://cli.github.com/manual/)
