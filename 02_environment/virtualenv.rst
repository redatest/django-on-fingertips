*********************
Виртуальное окружение
*********************

Представьте, что вы разрабатываете проект для заказчика, у которого на хостинге
используется Python 2.7 и ряд библиотек с жёстко определёнными версиями. Вы
устанавливаете на своём компьютере Python нужной версии и требуемые библиотеки,
теперь можно начинать разработку.

Через неделю вам потребовалось добавить небольшую функциональность к проекту
другого заказчика. Всё осложнается тем, что в старом проекте используется Python
версии 2.5 и соответствующие несвежие библиотеки.

Конфликт версий интерпретатора и библиотек -- вещь неприятная.

Чтобы не попадать в такую ситуацию, мы рекомендуем для каждого проекта заводить
отдельное виртуальное окружение. Это позволит вам оперативно активировать
требуемое окружение для работы с проектом.

Для создания виртуального окружения используют пакет `virtualenv
<http://pypi.python.org/pypi/virtualenv>`_.

Виртуальное окружение может быть изолированным и неизолированным.

Изолированное виртуальное окружение содержит программное обеспечение, которое
доступно вашему проекту. Никакое другое программное обеспечение, установленное
на компьютере, не будет доступно для проекта.

Неизолированное виртуальное окружение содержит только то программное
обеспечение, которое уникально для вашего проекта. Этот вариант удобен, когда
все ваши проекты используют версию интерпретатора, которая установлена в вашей
системе, и не сильно завязаны на версионность библиотек. Вам потребуется лишь
поставить в окружение библиотеки с экзотическими версиями.

В виртуальное окружение можно ставить не только Python пакеты, но и стандартные
системные утилиты и библиотеки необходимых версий. Это очень полезное свойство,
далее мы покажем как этим пользоваться.

.. _virtualenv_create:

==================
Создание окружения
==================

Для создания виртуального окружения следует выполнить в корне проекта команду:

* изолированное окружение::

    virtualenv env                           # начиная с версии 1.7
    virtualenv --no-site-packages env        # до версии 1.7

* неизолированное окружение::

    virtualenv --system-site-packages env    # начиная с версии 1.7
    virtualenv env                           # до версии 1.7

Будет создано пустое виртуальное окружение со следующей структурой каталогов,
пример показан для Python 2.6 в неизолированном окружении::

    bin/
      activate
      activate_this.py
      easy_install
      easy_install-2.6
      pip
      python
    include/
      python2.6/
    lib/
      python2.6/

При необходимости использовать определённую версию Python внутри окружения потребуется 
добавить параметр `-p` или `--python` к команде создания окружения. Например::

    virtualenv -p python2.5 env
    virtualenv --python=python2.7 env

.. _virtualenv_activate:

===================
Активация окружения
===================

Для активации виртуального окружения следует выполнить в корне проекта команду::

    . env/bin/activate

После этого в системном окружении появится переменная :envvar:`VIRTUAL_ENV`,
которая указывает путь до корня виртуального окружения.

=====================
Деактивация окружения
=====================

Для деактивации виртуального окружения следует выполнить в любом месте проекта команду::

    deactivate

