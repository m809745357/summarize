## laravel-5-boilerplate

```shell
sudo git clone https://github.com/rappasoft/laravel-5-boilerplate.git laravel-5-boilerplate
cd laravel-5-boilerplate
sudo cp .env.example .env
sudo vim .env
# 修改以下信息
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=boilerplate
DB_USERNAME=boilerplate
DB_PASSWORD=boilerplate

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=sync

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_DRIVER=smtp
MAIL_FROM_ADDRESS=809745357@qq.com
MAIL_FROM_NAME=809745357
MAIL_HOST=smtp.qq.com
MAIL_PORT=465
MAIL_USERNAME=809745357@qq.com
MAIL_PASSWORD=stevakbdlrswbecj
MAIL_ENCRYPTION=ssl

sudo composer install
sudo npm install

sudo php artisan key:generate
sudo php artisan migrate
sudo php artisan db:seed

sudo npm install -g gulp
sudo ln -s /usr/local/node/bin/gulp /usr/bin/gulp
gulp
```

```php
{{ }} 替换String
{!! !!} 替换HTML
```

