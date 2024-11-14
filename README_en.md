<h1 align="center">User's Guide [EN]</h1>

# <p align=center>Installation</p>
1. To install, you need to download the archive from the chat (available after purchase)
2. Unpack to a place convenient for you
3. For Windows:
   
   ```shell
   > cd <your folder path>
   > run.bat
   ```
   
<p align="center">
   <img src="https://github.com/user-attachments/assets/f7a8b7eb-6912-49cc-91d0-52e3795e03c5" />
   </p>
  
4. For Unix systems:
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


   <p align="center">After launching, the folder will be updated as follows</p>

<p align="center">
   <img src="https://github.com/user-attachments/assets/2bdded95-12bf-4bb4-90de-3d57a19b186a" />
   </p>


# <p align=center>Configuring the config</p>

The config is located on the path ``MemeFiWalletConnector/resources/.env``

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
| ``API_ID`` and ``API_HASH`` | Set as in other bots (for example, in [MemeFiBot](https://github.com/sirbiprod/MemeFiBot )) |
| ``DISABLE_RANDOM_DELAY_IN_RUN`` | Disabling delayed session start (initially set to ``False``). If you want to start all sessions at the same time, specify ``True`` |
| ``RANDOM_DELAY_IN_RUN`` | The range of delay in starting sessions (specified in seconds ``[5, 60]``, the launch occurs randomly between 5 and 60 seconds) |
| ``NOT_START_WITHOUT_PROXY`` | Whether to run the program without a proxy. To run without a proxy, you need to specify ``False`` |

The completed file ``.env`` looks like this:

<p align="center">
   <img src="https://github.com/user-attachments/assets/d8a1cb1f-986f-49f0-a3a8-5a4bb325dce4" />
   </p>

# <p align=center>Adding sessions</p>

To add sessions, you need to move your **pyrogram** files with the extension ``.session`` to the folder ``MemeFiWalletConnector/resources/sessions`` (the folder will be created at the first launch run.bat/run.sh )

Next, your proxies will be linked to your proxies in stages. I.e., the first line of the proxy is linked to the first file in the folder ``session`` and so on. If you have fewer proxy rows than sessions, then a proxy will be assigned to subsequent sessions starting from 1

# <p align=center>Adding a proxy</p>

To add a proxy, you need to register /replace in the file ``MemeFiWalletConnector/resources/proxies.txt `` (You can move your files in advance ``.session`` and ``proxies.txt `` to the folder ``resources``)

# <p align=center>Working with the script</p>

If you have completed all the previous steps, then you can proceed to this point.
To connect SUI and Linea wallets to your sessions, you need:

**1**. Enter the item ``7`` (Distributes the proxy to your sessions)

<p align="center">
   <img src="https://github.com/user-attachments/assets/fedab571-76ad-480c-80bd-2ee0be43679b" />
   </p>

**2**. Enter the item ``1`` (Analyzes your accounts, displays the associated proxy, nickname, name, addresses of Linea and Sui wallets)

   <p align="center">
   <img src="https://github.com/user-attachments/assets/a06db485-a817-440b-b037-a9b50fa9bcd2" />
   </p>

**3**. Enter the item ``4`` (Generates missing wallets for sessions based on the file ``wallets_dump.json```)

<p align="center">
   <img src="https://github.com/user-attachments/assets/549483b5-19e1-409b-9c44-30bbde4aef92" />
   </p>

**4**. Enter the item ``5`` (Creates the file ``payload_for_sign.json`` for subsequent signature). You need to send the created file to [@sirbiprod](https://t.me/sirbiprod ) to generate the file ``signatures.json``

<p align="center">
   <img src="https://github.com/user-attachments/assets/9a67dfe2-34f6-473e-9c52-1c456d0629c1" />
   </p>

**5**. Move the file ```signatures.json``` received from @sirbiprod along the path ``MemeFiWalletConnector\resources\signatures.json``

<p align="center">
   <img src="https://github.com/user-attachments/assets/747218f1-99b7-4486-a8c4-cb08db939a80" />
   </p>

**6**. Enter the item ``6`` (Signs the wallet connection using the file ``signatures.json``)

<p align="center">
   <img src="https://github.com/user-attachments/assets/754a656c-b473-4816-ac00-cd0be7f8bf84" />
   </p>

**7**. (Optional) Enter the item ``1`` to verify the connection of wallets

<p align="center">
   <img src="https://github.com/user-attachments/assets/89cad2fb-9965-4a88-b56c-86786dc5f274" />
   </p>

   
# <p align="center">The resources structure</p>

<p align="center">
   <img src="https://github.com/user-attachments/assets/8b576c61-9007-4bc4-8bb1-222486ffdea5" />
   </p>

| Files                         | Description                                                                                |
|-------------------------------|--------------------------------------------------------------------------------------------|
| session | Folder with session files ``.session`` |
| .env | Settings file |
| payload_for_sign.A json | File with the wallet and the string required to sign the connection. It must be sent to @sirbiprod (created after completing step 5) |
| proxies.txt | File with your proxies |
| sessions_config.json | File with information about the session name, linked proxy, linked UserAgent |
| wallets_dump.json | This file displays your sessions and wallets in the statuses ``connected``, `last_session_info`` and `wait_sign''. This is your personal database |
| signatures.The json | file required to sign the wallet connection, you put it in this folder yourself (you receive the file from [@sirbiprod](https://t.me/sirbiprod )) |

# <p align=center>Possible errors</p>

1. API_ID / API_HASH error
   
    ```shell
   missing API_ID: Field required
   missing API_HASH: Field required
   ```
   You need to configure ``API_ID`` and ``API_HASH`` in the file ``MemeFiWalletConnector/resources/.env``
   <p align="center">
   <img src="https://github.com/user-attachments/assets/0db3d98b-6d4f-42a3-af76-96e28a0241d4" />
   </p>


2. ModuleNotFoundError bip_utils / eth_utils error (Windows)

   <p align="center">
   <img src="https://github.com/user-attachments/assets/76168010-7a1b-4442-81c0-8ce4c524f0df" />
   </p>

   You need to delete the ```venv``` folder and run the ```run.bat``` file again which is located on the path ``MemeFiWalletConnector/run.bat``


3. Error ```DEBUG | utils.proxies | Write empty proxy file```

<p align="center">
   <img src="https://github.com/user-attachments/assets/4acca342-f201-429b-a75b-7ae28972d673" />
   </p>
   
   You need to fill in the file ``proxies.txt`` which is on the way ``MemeFiWalletConnector/resources/proxies.txt `` or in ``.env`` for the parameter ``NOT_START_WITHOUT_PROXY`` specify ```False```.


# <p align=center>Contacts</p>

You can use a private chat for communication (available after purchase via the link !!!!) or write a specific question in the bos @sirbiprod
