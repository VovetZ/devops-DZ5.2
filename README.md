# devops-DZ5.2

# Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"

---

## Задача 1

- Опишите своими словами основные преимущества применения на практике IaaC паттернов.
~~~
Ответ:
Преимущество применения паттернов IaaС на практике - возможность многократно воспроизводить инфрастуктуру с помощью ее описания, производить развёртывние идентичных серверов и сред для тестирования/разработки, масштабирование при необходимости. Автоматизация рутинных действий приводит к снижению трудозатрат на их выполнение - как следствие повышается скорость разработки, выявления и устранения дефектов за счёт более раннего их обнаружения и тестирования на этапе сборки. Автоматизация поставки - позволяет сократить время от этапа разработки до внедрения. Паттерны IaaC позволяют стандартизировать развёртывание инфраструктуры, что снижает вероятность появления ошибок или отклонений связанных с человеческим фактором. Итого
- Экономия ресурсов (время и деньги)
- Стабильность среды, устранение дрейфа конфигураци
- Ускорение производства и вывода продукта на рынок за счет автоматизации
~~~
- Какой из принципов IaaC является основополагающим?
~~~
Ответ:

Идемпотентность
~~~

## Задача 2

- Чем Ansible выгодно отличается от других систем управление конфигурациями?
~~~
Ответ:

Ansible не требует наличия агента на клиенте.
Можно использовать в существующем  ssh соединении, т.е. не требует другого соединения.
~~~
- Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?
~~~
Ответ:

pull
~~~

## Задача 3

Установить на личный компьютер:

- VirtualBox
- Vagrant
- Ansible

*Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.*
~~~
Ответ:

user@ubuntu-virt:~/vagrant$ VirtualBox -v
Графический интерфейс VirtualBox Версия 6.1.32_Ubuntu r149290

user@ubuntu-virt:~/vagrant$ vagrant -v
Vagrant 2.2.6

user@ubuntu-virt:~/vagrant$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/user/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, Mar 15 2022, 12:22:08) [GCC 9.4.0]

~~~

## Задача 4 (*)

Воспроизвести практическую часть лекции самостоятельно.

- Создать виртуальную машину.
- Зайти внутрь ВМ, убедиться, что Docker установлен с помощью команды
```
docker ps
```
~~~
Ответ:
поправил в Vagrantfile на:
NET = "192.168.56."

user@ubuntu-virt:~/vagrant$ vagrant up
Bringing machine 'server1.netology' up with 'virtualbox' provider...
==> server1.netology: Importing base box 'bento/ubuntu-20.04'...

...
ASK [Add the current user to docker group] ************************************
changed: [server1.netology]

PLAY RECAP *********************************************************************
server1.netology           : ok=7    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=1   


vagrant@server1:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
vagrant@server1:~$ docker version
Client: Docker Engine - Community
 Version:           20.10.16
 API version:       1.41
 Go version:        go1.17.10
 Git commit:        aa7e414
 Built:             Thu May 12 09:17:23 2022
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.16
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.17.10
  Git commit:       f756502
  Built:            Thu May 12 09:15:28 2022
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.4
  GitCommit:        212e8b6fa2f44b9c21b2798135fc6fb7c53efc16
 runc:
  Version:          1.1.1
  GitCommit:        v1.1.1-0-g52de29d
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
~~~
