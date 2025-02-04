# GitHub Dorking Guide

## Що таке GitHub Dorking?
GitHub Dorking — це спосіб шукати чутливі дані в публічних репозиторіях GitHub з допомогою специфічних пошукових запитів.

## Як формується запит GitHub Dorking?

1. Беремо адресу GitHub Search:
   ```
   https://github.com/search?q=
   ```  
2. Додаємо назву SITEу (`"example.com"`) або без доменного розширення (`"example"`).
3. Додаємо `%20` (пробіл) і пошукову фразу (наприклад, `password`).

**Приклад запиту:**
```
https://github.com/search?q="example.com"%20password&type=Code
```

## Приклади запитів

### Пошук витоків даних
$GIT_SITE = https://github.com/search?q=
$SITE  = example.com
$SITE_WITHOUT_SUFFIX  = example

#### паролі у вихідному коді 
```
"$GIT_SITE%22$SITE%22+password&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+password&type=Code"
```

#### витік токенів для npm-пакетів  
```
"$GIT_SITE%22$SITE%22+npmrc%20_auth&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+npmrc%20_auth&type=Code"
```

#### витік конфігурацій Docker  
```
"$GIT_SITE%22$SITE%22+dockercfg&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+dockercfg&type=Code"
```

#### витік приватних ключів SSL/SSH  
```
"$GIT_SITE%22$SITE%22+pem%20private&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+extension:pem%20private&type=Code"
```

#### SSH-приватні ключі  
```
"$GIT_SITE%22$SITE%22+id_rsa&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+id_rsa&type=Code"
```

#### AWS Access Key ID  
```
"$GIT_SITE%22$SITE%22+aws_access_key_id&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+aws_access_key_id&type=Code"
```

#### конфігурація S3  
```
"$GIT_SITE%22$SITE%22+s3cfg&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+s3cfg&type=Code"
```

#### файл `.htpasswd` (облікові дані Basic Auth)  
```
"$GIT_SITE%22$SITE%22+htpasswd&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+htpasswd&type=Code"
```

#### витік облікових даних Git  
```
"$GIT_SITE%22$SITE%22+git-credentials&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+git-credentials&type=Code"
```

#### паролі у `.bashrc`  
```
"$GIT_SITE%22$SITE%22+bashrc%20password&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+bashrc%20password&type=Code"
```

#### конфігурація SSH (`sshd_config`)  
```
"$GIT_SITE%22$SITE%22+sshd_config&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+sshd_config&type=Code"
```

#### Slack-токени (`xoxp`, `xoxb`, `xoxa`)  
```
"$GIT_SITE%22$SITE%22+xoxp%20OR%20xoxb%20OR%20xoxa&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+xoxp%20OR%20xoxb&type=Code"
```

#### секретний ключ (`SECRET_KEY`)  
```
"$GIT_SITE%22$SITE%22+SECRET_KEY&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+SECRET_KEY&type=Code"
```

#### клієнтський секрет (`client_secret`)  
```
"$GIT_SITE%22$SITE%22+client_secret&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+client_secret&type=Code"
```

#### GitHub-токен  
```
"$GIT_SITE%22$SITE%22+github_token&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+github_token&type=Code"
```

#### API-ключ  
```
"$GIT_SITE%22$SITE%22+api_key&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+api_key&type=Code"
```

#### FTP-доступ  
```
"$GIT_SITE%22$SITE%22+FTP&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+FTP&type=Code"
```

#### секрети додатків (`app_secret`)  
```
"$GIT_SITE%22$SITE%22+app_secret&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+app_secret&type=Code"
```

#### файл `passwd`  
```
"$GIT_SITE%22$SITE%22+passwd&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+passwd&type=Code"
```

#### файл `.env`  
```
"$GIT_SITE%22$SITE%22+.env&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+.env&type=Code"
```

#### конфігурація `beanstalkd.yml`  
```
"$GIT_SITE%22$SITE%22+beanstalkd.yml&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+beanstalkd.yml&type=Code"
```

#### файл `deploy.rake`  
```
"$GIT_SITE%22$SITE%22+deploy.rake&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+deploy.rake&type=Code"
```

#### облікові дані MySQL  
```
"$GIT_SITE%22$SITE%22+mysql&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+mysql&type=Code"
```

#### файл `credentials`  
```
"$GIT_SITE%22$SITE%22+credentials&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+credentials&type=Code"
```

#### збережені паролі (`PWD`)  
```
"$GIT_SITE%22$SITE%22+PWD&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+PWD&type=Code"
```

#### історія команд Bash  
```
"$GIT_SITE%22$SITE%22+.bash_history&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+.bash_history&type=Code"
```

#### файли `.sls`  
```
"$GIT_SITE%22$SITE%22+.sls&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+.sls&type=Code"
```

#### файл `secrets`  
```
"$GIT_SITE%22$SITE%22+secrets&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+secrets&type=Code"
```

#### конфігурація `composer.json`  
```
"$GIT_SITE%22$SITE%22+composer.json&type=Code"  
"$GIT_SITE%22$SITE_WITHOUT_SUFFIX%22+composer.json&type=Code"
```

## Застереження
GitHub Dorking потрібно використовувати тільки для етичних методів. За незаконне використання ви несете повну відповідальність!
