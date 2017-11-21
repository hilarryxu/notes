# xadmin 入门指南

## 版本说明

* 日期：2017-11-21
* xadmin: 1cdac79fb95c0ff9efc191fe91f5f54ab7e6a3cf
* django: 1.11.6

## 初始化基本环境

```bash
virtualenv .venv
source .venv/bin/activate

pip install Django==1.11.6
pip install -e .

版本信息
Successfully built django-reversion django-import-export httplib2 future tablib diff-match-patch odfpy openpyxl unicodecsv jdcal et-xmlfile
Installing collected packages: django-crispy-forms, django-reversion, django-formtools, odfpy, jdcal, et-xmlfile, openpyxl, unicodecsv, xlrd, xlwt, pyyaml, tablib, diff-match-patch, django-import-export, httplib2, future, six, xadmin
  Running setup.py develop for xadmin
  Successfully installed diff-match-patch-20121119 django-crispy-forms-1.7.0 django-formtools-2.1 django-import-export-0.5.1 django-reversion-2.0.10 et-xmlfile-1.0.1 future-0.16.0 httplib2-0.9.2 jdcal-1.3 odfpy-1.3.5 openpyxl-2.4.9 pyyaml-3.12 six-1.11.0 tablib-0.12.1 unicodecsv-0.14.1 xadmin xlrd-1.1.0 xlwt-1.3.0
```

## 运行demo

```bash
cd demo_app
./manage.py migrate
./manage.py createsuperuser
./manage.py runserver 0.0.0.0:3333
```

## 数据库表说明

django admin相关

- auth_user
- auth_group
- auth_permission
- auth_user_groups
- auth_group_permissions
- auth_user_user_permissions

- django_content_type
- django_session
- django_migrations
- django_admin_log

xadmin 相关

- reversion_version
- reversion_revision
- xadmin_usersettings
- xadmin_userwidget
- xadmin_bookmark
- xadmin_log

## xadmin_log 表结构

```sql
CREATE TABLE IF NOT EXISTS "xadmin_log" (
  "id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "action_time" datetime NOT NULL,  // 动作时间
  "ip_addr" char(39) NULL,  // IP地址
  "object_id" text NULL,  // 对象ID
  "object_repr" varchar(200) NOT NULL,  // 对象描述
  "message" text NOT NULL,  // 日志消息
  "content_type_id" integer NULL REFERENCES "django_content_type" ("id"),  // 对象类型
  "user_id" integer NOT NULL REFERENCES "auth_user" ("id"),  // 用户ID
  "action_flag" varchar(32) NOT NULL  // 动作标志
);
```
