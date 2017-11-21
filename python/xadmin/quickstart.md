# xadmin 入门指南

## 版本说明

日期：2017-11-21
xadmin: 1cdac79fb95c0ff9efc191fe91f5f54ab7e6a3cf
django: 1.11.6

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
