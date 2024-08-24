# Домашнее задание к занятию 2 «Работа с Playbook» «Макаров Денис»

## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.
4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`.

Решение:

Подговленный [prod.yml](https://github.com/Makarov-Denis/Ansible_working_playbook/blob/main/playbook/inventory/prod.yml)

2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev). Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по [ссылке](https://www.dmosk.ru/instruktions.php?object=ansible-nginx-install). не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!

Решение представлено в файлах ниже:

[template](https://github.com/Makarov-Denis/Ansible_working_playbook/tree/main/playbook/templates)

[site_new.yml](https://github.com/Makarov-Denis/Ansible_working_playbook/blob/main/playbook/site_new.yml)

3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.

Использованы модули:
1. ```ansible.builtin.get_url```
2. ```ansible.builtin.yum```
3. ```ansible.builtin.meta```
4. ```ansible.builtin.pause```
5. ```ansible.builtin.command```
6. ```ansible.builtin.file```
7. ```ansible.builtin.unarchive```
8. ```ansible.builtin.copy```
9. ```ansible.builtin.replace```
10. ```ansible.builtin.user```
11. ```ansible.builtin.service```
12. ```ansible.builtin.systemd```

4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.

Решение:

Представлено на скриншоте ниже:

![ansible-lint](https://github.com/user-attachments/assets/2aaaaed6-4eaf-473b-b7d7-9002cfcbb61d)

Ошибки были исправлены.

6. Попробуйте запустить playbook на этом окружении с флагом `--check`.

Решение:

Представлено на скриншоте ниже:

![ansible-playbook-check](https://github.com/user-attachments/assets/f8ca4153-49fc-4495-9c96-1144b1866727)

7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.

Решение представлено на скриншотах ниже:

![idenpotent](https://github.com/user-attachments/assets/44987917-503c-4737-a9c9-0cd55e41df93)

На данных скриншотах представлена работа clickhouse на hosts: clickhouse1

![proverka](https://github.com/user-attachments/assets/fcc0c976-dd8b-4faa-93fb-eda3bd88a4a1)


![clickhouse](https://github.com/user-attachments/assets/fec19613-b82b-4e2e-bfcb-bd7491716646)

На данных скриншотах представлена работа Vector на hosts: clickhouse2

![vector](https://github.com/user-attachments/assets/368570e0-407e-4c67-ace3-aa5bea56ca40)

![baza](https://github.com/user-attachments/assets/b4206800-e126-47ad-bcd1-2fac1d21372e)

8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.

Решение:

![idenpotent](https://github.com/user-attachments/assets/646ced24-6167-4a3c-9f0b-6dfba8570825)


9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по [ссылке](https://github.com/opensearch-project/ansible-playbook). Так же приложите скриншоты выполнения заданий №5-8
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
