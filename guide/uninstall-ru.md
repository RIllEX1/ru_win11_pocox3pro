<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Удаление

### Почему оно пригодится?

Если вы соблюдали старую инструкцию, ваш раздел будет совсем другой и может иметь последствия если вы не восстановите стоковую таблицу разделов.

Если вы хотите удалить Windows это пригодится вместо удаления разделов вручную и без человеческих ошибок + написание полной инструкции по удалению.

Если вы хотите "восстановить" телефон в обычное состояние и заблокировать Bootloader обратно, то вам нужна стоковая таблица разделов.

### Файлы для установки

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/tag/binares) (старый метод)
- [Модифицированный TWRP](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries) (новый метод)

#### Новый метод

##### Установите и запустите модифицированное рекавеки через ADB 

```cmd
fastboot flash recovery путь\до\twrp.img 
fastboot reboot recovery
```

##### Запустите восстанавливающий скрипт

```cmd
adb shell restore
```

##### Готово!

#### Старый метод (Если новый метод не работает в вашей ситуации)

##### Восстановите GPT (Таблица разделов)
> Замените ```путь\до\gpt_both0.bin``` актуальным путем где находится gpt_both0.bin файл.

```cmd
fastboot flash partition:0 путь\до\gpt_both0.bin
```

##### Очистите userdata чтобы не было БутЛупов и восстановите FS размер
```cmd
fastboot -w
```
