<div align="center">

<img src="https://files.catbox.moe/zcl82b.jpg" alt="WhatsApp Baileys Badzz" width="100%" style="border-radius: 16px;" />

<br/>
<br/>

# \u2726 WhatsApp Baileys Edgar \u2726

<p>
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" />
  <img src="https://img.shields.io/badge/WebSocket-010101?style=for-the-badge&logo=socketdotio&logoColor=white" />
  <img src="https://img.shields.io/badge/Open%20Source-FF4500?style=for-the-badge&logo=github&logoColor=white" />
</p>

<p>
  <img src="https://img.shields.io/github/stars/badzzne2/baileys?style=flat-square&color=FFD700&label=\u2b50 Stars" />
  <img src="https://img.shields.io/github/forks/badzzne2/baileys?style=flat-square&color=25D366&label=\ud83c\udf74 Forks" />
  <img src="https://img.shields.io/github/issues/badzzne2/baileys?style=flat-square&color=FF6B6B&label=\ud83d\udc1b Issues" />
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" />
</p>

> **Open-source WhatsApp automation library** \u2014 no browser required.  
> Built on WebSocket for speed, stability, and full multi-device support.

<br/>

[\ud83d\udce6 Installation](#-getting-started) \u2022 [\ud83d\udcd6 Documentation](#-sendmessage-documentation) \u2022 [\u2728 Features](#-main-features) \u2022 [\ud83d\udcac Telegram](https://t.me/badzzne2)

</div>

---

## \ud83c\udf1f What is Baileys Badzz?

**WhatsApp Baileys Badzz** is a powerful, open-source library built for developers who need reliable WhatsApp automation \u2014 without the overhead of a browser. Powered by **WebSocket technology**, it supports message management, group administration, interactive messages, and action buttons, all in a lightweight and modular package.

Actively maintained with continuous improvements to **pairing stability**, **session management**, and **WhatsApp multi-device compatibility**.

Perfect for:
- \ud83e\udd16 Business bots & chat automation
- \ud83c\udfa7 Customer service systems
- \ud83d\udce3 Broadcast & notification tools
- \ud83d\uded2 E-commerce integrations

---

## \u2728 Main Features

| Feature | Description |
|---|---|
| \ud83d\udd17 **Custom Pairing** | Stable pairing with your own codes \u2014 no disconnection issues |
| \ud83d\udcac **Interactive Messages** | Buttons, menus, native flows, and more |
| \ud83d\udce6 **Session Management** | Automatic, efficient, and long-term stable |
| \ud83d\udcf1 **Multi-Device Support** | Fully compatible with WhatsApp's latest multi-device API |
| \u26a1 **Lightweight & Modular** | Easy to integrate into any Node.js project |
| \ud83d\udcc4 **Rich Documentation** | Comprehensive guides and example code included |
| \ud83d\udd12 **Secure Auth** | Improved authentication flow with fixed prior vulnerabilities |

---

## \ud83d\udce6 Getting Started

Install via npm or yarn:

```bash
npm install @whiskeysockets/baileys
# or
yarn add @whiskeysockets/baileys
```

Then import and initialize:

```javascript
const { makeWASocket, useMultiFileAuthState } = require("@whiskeysockets/baileys");

const { state, saveCreds } = await useMultiFileAuthState("auth_info");
const sock = makeWASocket({ auth: state });

sock.ev.on("creds.update", saveCreds);
```

---

## \ud83d\udd27 Additional Functions

### \ud83d\udce1 Get Channel ID
```javascript
await sock.newsletterId(url);
```

### \ud83d\udeab Check Banned Number
```javascript
await sock.checkWhatsApp(target);
```

---

## \ud83d\udcd6 SendMessage Documentation

<details>
<summary><b>\ud83d\udce2 Group Status Message (V2)</b></summary>

```javascript
await sock.sendMessage(target, {
    groupStatusMessage: {
        text: "Hello World"
    }
});
```
</details>

<details>
<summary><b>\ud83d\uddbc\ufe0f Album Message (Multiple Images)</b></summary>

```javascript
await sock.sendMessage(target, {
    albumMessage: [
        { image: cihuy, caption: "First photo" },
        { image: { url: "IMAGE_URL" }, caption: "Second photo" }
    ]
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83d\udcc5 Event Message</b></summary>

```javascript
await sock.sendMessage(target, {
    eventMessage: {
        isCanceled: false,
        name: "Event Name",
        description: "Event description here",
        location: {
            degreesLatitude: 0,
            degreesLongitude: 0,
            name: "Location Name"
        },
        joinLink: "https://call.whatsapp.com/video/example",
        startTime: "1763019000",
        endTime: "1763026200",
        extraGuestsAllowed: false
    }
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83d\udcca Poll Result Message</b></summary>

```javascript
await sock.sendMessage(target, {
    pollResultMessage: {
        name: "Poll Title",
        pollVotes: [
            { optionName: "Option A", optionVoteCount: "112233" },
            { optionName: "Option B", optionVoteCount: "1" }
        ]
    }
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83d\udd18 Simple Interactive Message</b></summary>

```javascript
await sock.sendMessage(target, {
    interactiveMessage: {
        header: "Hello World",
        title: "Hello World",
        footer: "telegram: @badzzne2",
        buttons: [
            {
                name: "cta_copy",
                buttonParamsJson: JSON.stringify({
                    display_text: "Copy Code",
                    id: "123456789",
                    copy_code: "ABC123XYZ"
                })
            }
        ]
    }
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83c\udf0a Interactive Message with Native Flow</b></summary>

```javascript
await sock.sendMessage(target, {
    interactiveMessage: {
        header: "Hello World",
        title: "Hello World",
        footer: "telegram: @badzzne2",
        image: { url: "https://example.com/image.jpg" },
        nativeFlowMessage: {
            messageParamsJson: JSON.stringify({
                limited_time_offer: {
                    text: "Limited offer text",
                    url: "https://t.me/badzzne2",
                    copy_code: "PROMO2024",
                    expiration_time: Date.now() * 999
                },
                bottom_sheet: {
                    in_thread_buttons_limit: 2,
                    divider_indices: [1, 2, 3, 4, 5, 999],
                    list_title: "List Title",
                    button_title: "Button Title"
                },
                tap_target_configuration: {
                    title: "Title",
                    description: "Description text",
                    canonical_url: "https://t.me/badzzne2",
                    domain: "shop.example.com",
                    button_index: 0
                }
            }),
            buttons: [
                {
                    name: "single_select",
                    buttonParamsJson: JSON.stringify({ has_multiple_buttons: true })
                },
                {
                    name: "call_permission_request",
                    buttonParamsJson: JSON.stringify({ has_multiple_buttons: true })
                },
                {
                    name: "single_select",
                    buttonParamsJson: JSON.stringify({
                        title: "Select an Option",
                        sections: [
                            {
                                title: "Section Title",
                                highlight_label: "Label",
                                rows: [
                                    {
                                        title: "Row Title",
                                        description: "Row description",
                                        id: "row_1"
                                    }
                                ]
                            }
                        ],
                        has_multiple_buttons: true
                    })
                },
                {
                    name: "cta_copy",
                    buttonParamsJson: JSON.stringify({
                        display_text: "Copy Code",
                        id: "123456789",
                        copy_code: "ABC123XYZ"
                    })
                }
            ]
        }
    }
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83d\uddbc\ufe0f Interactive Message with Thumbnail</b></summary>

```javascript
await sock.sendMessage(target, {
    interactiveMessage: {
        header: "Hello World",
        title: "Hello World",
        footer: "telegram: @badzzne2",
        image: { url: "https://example.com/image.jpg" },
        buttons: [
            {
                name: "cta_copy",
                buttonParamsJson: JSON.stringify({
                    display_text: "Copy Code",
                    id: "123456789",
                    copy_code: "ABC123XYZ"
                })
            }
        ]
    }
}, { quoted: m });
```
</details>

<details>
<summary><b>\ud83d\uded2 Product Message</b></summary>

```javascript
await sock.sendMessage(target, {
    productMessage: {
        title: "Sample Product",
        description: "This is the product description.",
        thumbnail: { url: "https://example.com/image.jpg" },
        productId: "PROD001",
        retailerId: "RETAIL001",
        url: "https://example.com/product",
        body: "Product details",
        footer: "Special price",
        priceAmount1000: 50000,
        currencyCode: "USD",
        buttons: [
            {
                name: "cta_url",
                buttonParamsJson
