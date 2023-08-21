<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Обновление драйверов

### Файлы для установки

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [Модифицированный TWRP](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)
- [Автоматически обновитель драйверов](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Драйвера](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

#### Запустите TWRP рекавери через команду в ADB на ПК

```cmd
fastboot boot <twrp.img>
```

> Если у вас TWRP уже установлено, просто зажмите кнопку включения/выключения и громкость+ в выключенном состоянии телефона

> Вам надо отключить MTP в Mount
#### Запустите скрипт в ADB

```cmd
adb shell msc.sh
```

### Поставьте разметку буквы для диска

#### Запустите Управление дисками или другую программу для разметки дисков

> Когда X3 Pro отображается как диск в системе

```cmd
diskpart
```


### Разметьте `X` к тому Windows 

#### Выберите Windows том телефона
> Используйте `list volume` чтобы найти его, он будет называться "WINVAYU"

```diskpart
select volume <number>
```

#### Разметка буквы диска на "X"
```diskpart
assign letter=x
```

#### Выход из разметки
```diskpart
exit
```


### Посмотрите как тип панели вы имеете

```cmd
adb shell cat /proc/cmdline
```
> Посмотрите за `msm_drm.dsi_display0` в самом конце

> Если ваш телефон `Tianma`, `msm_drm.dsi_display0` будет назван `dsi_j20s_36_02_0a_video_display`

> Если ваш телефон `Huaxing`, `msm_drm.dsi_display0` будет назван `dsi_j20s_42_02_0b_video_display`

### Установка драйверов

> Замените `<vayudriversfolder>` актуальным путем до драйверов
> Замените `<paneltype>` актуальным типом панели (tianma/huaxing)

```cmd
.\driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu_<paneltype>.txt -r <vayudriversfolder> -p X:
```


### Запуститесь в Windows через UEFI образ

```
fastboot flash boot <uefi.img>
```

## Готово!
