<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 PRO

## Установка

## Разделивание телефона

### Файлы

- [Модифицированный TWRP](../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Запись
> [Предупреждение]  
> Если вы хоть раз удалите раздел через diskpart, Windows отправит UFS команду которая удаляет ВСЁ UFS ХРАНИЛИЩЕ!!!
> 
> Все файлы удалятся! Сделайте бекап (восстановление).
> 
> Не запускайте одну команду дважды.
> 
> НЕ ПЕРЕЗАПУСКАЙТЕ ВАШ ТЕЛЕФОН если вы думаете что вы сделали ошибку, обратитесь за помощью в нашем телеграмм чате [Телеграмм чат](https://t.me/winonvayualt).
> 
>
> Не запускайте команды в разброс, вводите их по очереди!
>
> ТЕЛЕФОН МОЖЕТ ЛЕГКО ОКИРПИЧИТЬСЯ ЕСЛИ ВЫ ВВЕДЕТЕ ИХ В НЕПРАВИЛЬНОМ ПОРЯДКЕ!!!

##### Установите модифицированный TWRP
```cmd
fastboot flash recovery path\to\twrp.img
fastboot reboot recovery
```

##### Запустите разделительный скрипт

> Если попросит запустить еще раз, сделайте это

```cmd
adb shell partition
```

#### Посмотрите, запускается ли Android после этих действий
Простой перезапуск телефона, если у вас запустится Android и можно им пользоваться, запускать приложения и тд, то вы сделали все правильно


## [Следующие этапы: Installing Windows](/guide/install-2-en.md)
