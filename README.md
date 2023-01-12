## Whatsapp Bot

| Feature  | Status |
| ------------- | ------------- |
| [WWebJS Library](https://github.com/pedroslopez/whatsapp-web.js/) | ✅ |
| Dialogflow Integration | ✅  |
| Save to MySQL DB | ✅  |
| Save to JSON File as DB | ✅  |
| QR Scan in Terminal | ✅ |
| Easily deploy to Heroku  | ✅  |
| Buttons support | ✅ℹ️  (May not work in multi-device mode)|
| Send Voice Notes | ✅ |

## Requirements
- NodeJS v16+
- VSCode code editor [Download](https://code.visualstudio.com/download)
- MySql (optional) only applies if using 'mysql' mode
- Dialogflow account (optional) only applies if using 'dialogflow' mode

### Buttons

To make use of buttons, you only need to call method __sendMessageButton__ which is in `./controllers/send`
Example:

``` javascript
const { sendMessageButton } = require('./controllers/send')

await sendMessageButton(
    {
        "title":"¿Que te interesa ver?",
        "message":"Recuerda todo este contenido es gratis y estaria genial que me siguas!",
        "footer":"Gracias",
        "buttons":[
            {"body":"😎 Cursos"},
            {"body":"👉 Youtube"},
            {"body":"😁 Telegram"}
        ]
    }
)

```

## Voice Notes

The bot can send voice notes using the native format so it doesn't appear as forwarded. In this example, I will send the file __PTT-20220223-WA0000.opus__ which can be found in the directory __/mediaSend__

``` javascript
const { sendMediaVoiceNote } = require('./controllers/send')

await sendMediaVoiceNote(client, from, 'PTT-20220223-WA0000.opus')
```

## Installation
__Download or Clone repository__

```
git clone https://github.com/jzvi12/bot-whatsapp-v1.git
```

__If using Ubuntu or any other Linux distro__
> Make sure to install the following packages:
```
sudo apt-get install -y libgbm-dev
sudo apt install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget
```

__Install dependencies (npm install)__
> From the app root directory, execute the following command:

```
npm i
``` 

__Configure .env File__
> Create a file and name it `.env` (including period) from the provided template file `.env.example`:
```
######DATABASE: none, mysql, dialogflow

DEFAULT_MESSAGE=true
SAVE_MEDIA=true
PORT=3000
DATABASE=none
LANGUAGE=es
SQL_HOST=
SQL_USER=
SQL_PASS=
SQL_DATABASE=
DIALOGFLOW_MEDIA_FOR_SLOT_FILLING=false
GDRIVE_FOLDER_ID=
```

__Start the bot__
> From the app root directory, execute the following command:
`npm run start`

__Scan QR code with your Phone__
If testing in your local PC, you can also open browser and go to http://127.0.0.1:3000/qr

# ¿Quieres ver como se creó? 🤖
- [Ver Video 1](https://www.youtube.com/watch?v=A_Xu0OR_HkE)
- [¿Como instalarlo? (Actulización)](https://youtu.be/5lEMCeWEJ8o)

## ¿Como usarlo el chatbot de whatsapp?
> Escribe un mensaje al whatsapp que vinculaste con tu BOT

![](https://i.imgur.com/OSUgljQ.png)

> Ahora deberías  obtener una respuesta por parte del BOT como la siguiente, ademas de esto tambien se crea un archivo excel
con el historial de conversación  con el número de tu cliente
