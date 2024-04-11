# Программирование частот на радиостанциях Retevis RT86

Дисклеймер: данная статья не является обзором радиостанции. Если нужен обзор, то неплохой есть [здесь](https://www.ixbt.com/live/gadgets/retevis-rt86-hidden-display-uhf-radio.html).

Радиостанции RT86 из коробки (я купил две) настроены на диапазон 430-440 MHz, это... ну, как бы не очень хорошо. Работать они, конечно, будут, но лучше настроить их частотный диапазон на таблицу [LPD433](https://ru.wikipedia.org/wiki/LPD433), чтобы не было проблем с законами. Тут я не углубляюсь, желающие могут загуглить, какие ограничения есть в РФ.

Чтобы прошить нужные частоты, качаем с [официального сайта](https://www.retevis.com/RT86-Hidden-Display-UHF-Radio-with-flashlight-long-distance-call#A9207A) программу и драйвер. Там всё под Windows, если кто-то хочет поколдовать с Linux &mdash; напишите про свои опыты.

1. Устанавливаем драйвер, устанавливаем программу RT86, перезагружаемся.
2. Подключаем радиостанцию к компьютеру кабелем. Смотрим в диспетчере, на каком COM-порту он обнаружился в Windows. Обычно бывает `COM3` или `COM4`, если нет других подобных устройств в системе.
3. Включаем радиостанцию. В отличие от обычного включения, когда она по-английски объявляет номер текущего канала, станция должна включиться молча. Это правильно и хорошо.
4. Запускаем программу RT86:
   ![скрин программы](https://github.com/siamoza/retevis_rt86/blob/master/3.interface.PNG)
5. Заходим в меню `Set` -> `Communication Port` и выбираем тот порт, который установился в пункте 2.
6. Нажимаем в панели кнопку `READ`. Спросят пароль, по умолчанию он не установлен. Всё, таблица частот с радиостанции считана в компьютер.
7. Каналов в Retevis RT80 &mdash; шестнадцать, поэтому в таблице нужно будет исправить 16 пар чисел. Заполняем первые две колонки &mdash; `Rx Freq` и `Tx Freq` &mdash; значениями из таблицы LPD433. Получится так:
   ![заполненные частоты](https://github.com/siamoza/retevis_rt86/blob/master/4.interface_ready.PNG)
8. Когда закончили, нажимаем в панели `WRITE` и тем самым записываем нашу новую таблицу в радиостанцию. Здесь также можно сохранить таблицу в файл, чтобы на других рациях снова не набирать частоты вручную.
9. Выключаем рацию, отсоединяем провод. Всё.

###to be continued###

Todo:
- [ ] копирование настроек с одной радиостанции на другую
- [ ] работа с Linux
