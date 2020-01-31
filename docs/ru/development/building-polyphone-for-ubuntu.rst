.. _build for ubuntu:

Сборка Polyphone для Ubuntu
===========================

Используйте эти указания, если вы не можете установить Polyphone в свой дистрибутив Linux с помощью доступных инсталляторов в разделе “Download_”.
Этот метод был протестирован с Ubuntu 16.04 (Xenial).


Перед тем как начать
--------------------

Требуются следующие библиотеки:

* qt (``qt5-default`` + ``libqt5svg5-dev``)
* alsa (``libasound2-dev``)
* jack (``libjack-jackd2-dev``)
* portaudio (``portaudio19-dev``)
* rtmidi (``librtmidi-dev``)
* stk (``libstk0-dev``)
* qcustomplot (``libqcustomplot-dev``)
* vorbis (``libvorbis-dev``)
* ogg (``libogg-dev``)
* flac (``libflac-dev``)
* ssl (``libssl-dev``)

Установите их с помощью :program:`synaptic`.


Сборка
------

В корневом каталоге проекта откройте терминал и соберите Polyphone, выполнив следующую команду::

  qmake && make

Если всё прошло правильно, в каталоге :file:`RELEASE` должен появиться исполняемый файл :file:`polyphone`.

В случае, если библиотеки, такие как RtMidi, Stk, QCustomPlot отсутствуют или не совместимой версии в вашем дистрибутиве, вы можете отредактировать файл :file:`.pro`, чтобы использовать их локальные копии.
Для этого раскомментируйте соответствующие строки. Например,

::

  #DEFINES += USE_LOCAL_RTMIDI

станет

::

  DEFINES += USE_LOCAL_RTMIDI

(без начального «#»).

.. note::
   Если вы используете :program:`Qt Creator`, проект можно открыть через его файл :file:`.pro`, находящийся в корневом каталоге.
   Позаботьтесь о том, чтобы опция :guilabel:`теневая сборка` в свойствах проекта не была включена.


.. external links:

.. _download:  https://www.polyphone-soundfonts.com/en/download
