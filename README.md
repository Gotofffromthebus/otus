### Otus ###
**Домашнее задание №1**

**Цель домашнего задания**

1. Подготовить ПК для выполнения домашних работ
2. Научиться обновлять ядро в ОС Linux. Получить навыки работы с Vagrant, Packer и публикацией готовых образов в Vagrant Cloud.

**Описание домашнего задания**

1. Обновить ядро ОС из репозитория ELRepo
2. Создать Vagrant box c помощью Packer
3. Загрузить Vagrant box в Vagrant Cloud

**Используемые инструменты**

1. Vagrant
2. Packer
3. Git
4. GitHub

**Этапы выполнения**

1. Установить необходимые инструменты.
2. Сборка Packer - BOX. Создать дирректорию Vagrant, создать в ней директорию packer, в ней две директории http и scripts. Создать файлы centos.json (Vagrant), ks.cfg (http), stage1 и stage2 (Scripts). Отредактировать все файлы с необходимыми конфигурациями согласно заданию.
Запустить сборку: 
```bash
packer build centos.json
   ```
3. Cгенерировав токен на сайте.
```bash
vagrant cloud auth login -t <your_token>
```
4. Загрузить BOX в Vagrant cloud командой
```bash
vagrant cloud publish --release <user_account>/centos8-kernel5 1.0 virtualbox centos-8-kernel-5-x86_64-Minimal.box
```
5. Скачать свой BOX для проверки и запуска в своем каталогею 
```bash
vagrant init <your_box>
```
6. Затем запускаем собранный BOX
```bash
vagrant up
```
7. Подключиться к виртуальной машине
```bash 
vagrant ssh
``` 
8. Проверить версию ядра
``` bash
uname -a
`~~~~``