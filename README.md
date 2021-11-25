# Configurando Ambiente de Desenvolvimento Linux (ZorinOS)



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

Agora adicione permita executáveis no binário:

```
sudo chmod +x /usr/local/bin/docker-compose
```



<hr>

## Erros e Soluções

Laravel & Docker: The stream or file "/var/www/html/storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied

```bash
sudo chmod o+w ./storage/ -R
```

dom extension PHP

~~~bash
sudo apt-get install php-xml
~~~

