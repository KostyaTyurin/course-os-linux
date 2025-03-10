Tmux – терминальный мультиплексор
================================
:date: 2022-05-12 09:00
:summary: Краткий экскурс в tmux
:status: published
:author: Тюрин К.А., Быданов Д.В.

.. default-role:: code
.. contents:: Содержание

**Tmux** — это консольная утилита, предоставляющая пользователю доступ к
нескольким терминалам в рамках одного экрана. Простыми словами,
используя эту утилиту можно в одном окне открыть несколько терминальных
окон. Также возможно подключение к существующей сессии из другого
рабочего места не прерывая выполнение определенных задач.

.. image:: ./images/tmux/01.png
    :scale: 100 %
    :alt: 01
    :target: ./images/tmux/01.png 

Как видно из скриншота, у нас несколько консольных панелей в одном окне.
Очень удобно работать. Приступим к более подробному рассмотрению. Для
установки *tmux* утилиты в Ubuntu достаточно
выполнить команду:

.. code:: bash

    sudo apt-install tmux

После установки программы можно приступать к использованию

Вводим команду:

.. code:: bash

    tmux

Происходит запуск утилиты. Понять, что мы находимся в tmux можно по наличию зеленой строки внизу консоли, на которой размещены дата и время.

.. image:: ./images/tmux/02.png
    :scale: 100 %
    :alt: 02
    :target: ./images/tmux/02.png


По умолчанию создается одна панель на весь экран. Для того, чтобы
добавить вертикальную панель необходимо воспользоваться сервисными
клавишами «Ctrl+B»(система понимает, что вы вводите не консольную
команду, а пользуетесь функцией терминального мультиплексера), далее
нажимаете «Shift+%». Справа создается еще одна панель.

.. image:: ./images/tmux/03.png
    :scale: 100 %
    :alt: 03
    :target: ./images/tmux/03.png

Теперь в рамках одного окна у вас есть две рабочие зоны.

Для переключения между панелями воспользуйтесь клавишами «Ctrl+B» далее стрелочками вправо или влево.

Для создания горизонтальной панели нажмите «Crtl+B» далее «Shift+”»
(кавычка находится на русской букве «Э»)

.. image:: ./images/tmux/4.png
    :scale: 100 %
    :alt: 04
    :target: ./images/tmux/4.png 

Для изменения размера определенной панели есть следующая комбинация
клавиш:

«Ctrl+B» затем зажимаем Alt и стрелочками изменяем размер.

.. image:: ./images/tmux/5.png
    :scale: 100 %
    :alt: 05
    :target: ./images/tmux/5.png

Для изменения местоположения панели воспользуется комбинацией клавиш
«Ctrl+B» затем «}».

.. image:: ./images/tmux/04.png
    :scale: 100 %
    :alt: 06
    :target: ./images/tmux/04.png



Также есть возможность создать еще одно окно. Для этого предусмотрена
команда «Ctrl+B» «c»

Для просмотра списка окон можно воспользоваться командой «Ctrl+B» «w»

.. image:: ./images/tmux/05.png
    :scale: 100 %
    :alt: 07
    :target: ./images/tmux/05.png  

Как видно из скриншота, у нас создалось второе окно. Для удобного
распознавания нужного окна можно присвоить им имена:

.. code:: bash

    tmux rename-window window_name

Также можно воспользоваться командной строкой терминала выполнив команду
«Ctrl+B» «:»

И в командной строке набрать команду «remane-window masinc» (где
«window_name» это новое имя)

Для переименования сессии применяется следующая команда: «tmux
rename-session –t 0 session_name»

-t указывает на номер сессии, если этот параметр опустить будет
переименована существующая сессия.

Для просмотра количества существующих сессий воспользуемся командой

.. code:: bash

    tmux ls

Создадим еще одну сессию tmux, для этого выйдем из существующей сессии:

.. code:: bash

    tmux detach (или Ctrl+B d)

.. code:: bash

    tmux

Посмотрим список созданных сессий:

.. code:: bash

    tmux ls

.. image:: ./images/tmux/06.png
    :scale: 100 %
    :alt: 08
    :target: ./images/tmux/06.png



Для подключения к определенной сессиb воспользуемся командой:

.. code:: bash

    tmux a –t session_name

Мы подключились к сесси «session_name».

Для закрытия сессии необходимо закрыть все панели командой «Ctrl+B» «x».
Затем «у» для подтверждения.

Также для завершения сессии можно воспользоваться командой:

.. code:: bash

    tmux kill-session

Для отключения от сессии с сохранением ее работоспособности есть
несколько вариантов:

.. code:: bash

    tmux detach
.. code:: bash

     tmux d

.. code:: bash

    «Ctrl+B» «d»

Также есть возможность управлять размером окон с помощью мышки. Для
этого в конфигурационный файл /etc/tmux.conf следует добавить следующие
строки:

.. code:: bash

    set -g mouse-resize-pane on

Для применения настроек необходимо перечитать конфигурационный файл

.. code:: bash

    tmux source-file /etc/tmux.conf

Если вы хотите переподключиться к другой сессии выполните команду:

.. code:: bash

    tmux switch –t name

Или же можно воспользоватсья клавишами "Ctrl + B + S" 


Для прокрутки страницы вверх используйте комбинацию клавиш «Ctrl+B»
    «PgUp/PgDwn»

Также очень много удобных дополнительных функций можно добавить внеся
необходимые изменения в конфигурационный файл. Воспользовавшись мануалом
«man tmux» можно получить дополнительную информацию.



+--------------------------------+----------------------+
| **Название команды**           | **Горячие клавиши**  |
+================================+======================+
| “Убить” сессию                 | Ctrl + b + d         |
+--------------------------------+----------------------+
| Создает новую вкладку          | Ctrl + b + b         |
+--------------------------------+----------------------+
| Переименовать файл             | Ctrl + b + ,         |
+--------------------------------+----------------------+
| Выход из tmux                  | Ctrl + b + d         |
+--------------------------------+----------------------+
| Разделить окно по вертикали    | Ctrl + b + %         |
+--------------------------------+----------------------+
| Разделить окно по горизонтали  | Ctrl + b + "         |
+--------------------------------+----------------------+
| Переход между окнами           | Ctrl + b + ->        |
+--------------------------------+----------------------+
| Открыть диспетчер задач        | htop                 |
+--------------------------------+----------------------+

 


**Задание**

Выполните следующие действия: 

1. Откройте tmux

.. image:: ./images/tmux/t1.jpg
    :scale: 100 %
    :alt: t1
    :target: ./images/tmux/t1.jpg

2. Создайте четыре окна и измените их размер, как показано на фотографии

.. image:: ./images/tmux/t2.jpg
    :scale: 100 %
    :alt: t2
    :target: ./images/tmux/t2.jpg

3. Откройте в левом верхнем окне диспетчер задач, а в правом верхнем - время (в соответствии с фотографией)

.. image:: ./images/tmux/t3.jpg
    :scale: 100 %
    :alt: t3
    :target: ./images/tmux/t3.jpg

4. Создайте скрипт (или воспользуйтесь скриптом из прошлой лабы), который по выбору пользователя с интервалом печатает цифры. Запустите скрипт в левом нижнем окне.

.. image:: ./images/tmux/t4.jpg
    :scale: 100 %
    :alt: t4
    :target: ./images/tmux/t4.jpg

5. Используя знания о работе с процессами, запустите данный скрипт три раза в левом нижнем окне (при этом цифры, выводящиеся на экран, должны быть различными)

.. image:: ./images/tmux/t5.jpg
    :scale: 100 %
    :alt: t5
    :target: ./images/tmux/t5.jpg

6. В правом нижнем окне отройте используемый скрипт в редакторе vim (на фотографии, конечно, не он)

.. image:: ./images/tmux/t6.jpg
    :scale: 100 %
    :alt: t6
    :target: ./images/tmux/t6.jpg
