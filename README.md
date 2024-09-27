# Задание 19 - Кросс-компиляция
## Задания
Собрать vanilla версию ОС Linux со стандартной конфигурацией. Для проверки ядра на работоспособность воспользоваться утилитой QEMU 

## Используемые цели и утилиты 
Для очистки ядра воспользуемся следующей целью:
- `make distclean`
Для создания стандратной конфигурации воспользуемся целью:
- `ARCH=arm make defconfig`
Сборка ядра осуществляется при помощи следующей цели:
- `ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make -j6 zImage` - сборка образа на 6-ти ядрах
Для сборки DTB файла воспользуемся следующей целью:
- `ARCH=arm make dtbs`
Запуск QEMU эмулятора осуществляется следующей командой:
- `QEMU_AUDIO_DRV=none qemu-system-arm -M vexpress-a9 -kernel /path/to/kernel -dtb /path/to/dtb -nographic -append "console=ttyAMA0"`
В данной команде `QEMU_AUDIO_DRV=none` отключает аудион на эмуляторе при помощи изменения среды окружения `-M vexpress-a9` указывает виртуальное "железо".`-kernel /path/to/kernel` указывает путь до образа ядра. `-dtb /path/to/dtb` указывает путь до DTB файла, `-nographic` убирает графику, работа в консоле. `-append "console=ttyAMA0"` настраивает вывод на нашу консоль.
## Результаты выода при последней сборке
- `ARCH=arm make defconfig`
![Screenshot from 2024-09-27 21-30-35](https://github.com/user-attachments/assets/c12a5c3c-16ba-4303-beea-903057a224ea)

- `ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make -j6 zImage`
![Screenshot from 2024-09-27 22-06-48](https://github.com/user-attachments/assets/9bf7fc81-1856-46ae-a859-9ddbe91df0fe)

- `ARCH=arm make dtbs`
![Screenshot from 2024-09-27 22-41-26](https://github.com/user-attachments/assets/a27d120f-b321-48da-b508-034ce5ecf0bb)

- `QEMU_AUDIO_DRV=none qemu-system-arm -M vexpress-a9 -kernel /path/to/kernel -dtb /path/to/dtb -nographic -append "console=ttyAMA0"`
![Screenshot from 2024-09-27 22-20-09](https://github.com/user-attachments/assets/18c15354-d081-4a22-b2c6-40a0b78fa88d)
Результат запуска:
![Screenshot from 2024-09-27 22-20-16](https://github.com/user-attachments/assets/07c0d53e-36e8-45ea-9551-40a2f07cfa75)

