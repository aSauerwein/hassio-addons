# Home Assistant Add-on: Tesla-Invoices

A self-hosted script to download tesla invoices and export as mail

Source Code: https://github.com/aSauerwein/tesla-invoices

## About

- Written in python
- Data is stored in `/data/`
- Caddy Webserver to show/download invoices in HA
- runs the docker image provided at [dockehub](https://hub.docker.com/r/asauerwein/tesla-invoices)

![Ingress](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2FaSauerwein%2Fhassio-addons%2Fdev%2Ftesla-invoices%2Fconfig.yaml&query=ingress&label=Ingress)
![Arch](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2FaSauerwein%2Fhassio-addons%2Fdev%2Ftesla-invoices%2Fconfig.yaml&query=arch&label=Arch&color=green)


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



[addon]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FaSauerwein%2Fhassio-addons
[addons-repo]: https://github.com/aSauerwein/hassio-addons
[repo-btn]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg