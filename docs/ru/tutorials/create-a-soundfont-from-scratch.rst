.. _create a soundfont from scratch:

Как создать SoundFont с нуля
============================

Чтобы создать :ref:`SoundFont <sf2 format>`, нажмите кнопку :guilabel:`Создать SoundFont` на :ref:`главном экране <left part>`.
Файлы SoundFont содержат трёхуровневую структуру, поэтому создание нового SoundFont предполагает три основных этапа:

* `подготовка семплов <sample preparation_>`_,
* `создание инструментов <instrument creation_>`_, включающих семплы,
* `создание пресетов <preset creation_>`_, включающих инструменты.


.. _sample preparation:

Подготовка семплов
------------------


Загрузка семплов
^^^^^^^^^^^^^^^^

Подготовка семплов начинается с **загрузки** файлов .wav.
Для этого сначала выберите категорию :guilabel:`Семплы` в :ref:`дереве <tree>` и выберите :guilabel:`Импортировать семплы` на :ref:`панели инструментов <toolbar edit>`.
Семплы могут быть получены:

* через интернет,
* записав настоящий музыкальный инструмент,
* путём синтеза с использованием специализированного ПО.


Закольцовка семплов
^^^^^^^^^^^^^^^^^^^

Далее, семпл может потребоваться **закольцевать**, если вы хотите, чтобы он звучал дольше, чем его обычная длительность.
Например, если у вас есть только 1-секундный семпл флейты, но вы хотите, чтобы он звучал постоянно.
Это можно сделать, указав вручную или автоматически точки петли (начало и конец) в пределах границ семпла, чтобы область петли повторялась и семпл звучал дольше.
Хотя вы можете назначить точки петли вручную, использование функции «:ref:`sample tool autoloop`» для их автоматического назначения обычно даёт лучшие результаты и намного быстрее.

Чтобы назначить точки петли вручную:

#. щёлкните в :ref:`дереве <tree>` на семпле, который будет закольцован,
#. в :ref:`редакторе семплов <sample editor>` произвольно расположите начало и конец петли на графике (область отображения WAV), если цикл ещё не определён.
   Щёлкните левой кнопкой мыши в начале и правой кнопкой мыши в конце.
   Правая точка петли должна быть указана первой (поскольку левая точка по умолчанию указывает на позицию 0, а правая точка не может стоять перед левой точкой).
#. нажмите кнопку :guilabel:`Воспроизведение` после выбора функции петли,
#. отрегулируйте начало и / или конец петли во время воспроизведения семпла, пока переход между двумя положениями не станет как можно более плавным.

.. note::
   Чтобы услышать петлю в инструменте, вы должны выбрать |loop on| в строке параметра :guilabel:`Играть петлю` в глобальном столбце или в столбце отдельных нот в :ref:`таблице параметров <instrument editor table>`.

   |loop on| включает воспроизведение петли, |loop off| или пустая ячейка — отключает.


.. figure:: images/loop_illustration.png

   Иллюстрация петли


Подстройка семплов
^^^^^^^^^^^^^^^^^^

Наконец, нужно **подстроить** семплы.
Для этого на странице редактирования :ref:`семплов <sample editor player>` доступно средство калибровки (синус).
Для каждого семпла метод выглядит следующим образом:

#. начните воспроизведение (нажмите кнопку :guilabel:`Воспроизведение`), если возможно, с выбранной функцией петли,
#. выберите функцию синуса,
#. отрегулируйте ползунок громкости, чтобы слышать два звука как можно более чётко,
#. меняйте корнеыую клавишу, пока два звука не будут наиболее близко совпадать,
#. отрегулируйте поправку (в центах), чтобы окончательно подстроить семпл.
   Для этого обратите внимание на любые слышимые биения и добейтесь, чтобы они были как можно медленнее.

:ref:`Частотный анализ <sample editor frequency>` может быть хорошим индикатором для начала настройки.


Другие возможности
^^^^^^^^^^^^^^^^^^

При редактировании семплов доступно несколько средств:

* :ref:`удаление тишины <sample tool removeblank>` в начале,
* :ref:`выравнивание <sample editor equalizer>` звука,
* :ref:`транспонирование <sample tool transpose>`,
* :ref:`нормализация <sample tool volume>` громкости,
* :ref:`регулировка баланса <sample tool balance>` стерео семплов.


.. _instrument creation:

Создание инструмента
--------------------

На этом этапе предполагается, что один или несколько семплов уже доступны для создания инструмента.


Создание инструмента и добавление семплов
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Сначала нажмите :guilabel:`Новый инструмент` на :ref:`панели инструментов <toolbar edit>`.
Теперь введите имя.

Затем добавьте семплы к инструменту с помощью :ref:`перетаскивания <tree dragdrop>`.
В дереве вы заметите, что в инструменте появляются разделы.

.. note::
   При создании семплов разделы не копируются, а связываются.
   Количество разделов не ограничено.


Распределение разделов
^^^^^^^^^^^^^^^^^^^^^^

Когда семплы добавляются в инструменты, они отображаются в виде разделов (столбцов) в :ref:`таблице редактора инструментов <instrument editor table>`.
Каждый раздел затем должен быть размещён на клавиатуре путём изменения значения :guilabel:`Диапазон клавиш` в таблице.
Считается хорошим тоном, чтобы диапазон раздела включал корневую клавишу представленного семпла.
Вся поверхность клавиатуры должна быть заполнена (например, с клавиши 36 по клавишу 96 для классической клавиатуры синтезатора).

Средство «:ref:`instrument tool position`» автоматически распределяет семплы по клавиатуре.


Настройка разделов
^^^^^^^^^^^^^^^^^^

Если семпл зациклен, чтобы услышать зацикливание в инструменте, выберите значок |loop on| в строке параметра :guilabel:`Играть петлю` в столбце :guilabel:`Глобальные` или в отдельных столбцах разделов инструмента в :guilabel:`Таблице параметров`.

* |loop on| включает петлю,
* |loop off| или пустое значение ячейки выключает её.
* |loop on and end| включает петлю, а после отпускания клавиши семпл будет проигран до конца.

Глобальный раздел, как следует из его названия, позволяет ввести параметр для всего инструмента.
Глобальный параметр применяется только к разделам, в которых этот параметр не указан.
Это означает, что параметры отдельных разделов имеют приоритет над настройками глобального раздела.

В этом простом уроке мы не будем редактировать никакие другие параметры для работы инструмента.
Уже можно играть с помощью :ref:`виртуальной клавиатуры <toolbar keyboard>`.

Однако, чтобы улучшить инструмент, рекомендуется ввести значение в строку :guilabel:`Огибающая громкости: затухание (сек)`, что предотвратит резкое прекращение звука при отпускании клавиши.
Другие параметры описаны в описании :ref:`таблиц <instrument editor table>`.


.. _preset creation:

Создание пресетов
-----------------

На этом этапе предполагается, что один или несколько инструментов уже доступны для создания пресета.


Что такое пресет?
^^^^^^^^^^^^^^^^^

Пресет является эквивалентом имени звукового патча из аппаратных синтезаторов.
Он виден снаружи SoundFont и идентифицируется номером банка и номером пресета.
SoundFont может иметь один или несколько пресетов.
Каждый пресет содержит один или несколько инструментов, так же как каждый инструмент содержит один или несколько семплов.


Создание пресета и добавление инструментов
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Во-первых, нажмите :guilabel:`Новый пресет` на :ref:`панели инструментов <toolbar edit>`.
Введите имя.

Затем добавьте инструменты в пресет с помощью :ref:`перетаскивания <tree dragdrop>`.
В дереве вы заметите, что в пресете появится один или несколько разделов.
Часто раздел может быть только один, как в случае пресета, содержащего один инструмент.

Можно создать столько же (или больше) пресетов, сколько и инструментов, а каждый пресет может содержать один или несколько инструментов.


Настройка пресета
^^^^^^^^^^^^^^^^^

Изменение параметров пресетов может не потребоваться, поскольку:

* при создании пресета номер банка и номер пресета назначаются автоматически,
* при добавлении инструмента в пресет диапазон клавиш автоматически рассчитывается в соответствии с инструментом.

В рамках данного урока создание SoundFont завершено!


.. inline images:

.. |loop on|         image:: images/loop_on.png
.. |loop off|        image:: images/loop_off.png
.. |loop on and end| image:: images/loop_on_end.png
