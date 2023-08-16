<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Установке

## Установка Windows

### Файлы

- [Windows на ARM образе (Windows 11 рекомендована)](https://uupdump.net/)
- [UEFI образ](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [ОбновлениеДрайверов.exe](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Драйвера](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)
- [Модифицированный TWRP](../../../releases/Recoveries) (должно быть уже установлено)

#### Запуститесь в TWRP

#### Запустите MSC скрипт

> Если просит запустить еще раз, сделайте это.

```cmd
adb shell msc
```

  

### Привяжите букву к тому
  

#### Запустите Управление дисками Windows

> Когда X3 Pro отображается как диск
> (если нет, переподключите его)

```cmd
diskpart
```


### Привяжите букву `X` на том Windows'а

#### Выберите том Windows телефона
> Используйте `list volume` чтобы найти его, он называется "WINVAYU"

```diskpart
select volume <number>
```

#### Привяжите "X" к тому
```diskpart
assign letter x
```

### Привяжите "Y" к загрузочному тому

#### Выберите загрузочный том
> Используйте `list volume` чтобы найти его, он называется "ESPVAYU"

```diskpart
select volume <number>
```

#### Привяжите букву "Y"

```diskpart
assign letter y
```

#### Выйти из diskpart
```diskpart
exit
```

  
  

### Установка

> Замените `путь\до\install.wim` актуальным путем до install.wim,

> `install.wim` находится ISO
> (также оно может называться `install.esd`)
> Вы можете их получить через ISO образ системы

```cmd
dism /apply-image /ImageFile:path\to\install.wim /index:1 /ApplyDir:X:\
```

### Проверьте какой тип панели у вас стоит

> Откройте cmd/командная строка

```cmd
adb shell "dmesg | grep dsi_display_bind"
```
> Если ваша панель: `Tianma`, то оно названо `dsi_j20s_36_02_0a_video_display`

> Если ваша панель: `Huaxing`, то оно названо `dsi_j20s_42_02_0b_video_display`

### Установка драйверов

> Замените `path\to\drivers` на актуальную папку с драйверами
> Замените `paneltype` на актульный тип панели (tianma/huaxing)

```cmd
.\driverupdater.exe -d path\to\drivers\definitions\Desktop\ARM64\Internal\vayu_paneltype.txt -r path\to\drivers -p X:
```

  

### Создайте Windows bootloader файлы

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

  
  

## Разрешить неподписанные драйвера

> Если вы это не сделайте, у вас будут синие экраны смерти

```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Отвяжите буквы от томов
  
> Так они не останутся тут после отключение телефона

```cmd
diskpart
```


#### Выберите том Windows телефона
> Используйте `list volume` чтобы найти его, он называется "WINVAYU"

```diskpart
select volume <number>
```

#### Отвяжите букву "X"
```diskpart
remove letter x
```

#### Выберите загрузочный том телефона
> Используйте `list volume` чтобы найти его, он называется "ESPVAYU"

```diskpart
select volume <number>
```

#### Отвяжите букву "Y"
```diskpart
remove letter y
```

#### Выйти из diskpart
```diskpart
exit
```

## Запуститесь в Windows

### Переместите `<uefi.img>` файл на телефон

```cmd
adb push <uefi.img> /sdcard
```

#### Если у вас есть карта памяти то используйте

```cmd
adb push <uefi.img> /external_sd
```


### Сделайте бекап вашего основного образа
> Надо сделать **1 РАЗ!!!**

> Переместите его на карту памяти, если это возможно


### Установите uefi образ через TWRP
Перейдите в `uefi.img` файл и установите его в TWRP

## Запуститесь в Android
> Используйте ваше бекап образ через TWRP

## Готово!
