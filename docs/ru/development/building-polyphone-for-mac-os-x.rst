.. _build for mac:

Сборка Polyphone для Mac OS X
=============================

Используйте эти указания, если вы не можете установить Polyphone на Mac OS X используя установщики, доступные в разделе “Download_”.


Перед тем как начать
--------------------

Потребуются следующие приложения:

* Xcode (доступно в Apple Store)
* `Qt Creator с фреймворком <get qt_>`_

Вам также нужны исходники Polyphone, доступные `здесь <download_>`_ или `на GitHub`_, а также необходимые библиотеки, которые вы можете скачать `здесь <libmac_>`_.


Сборка
------

Разархивируйте библиотеки и поместите каталог :file:`lib_mac` рядом с каталогом :file:`sources`.

Откройте файл :file:`polyphone.pro` с помощью :program:`Qt Creator`.
После сборки проекта в каталоге :file:`lib_mac` должен появиться пакет :file:`polyphone.app`.

Если путь SDK не может быть определен, попробуйте изменить файл :file:`polyphone.pro`, включив в него следующие переменные (сначала настройте версию Mac OSX)::

  QMAKE_MACOSX_DEPLOYMENT_TARGET = 10.11
  QMAKE_MAC_SDK = macosx10.11


Доработка пакета
----------------

Запустите следующую команду, чтобы включить библиотеки и фреймворки в состав пакета (сначала измените пути!)::

  /путь/к/Qt/5.2.0/clang_64/bin/macdeployqt /путь/к/lib_mac/polyphone.app

Скопируйте фреймворк Jackmp из :file:`lib_mac` и вставьте его в :file:`lib_mac/polyphone.app/Contents/Frameworks`.
Вам придётся щелкнуть правой кнопкой мыши и выбрать :guilabel:`Просмотр содержимого`, чтобы перейти внутрь пакета, а не выполнить его.

Наконец, запустите следующую команду одной строкой (сначала измените последний путь!)::

  install_name_tool -change /System/Library/Frameworks/Jackmp.framework/Versions/A/Jackmp @executable_path/../Frameworks/Jackmp.framework/Versions/A/Jackmp /путь/к/lib_mac/polyphone.app/Contents/MacOS/Polyphone

Теперь вы можете запустить программу или сжать ее в ZIP-архив, чтобы поделиться ею.


Отладка
-------

Просмотрите эту тему_, если вам нужна дополнительная информация или помощь.


.. external links:

.. _download:  https://www.polyphone-soundfonts.com/en/download
.. _get qt:    https://www.qt.io/download-open-source
.. _на GitHub: https://github.com/davy7125/polyphone
.. _libmac:    https://www.polyphone-soundfonts.com/downloads/lib_mac.zip
.. _тему:      https://www.polyphone-soundfonts.com/en/forum/support-bug-reports/8-success-build-polyphone-on-osx-10-11-6-qt-5-7
