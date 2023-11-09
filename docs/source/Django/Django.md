# Django
## 目录
- [Django](#django)
  - [目录](#目录)
  - [初始化项目](#初始化项目)
    - [models](#models)
  - [常用命令](#常用命令)
  - [文件结构说明](#文件结构说明)
- [一些资料](#一些资料)

## 初始化项目
``` bash
python manage.py startapp app1 
```

| 文件 | 说明 | 
| :--: | :--: | 
|migrations|执行数据库迁移生成的脚本|
|admin.py|配置Django管理后台的文件|
|apps.py|单独配置添加的每个App的文件|
|models.py|创建数据库数据模型对象的文件|
|tests.py|用来编写测试脚本的文件|
|views.py|用来编写视图控制器的文件|
|settings.py|将创建的 App 添加到 settings.py 配置文件中|

### models

## 常用命令

``` bash
# 启动
python manage.py runserver  --insecure 0.0.0.0:0090 
python manage.py migrate # 执行数据库迁移生成数据表
python manage.py createsuperuser # 按照提示输入账户和密码，密码强度符合一定的规则要求
python manage.py startapp app1 #可以启用一个应用程序
``` 
## 文件结构说明


# 一些资料

- 搜集的可用项目，功能比较简单，供学习[gitcode](https://gitcode.net/explore/topics/django)
- 比较完整的项目[fuadmin](https://github.com/FuAdmin/fu-admin)
- [pdf书籍资料](https://gitcode.net/e-books/books_abt_python3/-/blob/master/%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3Django%EF%BC%9A%E6%A1%86%E6%9E%B6%E5%86%85%E5%B9%95%E4%B8%8E%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86_9787121421884.pdf)