<h1 align="center">Руководство пользователя [RU]</h1>

# <p align=center>Установка</p>
1. Для установки необходимо скачать архив из чата (доступен после покупки)
2. Распаковать в удобное для вас место
3. Для Windows:
   
   ```shell
   > cd <ваш путь к папке>
   > run.bat
   ```
   
<p align="center">
   <img src="https://github.com/user-attachments/assets/f7a8b7eb-6912-49cc-91d0-52e3795e03c5" />
   </p>
  
4. Для Unix систем:
   ```shell
   $ cd MemeFiWalletConnector
   $ sh run.sh
   ```

<p align="center">
   <img src="https://github.com/user-attachments/assets/0b9b2d2b-9b4c-460c-bf52-b8ee7ab46eec" />
   </p>

<p align="center">
   <img src="https://github.com/user-attachments/assets/ffb648bd-ef64-4e67-af42-9effa0b79ac7" />
   </p>


   <p align="center">После запуска папка будет выглять следующим образом</p>

<p align="center">
   <img src="https://github.com/user-attachments/assets/2bdded95-12bf-4bb4-90de-3d57a19b186a" />
   </p>


# <p align=center>Настройка конфига</p>

Конфиг находится по пути ```MemeFiWalletConnector/resources/.env```

```config
API_ID=
API_HASH=

DISABLE_RANDOM_DELAY_IN_RUN=False
RANDOM_DELAY_IN_RUN=[5, 60]

NOT_START_WITHOUT_PROXY=True
```
<p align="center">
   <img src="https://github.com/user-attachments/assets/22f9c367-76fd-4a21-88e9-8264867a68e9" />
   </p>


| Settings                      | Description                                                                                |
|-------------------------------|--------------------------------------------------------------------------------------------|
| ```API_ID``` и ```API_HASH``` | Задаем как в других ботах (например в [MemeFiBot](https://github.com/sirbiprod/MemeFiBot)) |
| ```DISABLE_RANDOM_DELAY_IN_RUN``` |  Отключение отложенного запуска сессий (изначально равно ```False```). Если хотите запускать все сессии одновременно - укажите ```True``` |
| ```RANDOM_DELAY_IN_RUN``` | Диапозон задержки запуска сессий (указывается в секундах ```[5, 60]```, запуск происходит рандомно между 5 и 60 секундами) |
| ```NOT_START_WITHOUT_PROXY``` | Запускать ли программу без прокси. Для запуска без прокси нужно указать ```False``` |

Заполненный файл ```.env``` выглядит так:

<p align="center">
   <img src="https://github.com/user-attachments/assets/d8a1cb1f-986f-49f0-a3a8-5a4bb325dce4" />
   </p>

# <p align=center>Добавление сессий</p>

Для добавления сессий необходимо переместить ваши **pyrogram** файлы с расширением ```.session``` в папку ```MemeFiWalletConnector/resources/sessions``` (папка будет создана при первом запуске run.bat/run.sh)

Далее ваши прокси будут привязаны к вашим прокси поэтапно. Т.е. Первая строчка прокси привязывается к первому файлу в папке ```session``` и так далее. Если у вас строк прокси меньше чем сессий, то на последующие сессии будет назначаться прокси начиная с 1

# <p align=center>Добавление прокси</p>

Для добавления прокси вам необходимо прописать / заменить в файле ```MemeFiWalletConnector/resources/proxies.txt``` (Вы можете заранее переместить ваши файлы ```.session``` и ```proxies.txt``` в папку ```resources```)

# <p align=center>Работа со скриптом</p>

Если вы выполнили все предыдущие шаги то можете приступать к этому пункту.
Для коннекта SUI и Linea кошельков к вашим сессиям вам необходимо:

**1**. Вводите пункт ```7``` (Распределяет прокси на ваши сессии)

<p align="center">
   <img src="https://github.com/user-attachments/assets/fedab571-76ad-480c-80bd-2ee0be43679b" />
   </p>

**2**. Вводите пункт ```1``` (Анализирует ваши аккаунты, отображает привянный прокси, ник, имя, адреса кошельков Linea и Sui)

   <p align="center">
   <img src="https://github.com/user-attachments/assets/a06db485-a817-440b-b037-a9b50fa9bcd2" />
   </p>

**3**. Вводите пункт ```4``` (Генерирует недостающие кошельки для сессий на основе файла ```wallets_dump.json```)

<p align="center">
   <img src="https://github.com/user-attachments/assets/549483b5-19e1-409b-9c44-30bbde4aef92" />
   </p>

**4**. Вводите пункт ```5``` (Создает файл ```payload_for_sign.json``` для последующей подписи). Созданный файл вам необходимо отправить [@sirbiprod](https://t.me/sirbiprod) для генерации файла ```signatures.json```

<p align="center">
   <img src="https://github.com/user-attachments/assets/9a67dfe2-34f6-473e-9c52-1c456d0629c1" />
   </p>

**5**. Перемещаете полученый от @sirbiprod файл ```signatures.json``` по пути ```MemeFiWalletConnector\resources\signatures.json```

<p align="center">
   <img src="https://github.com/user-attachments/assets/747218f1-99b7-4486-a8c4-cb08db939a80" />
   </p>

**6**. Вводите пункт ```6``` (Подписывает коннект кошельков с помощью файла ```signatures.json```)

<p align="center">
   <img src="https://github.com/user-attachments/assets/754a656c-b473-4816-ac00-cd0be7f8bf84" />
   </p>

**7**. (Опционально) Вводите пункт ```1``` для проверки подключения кошельков

<p align="center">
   <img src="https://github.com/user-attachments/assets/89cad2fb-9965-4a88-b56c-86786dc5f274" />
   </p>

   
# <p align="center">Структура resources</p>

<p align="center">
   <img src="https://github.com/user-attachments/assets/8b576c61-9007-4bc4-8bb1-222486ffdea5" />
   </p>

| Files                         | Description                                                                                |
|-------------------------------|--------------------------------------------------------------------------------------------|
| session | Папка с файлами сессий ```.session``` |
| .env | Файл с настройками |
| payload_for_sign.json | Файл с кошельком и строкой, необходимой для подписи коннекта. Его необходимо отправить @sirbiprod (создается после выполнения 5 пункта) |
| proxies.txt | Файл с вашими прокси |
| sessions_config.json | Файл с информациии о имени сессии, привязанному прокси, привязанному UserAgent |
| wallets_dump.json | В этом файле отображаются ваши сессии и кошельки в статусах ```connected```, ```last_session_info``` и ```wait_sign```. Это ваша личная база данных  |
| signatures.json | Файл, необходимый для подписи подключения кошелька, вы сами помещаете его в эту папку (файл вы получаете от [@sirbiprod](https://t.me/sirbiprod)) |

# <p align=center>Возможные ошибки</p>

1. Ошибка API_ID / API_HASH
   
    ```shell
   missing API_ID: Field required
   missing API_HASH: Field required
   ```
   Вам необходимо настроить ```API_ID``` и ```API_HASH``` в файле ```MemeFiWalletConnector/resources/.env```
   <p align="center">
   <img src="https://github.com/user-attachments/assets/0db3d98b-6d4f-42a3-af76-96e28a0241d4" />
   </p>


2. Ошибка ModuleNotFoundError bip_utils / eth_utils (Windows)

   <p align="center">
   <img src="https://github.com/user-attachments/assets/76168010-7a1b-4442-81c0-8ce4c524f0df" />
   </p>

   Вам необходимо удалить папку ```venv``` и запустить еще раз файл ```run.bat``` который находиться по пути ```MemeFiWalletConnector/run.bat```


3. Ошибка ```DEBUG | utils.proxies | Write empty proxy file```

<p align="center">
   <img src="https://github.com/user-attachments/assets/4acca342-f201-429b-a75b-7ae28972d673" />
   </p>
   
   Вам необходимо заполнить файл ```proxies.txt```, который находится по пути ```MemeFiWalletConnector/resources/proxies.txt``` либо в ```.env``` для параметра ```NOT_START_WITHOUT_PROXY``` указать ```False```.


# <p align=center>Контакты</p>

Для связи можете использовать закрытый чат (доступен после покупки по ссылке !!!!) либо написать конкретный вопрос в лс @sirbiprod

   

