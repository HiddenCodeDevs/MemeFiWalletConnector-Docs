<h1 align="center">Руководство пользователя</h1>

# Установка
1. Для установки необходимо скачать архив из чата (доступен после покупки)
2. Распаковать в удобное для вас место
3. Для Windows:
   ```shell
   > cd <ваш путь к папке>
   > run.bat
   ```
   
   ![image](https://github.com/user-attachments/assets/66d5e515-0553-4e53-86c8-529f5bbc8365)
4. Для Unix систем:
   ```shell
   $ cd MemeFiWalletConnector
   $ sh run.sh
   ```

# Настройка конфига

Конфиг находится по пути /resources/.env

```config
API_ID=
API_HASH=

DISABLE_RANDOM_DELAY_IN_RUN=False
RANDOM_DELAY_IN_RUN=[5, 60]

NOT_START_WITHOUT_PROXY=True
```

| Settings                      | Description                                                                                |
|-------------------------------|--------------------------------------------------------------------------------------------|
| ```API_ID``` и ```API_HASH``` | Задаем как в других ботах (например в [MemeFiBot](https://github.com/sirbiprod/MemeFiBot)) |
| ```DISABLE_RANDOM_DELAY_IN_RUN``` |  Отключение отложенного запуска сессий (изначально равно ```False```). Если хотите запускать все сессии одновременно - укажите ```True``` |
| ```RANDOM_DELAY_IN_RUN``` | Диапозон задержки запуска сессий (указывается в секундах ```[5, 60]```, запуск происходит рандомно между 5 и 60 секундами) |
| ```NOT_START_WITHOUT_PROXY``` | Запускать ли программу без прокси. Для запуска без прокси нужно указать ```False``` |


# Добавление сессий

Для добавления сессий необходимо переместить ваши **pyrogram** файлы с расширением ```.session``` в папку ```MemeFiWalletConnector/resources/sessions``` (папка будет создана при первом запуске run.bat/run.sh)

# Добавление прокси

//тут будет инфа по прокси

# Работа со скриптом

Если вы выполнили все предыдущие шаги то можете приступать к этому пункту.
Для коннекта SUI и Linea кошельков к вашим сессиям вам необходимо:
//тут будет инфа по работе

# Возможные ошибки

1. Ошибка API_ID/API_HASH
    ```shell
   missing API_ID: Field required
   missing API_HASH: Field required
   ```
   Вам необходимо настроить ```API_ID``` и ```API_HASH``` в файле ```resources/.env```
   
   ![image](https://github.com/user-attachments/assets/0db3d98b-6d4f-42a3-af76-96e28a0241d4)

2. Ошибка bip_utils / eth_utils (Windows)
   
![image](https://github.com/user-attachments/assets/76168010-7a1b-4442-81c0-8ce4c524f0df)

Вам необходимо удалить папку ```(0)``` и запустить файл ```install_blake2b.bat``` который находиться по пути ```MemeFiWalletConnector/install_blake2b.bat```

![image](https://github.com/user-attachments/assets/032f1458-3bc6-4b15-a4f0-64e0084fdf3b)

После этого запустите еще раз ```run.bat```

3. Ошибка ModuleNotFoundError
   ```shell
   ModuleNotFoundError: No module named 'pyrogram' #вместо pyrogram может быть любая другая библиотека
   ```
![image](https://github.com/user-attachments/assets/787ca261-45af-4d53-90cb-6755f9556a58)

   Вам необходимо удалить папку ```(0)``` и запустить еще раз файл ```run.bat```

4. //возможные ошибки 

