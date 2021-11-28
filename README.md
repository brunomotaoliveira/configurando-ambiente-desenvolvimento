# Configurando Ambiente de Desenvolvimento Linux

## Personalizando o Terminal

- ##### Instalando o Oh My Zsh:

  > - Instale o ZSH: <code>*apt install zsh*</code>
  >
  > - Instale Oh My Zsh: <code>curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh; zsh</code>
  >
  > - Se o Shell não for alterado use esse comando: <code>sudo usermod --shell $(which zsh) $USER</code>. Depois reabra o terminal.
  >
  >   

- ##### Recursos:

  - <u>**zsh-syntax-highliting**</u>: Exibe se o comando está certo(verde) ou errado(vermelho)

    ~~~bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ~~~

    Use o comando <code>sudo nano ~./zshrc</code> ,  e em plugins. Adicione o <code>zsh-syntax-highlighting</code>. Irá ficar assim:

    ~~~bash
    plugins=(
    git
    dnf
    zsh-syntax-highlighting
    )
    ~~~

  - **<u>zsh-autosuggestions</u>** : sugestão de comandos. 

    ~~~bash
    git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
    ~~~

    Use o comando <code>sudo nano ~./zshrc</code>, e em plugins abaixo de highliting. Adicione <code>zsh-autosuggestions</code>

    

- ##### Visual:

  - **<u>Fonte:</u>** https://github.com/ryanoasis/nerd-fonts/releases/download/v1.2.0/Hack.zip

    Extrair a fonte em ~.fonts:

    ~~~bash
    mkdir ~/.fonts && cd ~/.fonts
    unzip ~/Downloads/Hack.zip
    ~~~

    E depois escolha a fonte no terminal.

  - <u>**Powerlevel9k**</u>: tema para o terminal <code>git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k</code>.

    - Depois execute o comando: <code>sudo nano ~/.zshrc</code>. E altere o <code>ZSH_THEME</code> para <code>powerlevel9k/powerlevel9k</code> e abaixo adicione: <code>POWERLEVEL9K_MODE="nerdfont-complete"</code> para habilitar os icones. Fecha e abra o terminal.

  - **<u>Dracula Theme para o Gnome Terminal</u>** : <code>sudo apt-get install dconf-cli</code>

    ~~~bash
    git clone https://github.com/dracula/gnome-terminal
    cd gnome-terminal
    ~~~

    E depois: <code>./install.sh</code>

    > https://draculatheme.com/gnome-terminal

<hr>

### Atualizando a versão do composer para a 2

Se não conseguir atualizar o composer com o <code>composer self-update --2</code>, remova o mesmo com o seguinte comando:

<code>sudo apt remove composer</code>

Instale a última versão do composer:

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

php -r "if (hash_file('sha384', 'composer-setup.php') === '906a84df04cea2aa72f40b5f787e49f22d4c2f19492ac310e8cba5b96ac8b64115ac402c8cd292b8a03482574915d1a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

php -r "unlink('composer-setup.php');"
```

Para verificar a versão instalada utilize: <code>composer --version</code>

<hr>

## Instalar o Docker Compose

Primeiro faça download da versão atual do Docker: 

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Agora permita executáveis no binário:

```
sudo chmod +x /usr/local/bin/docker-compose
```



<hr>

## Erros e Soluções

- Laravel & Docker: The stream or file "/var/www/html/storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied

  ~~~bash
  sudo chmod o+w ./storage/ -R
  ~~~

- **dom extension PHP**

  ~~~bash
  sudo apt-get install php-xml
  ~~~

  

- **Laravel command not found**

  1 - Após executar o comando <code>composer global require laravel/installer</code> você terá o diretório de configuração do composer disponivel, geralmente dentro do seu Home em <code>./config/composer/vendor/bin</code>

  

  2- Verificado se está lá seus arquivos, você vai executar o comando <code>nano ~/.bashrc</code> ou <code>nano ~/.zshrc</code> dependendo do seu terminal. E exportar o seu arquivo de configuração composer com o seguinte comando:

  ~~~bash
  export PATH="$PATH:$HOME/.config/composer/vendor/bin"
  ~~~

  Depois de salvar. Atualize seu <code>.bashrc</code> ou <code>.zshrc</code> com o comando no terminal:

  ~~~bash
  source ~/.bashrc
  source ~/.zshrc
  ~~~

  E provavelmente seu comando <code>laravel</code> será reconhecido.
