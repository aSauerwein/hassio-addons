# Home Assistant Add-on: Tesla-Invoices

## Requirements

To use the component, you will need an application to generate a Tesla refresh token:

- Android: [Tesla Tokens](https://play.google.com/store/apps/details?id=net.leveugle.teslatokens)
- iOS: [Auth App for Tesla](https://apps.apple.com/us/app/auth-app-for-tesla/id1552058613)
- TeslaFi: [Tesla v3 API Tokens](https://support.teslafi.com/en/communities/1/topics/16979-tesla-v3-api-tokens)
- Chromium/Edge: [Chromium Tesla Token Generator](https://github.com/DoctorMcKay/chromium-tesla-token-generator)


## Installation

1. Add my [add-ons repository][addons-repo] to Home Assistant or click the button below to open my add-on repository on your Home Assistant instance.

   [![Open add-on repo on your Home Assistant instance][repo-btn]][addon]

2. Install the "Tesla-Invoices" Add-on
3. configure at least `access_token` and `refresh_token` ( see [Requirements](#requirements) )
4. start Add-on

## Configuration
Add-on configuration:
```yaml
access_token: ""
refresh_token: ""
enable_email_export: false
enable_subscription_invoice: true
email:
  from: sender_mail@example.com
  to: receiver_mail@example.com
  mailserver: mailserver.example.com
  port: 587
  user: ""
  password: ""
```
### Option: `access_token` (required)
The access_token retrieved from on of the authentication apps ( see [Requirements](#requirements) )

### Option: `refresh_token` (required)
The refresh_token retrieved from on of the authentication apps ( see [Requirements](#requirements) )

### Option: `enable_email_export`
`true` if invoices should be sent as email

### Option: `email` ( required if `enable_email_export` is set)
yaml dictionary of email server settings
- `from`: Email Sender Address
- `to`: Email Receiver Address
- `mailserver`: Mailserver IP or FQDN
- `port`: Port for SMTP Transfer ( usualy 25 for plaintext and 587 for SSL/TLS)
- `user`: Username to authenticate with mailserver
- `password`: Passowrd to authenitcate with mailserver

[addon]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FaSauerwein%2Fhassio-addons
[addons-repo]: https://github.com/aSauerwein/hassio-addons
[repo-btn]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg

## Usage
* the Add-on runs in daemon mode where invoices of the current month are downloaded every 15 minutes
* when accesing the Web-UI all Invoices can be viewed and donwnloaded in Homeassistant UI
* to download all invoices it is necessary to connect to the container by ssh
    ```bash
    ~ # docker exec -it addon_61d34ee3_tesla_invoices ./download_v2.py
    Bitte gewünschten Monat im Format 'YYYY-MM' bzw. 'cur' oder 'prev' oder 'all' für aktuellen oder vorherigen Monat oder alles eingeben [prev]: all
    ```
* `refresh_token` and `access_token` are stored inside `/data/` in the container itself. Token from `options` are only used if they are newer. If you switch to a different tesla account it may be necessary to delete the files inside `/data/` 
