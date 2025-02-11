+++
title = 'Linux'
subtitle = 'Установка, настройка и использование'
date = 2025-02-06T08:42:11+03:00
draft = false
+++

В данном руководстве по установке и настройке операционной системы Linux мы рассмотрим

---

- Установка Debian
- Настройка системы
- Установка программ

# Установка Debian

Скачайте [Balena Etcher](https://etcher.balena.io) 

![Pasted image](20250126112126.png)

Запустите установщик

Скачайте образ [Debian](https://www.debian.org) 

![Pasted image](20250126112229.png)

Загрузите на флешку через Balena Etcher

ё

1. Выберите опцию `Flash from file`
2. Выберите образ Debian
3. Нажмите `Select target`
4. Выберите флешку
5. Нажмите `Flash!`

После окончания загрузки образа на флешку - выключите свой компьютер. Запустите установочную флешку через компьютер через BIOS. Способ выхода в BIOS отличается для каждого компьютера, в зависимости от материнской платы

![Pasted image](20250126114321.png)

Выберите язык и следуйте инструкциям из установщика

![Pasted image](20250126114358.png)

Если при запуске системы у вас отображается чёрный экран - нажмите `Ctrl + F2` и установите драйвера NVIDIA 

В открывшейся консоли введите

```
sudo nano /etc/apt/sources.list
```

Добавьте новую строку с кодом

```
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
```

Затем нажмите `Ctrl+S`, чтобы сохранить изменения в файле и `Ctrl+X`, чтобы выйти. И введите следующие команды

```
sudo apt update
sudo apt install nvidia-driver firmware-misc-nonfree
```

# Настройка системы

## Оптимизация
Для оптимизации работы компьютера установите следующие программы с помощью консоли

Earlyoom

```
sudo apt install earlyoom
```

ZRAM

```
sudo apt install zram-tools
```

Откройте файл `/etc/default/zramswap` при помощи команды

```
sudo nano /etc/default/zramswap
```

И добавьте в него следующие строки

```
ALGO=zstd
PERCENT=100
PRIORITY=100
```

Запустите команду

```
systemctl restart zramswap
```

## Магазин приложений

Далее рекомендуется установить flathub для удобной установки большинства приложений

```
sudo apt install flatpak
sudo apt install plasma-discover-backend-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

После перезагрузки компьютера изменения вступят в силу

# Установка программ

