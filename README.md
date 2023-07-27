# Github Push-Notifier
The whatsapp and telegram  bot built using Twilio APIs which sends a Whatsapp message when code is pushed to a repository.

<h1 align="center">Github Push Notify Action 🚀</h1>


<!-- > A github action which sends a Whatsapp message when code is pushed to a repository. -->

<!-- ### :house_with_garden: [Homepage](https://github.com/g-sudarshan/whatsapp-push-notify-action) -->

### Usage
1. Create account in twilio [here](https://www.twilio.com/).  
2. From your twilio dashboard fetch Account Sid and Auth Token.  
3. To encrypt them, create new secrets in your repository named ```account_sid, auth_token, to_whatsapp_no``` and give it's value.  
4. Create a ```.github/workflows/whatsapp-push-notify-action.yml```.  
5. Add the following properties to ```whatsapp-push-notify-action.yml``` file   

```name: When a push occurs in the master branch, a private message is sent on the Whatsapp and telegram.
name: Notifier

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:

  notifyWhatsApp:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Notification WhatsApp
        id: whatsapp-notify
        env:
          account_sid: ${{ secrets.twilio_account_sid }}
          auth_token: ${{ secrets.twilio_auth_token }}
          to_whatsapp_no: ${{ secrets.twilio_to_whatsapp_no }}
          message: "Code Pushed in main branch of https://github.com/imprs21/GitHub_Push"
        

  notifyTelegram:
    runs-on: ubuntu-latest
    steps:
    - name: send custom message
      uses: appleboy/telegram-action@master
      with:
        to: ${{ secrets.TELEGRAM_TO }}
        token: ${{ secrets.TELEGRAM_TOKEN }}
        message: |
          Code Pushed in main branch of https://github.com/imprs21/GitHub_Push
```

## 📸 Whatsapp Push Notifier Output

![whatsapp-push-notify-screenshot](https://github.com/imprs21/GitHub_Push/blob/main/Github%20Push%20Notifier%201.jpg)


## 📸 Telegram Push Notifier Output

![Telegram-push-notify-screenshot](https://github.com/imprs21/GitHub_Push/blob/main/Github%20Push%20Notifier.jpg)





