# 環境構築  
### コンテナ構築  
```
$ docker-compose build
```
  
### コンテナ起動
```
$ docker-compose up -d
```

### Djangoプロジェクトを作成
```
$ docker-compose exec app django-admin.py startproject *プロジェクト名* .
```

### 作成したら一度再起動
```
$ docker-compose restart
```

### Djangoプロジェクトの設定

プロジェクト内のsettings.pyを書き換える。  

```md:/src/プロジェクト名/settings.py
DATABASES = {
　　'default': {
 　     'ENGINE': 'django.db.backends.mysql',
        'NAME': 'django_local',
        'USER': 'django_user',
        'PASSWORD': 'secret',
        'HOST': 'db',
        'POST': 3306`
   }
}

LANGUAGE_CODE = 'ja'

TIME_ZONE = 'Asia/Tokyo'
```

### DjangoとMySQL接続
```
$ docker-compose exec app ./manage.py migrate
```

