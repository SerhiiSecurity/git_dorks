# GitHub Dorking Guide

## Що таке GitHub Dorking?
GitHub Dorking — це спосіб шукати чутливі дані в публічних репозиторіях GitHub з допомогою специфічних пошукових запитів.

## Як формується запит GitHub Dorking?

1. Беремо адресу GitHub Search:
   ```
   https://github.com/search?q=
   ```  
2. Додаємо назву сайту (`"example.com"`) або без доменного розширення (`"example"`).
3. Додаємо `%20` (пробіл) і пошукову фразу (наприклад, `password`).

**Приклад запиту:**
```
https://github.com/search?q="example.com"%20password&type=Code
```

## Приклади запитів

### Пошук витоків даних

#### Паролі у вихідному коді
```
"ГІТ%22САЙТ%22+password&type=Code"
"ГІТ%22САЙТ_БС%22+password&type=Code"
```

#### паролі у вихідному коді 
```
"ГІТ%22САЙТ%22+password&type=Code"  
"ГІТ%22САЙТ_БС%22+password&type=Code"
```

#### витік токенів для npm-пакетів  
```
"ГІТ%22САЙТ%22+npmrc%20_auth&type=Code"  
"ГІТ%22САЙТ_БС%22+npmrc%20_auth&type=Code"
```

#### витік конфігурацій Docker  
```
"ГІТ%22САЙТ%22+dockercfg&type=Code"  
"ГІТ%22САЙТ_БС%22+dockercfg&type=Code"
```

#### витік приватних ключів SSL/SSH  
```
"ГІТ%22САЙТ%22+pem%20private&type=Code"  
"ГІТ%22САЙТ_БС%22+extension:pem%20private&type=Code"
```

#### SSH-приватні ключі  
```
"ГІТ%22САЙТ%22+id_rsa&type=Code"  
"ГІТ%22САЙТ_БС%22+id_rsa&type=Code"
```

#### AWS Access Key ID  
```
"ГІТ%22САЙТ%22+aws_access_key_id&type=Code"  
"ГІТ%22САЙТ_БС%22+aws_access_key_id&type=Code"
```

#### конфігурація S3  
```
"ГІТ%22САЙТ%22+s3cfg&type=Code"  
"ГІТ%22САЙТ_БС%22+s3cfg&type=Code"
```

#### файл `.htpasswd` (облікові дані Basic Auth)  
```
"ГІТ%22САЙТ%22+htpasswd&type=Code"  
"ГІТ%22САЙТ_БС%22+htpasswd&type=Code"
```

#### витік облікових даних Git  
```
"ГІТ%22САЙТ%22+git-credentials&type=Code"  
"ГІТ%22САЙТ_БС%22+git-credentials&type=Code"
```

#### паролі у `.bashrc`  
```
"ГІТ%22САЙТ%22+bashrc%20password&type=Code"  
"ГІТ%22САЙТ_БС%22+bashrc%20password&type=Code"
```

#### конфігурація SSH (`sshd_config`)  
```
"ГІТ%22САЙТ%22+sshd_config&type=Code"  
"ГІТ%22САЙТ_БС%22+sshd_config&type=Code"
```

#### Slack-токени (`xoxp`, `xoxb`, `xoxa`)  
```
"ГІТ%22САЙТ%22+xoxp%20OR%20xoxb%20OR%20xoxa&type=Code"  
"ГІТ%22САЙТ_БС%22+xoxp%20OR%20xoxb&type=Code"
```

#### секретний ключ (`SECRET_KEY`)  
```
"ГІТ%22САЙТ%22+SECRET_KEY&type=Code"  
"ГІТ%22САЙТ_БС%22+SECRET_KEY&type=Code"
```

#### клієнтський секрет (`client_secret`)  
```
"ГІТ%22САЙТ%22+client_secret&type=Code"  
"ГІТ%22САЙТ_БС%22+client_secret&type=Code"
```

#### GitHub-токен  
```
"ГІТ%22САЙТ%22+github_token&type=Code"  
"ГІТ%22САЙТ_БС%22+github_token&type=Code"
```

#### API-ключ  
```
"ГІТ%22САЙТ%22+api_key&type=Code"  
"ГІТ%22САЙТ_БС%22+api_key&type=Code"
```

#### FTP-доступ  
```
"ГІТ%22САЙТ%22+FTP&type=Code"  
"ГІТ%22САЙТ_БС%22+FTP&type=Code"
```

#### секрети додатків (`app_secret`)  
```
"ГІТ%22САЙТ%22+app_secret&type=Code"  
"ГІТ%22САЙТ_БС%22+app_secret&type=Code"
```

#### файл `passwd`  
```
"ГІТ%22САЙТ%22+passwd&type=Code"  
"ГІТ%22САЙТ_БС%22+passwd&type=Code"
```

#### файл `.env`  
```
"ГІТ%22САЙТ%22+.env&type=Code"  
"ГІТ%22САЙТ_БС%22+.env&type=Code"
```

#### конфігурація `beanstalkd.yml`  
```
"ГІТ%22САЙТ%22+beanstalkd.yml&type=Code"  
"ГІТ%22САЙТ_БС%22+beanstalkd.yml&type=Code"
```

#### файл `deploy.rake`  
```
"ГІТ%22САЙТ%22+deploy.rake&type=Code"  
"ГІТ%22САЙТ_БС%22+deploy.rake&type=Code"
```

#### облікові дані MySQL  
```
"ГІТ%22САЙТ%22+mysql&type=Code"  
"ГІТ%22САЙТ_БС%22+mysql&type=Code"
```

#### файл `credentials`  
```
"ГІТ%22САЙТ%22+credentials&type=Code"  
"ГІТ%22САЙТ_БС%22+credentials&type=Code"
```

#### збережені паролі (`PWD`)  
```
"ГІТ%22САЙТ%22+PWD&type=Code"  
"ГІТ%22САЙТ_БС%22+PWD&type=Code"
```

#### історія команд Bash  
```
"ГІТ%22САЙТ%22+.bash_history&type=Code"  
"ГІТ%22САЙТ_БС%22+.bash_history&type=Code"
```

#### файли `.sls`  
```
"ГІТ%22САЙТ%22+.sls&type=Code"  
"ГІТ%22САЙТ_БС%22+.sls&type=Code"
```

#### файл `secrets`  
```
"ГІТ%22САЙТ%22+secrets&type=Code"  
"ГІТ%22САЙТ_БС%22+secrets&type=Code"
```

#### конфігурація `composer.json`  
```
"ГІТ%22САЙТ%22+composer.json&type=Code"  
"ГІТ%22САЙТ_БС%22+composer.json&type=Code"
```

## Застереження
GitHub Dorking потрібно використовувати тільки для етичних методів. За незаконне використання ви несете повну відповідальність!
