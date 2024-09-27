# Задание 19 - Кросс-компиляция
## Задания
Собрать vanilla версию ОС Linux со стандартной конфигурацией. Для проверки ядра на работоспособность воспользоваться утилитой QEMU 

## Используемые цели и утилиты 
Для очистки ядра воспользуемся следующей целью:
- `make distclean`
Для создания стандратной конфигурации воспользуемся целью:
- `ARCH=arm make defconfig`
Сборка ядра осуществляется при помощи следующей цели:
- `ARCH=arm make -j6 zImage` - сборка образа на 6-ти ядрах
Для сборки DTB файла воспользуемся следующей целью:
- `ARCH=arm make dtbs`
Запуск QEMU эмулятора осуществляется следующей командой:
- `QEMU_AUDIO_DRV=none qemu-system-arm -M vexpress-a9 -kernel /path/to/kernel -dtb /path/to/dtb -nographic -append "console=ttyAMA0"`
В данной команде `QEMU_AUDIO_DRV=none` отключает аудион на эмуляторе при помощи изменения среды окружения `-M vexpress-a9` указывает виртуальное "железо".`-kernel /path/to/kernel` указывает путь до образа ядра. `-dtb /path/to/dtb` указывает путь до DTB файла, `-nographic` убирает графику, работа в консоле. `-append "console=ttyAMA0"` настраивает вывод на нашу консоль.
## Результаты выода при последней сборке
- `make distclean`

- `ARCH=arm make defconfig`

- `ARCH=arm make -j6 zImage`

- `ARCH=arm make dtbs`

- `QEMU_AUDIO_DRV=none qemu-system-arm -M vexpress-a9 -kernel /path/to/kernel -dtb /path/to/dtb -nographic -append "console=ttyAMA0"`

