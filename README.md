Home Assistant Custom Integration for Midea Group(Hualing, Senville, Klimaire, AirCon, Century, Pridiom, Thermocore, Comfee, Alpine Home Air, Artel, Beko, Electrolux, Galactic, Idea, Inventor, Kaisai, Mitsui, Mr. Cool, Neoclima, Olimpia Splendid, Pioneer, QLIMA, Rotenso, Royal Clima, Qzen, Toshiba, Carrier, Goodman, Friedrich, Samsung, Kenmore, Trane, Lennox, LG and much more) Air Conditioners via LAN.

Tested with Home Assistant 2021.7.2.

## Attention!!!
Version >= 0.1.27, The ENTITY ID of the climate devices has been changed. if you have any problem with an old entity being "unavailable", you should check whats the new ID name of the entity and change it in lovelace.

## Installation

### Install from HACS
[![Type](https://img.shields.io/badge/Type-Custom_Component-orange.svg)](https://github.com/mac-zhou/midea-ac-py) [![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

Search the HACS Store for ```midea_ac```

### Install manually
1. Clone this repo
2. Place the `custom_components/midea_ac` folder into your `custom_components` folder

## Configuration

**Configuration variables:**  

key | description | example 
:--- | :--- | :---
**platform (Required)** | The platform name. | midea_ac
**host (Required)** | Midea AC Device's IP Address. | 192.168.1.100
**id (Required)** | Midea AC Device's applianceId. | 123456789012345
**token (Optional)** | Midea AC Device's token, V3 is required. | ACEDDA53831AE5DC...(Length 128)
**k1 (Optional)** | Midea AC Device's k1, V3 is required. | CFFA10FC...(Length 64)
**temp_step (Optional)** | Step size for temperature set point, default is 1.0 | 0.5
**prompt_tone (Optional)** | Prompt Tone, default is true. | false
**keep_last_known_online_state (Optional)** | Set this to true if you see too many  `unavailable` in log. | true
**use_fan_only_workaround (Optional)** | Set this to true if you need to turn off device updates because they turn device on and to fan_only | true

**Example configuration.yaml:**
```yaml
climate:
  - platform: midea_ac
    host: 192.168.1.100
    id: 123456789012345
    # v3 need token and k1(key)
    # token: ACEDDA53831AE5DC...(Length 128)
    # k1: CFFA10FC...(Length 64)
```

## How to Get Configuration variables:
- `midea-discover` can help you discover Midea devices from the LAN.
  ```zsh
    pip3 install msmart
    midea-discover
  ```
  - Basic Usage
  ```
  Usage: midea-discover [OPTIONS]

    Discover Midea Deivces and Get Device's info

  Options:
    -d, --debug           Enable debug logging
    -c, --amount INTEGER  Number of broadcast packets, default is 1.
                          if you have many devices, you may change this value.
    -a, --account TEXT    Your email address for your Midea account.
    -p, --password TEXT   Your password for your Midea account.
    -i, --ip TEXT         IP address of Midea device. you can use:
                          - broadcasts don't work.
                          - just get one device's info.
                          - an error occurred.
    --help                Show this message and exit.
  ```
  ***Note***: 
  - This component only supports devices with model 0xac (air conditioner) and words `supported` in the output. 
  - Configure v3 devices need `token` and `k1`.
  - You `midea-discover`  when broadcasts don't work.
  - `midea-discover` use a registered account of `MSmartHome` [[AppStore]](https://apps.apple.com/sg/app/midea-home/id1254346490) [[GooglePlay]](https://play.google.com/store/apps/details?id=com.midea.ai.overseas) to get Token and K1(key).
  it's my account, but now it’s an open account.
  If you just only get Token and K1(key) with this account, I and others can't get your information through this account.
  Don't use this account to login to the APP and add device, this may reveal your information. Of course, you can use your own account，this is also the way I recommend.
    ```zsh
    midea-discover -a YOUR_ACCOUNT -p YOUR_PASSWORD
    ```

## Buy me a cup of coffee

- [via Paypal](https://www.paypal.me/himaczhou)
- [via Bitcoin](bitcoin:3GAvud4ZcppF5xeTPEqF9FcX2buvTsi2Hy) (**3GAvud4ZcppF5xeTPEqF9FcX2buvTsi2Hy**)
- [via AliPay(支付宝)](https://i.loli.net/2020/05/08/nNSTAPUGDgX2sBe.png)
- [via WeChatPay(微信)](https://i.loli.net/2020/05/08/ouj6SdnVirDzRw9.jpg)

Your donation will make me work better for this project.
