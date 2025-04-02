# tdata-converter 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
<!-- Добавьте другие значки по необходимости: статус сборки, версия и т.д. -->
<!-- [![Build Status](https://travis-ci.org/ВАШ-USERNAME/tdata-converter.svg?branch=main)](https://travis-ci.org/ВАШ-USERNAME/tdata-converter) -->
<!-- [![PyPI version](https://badge.fury.io/py/tdata-converter.svg)](https://badge.fury.io/py/tdata-converter) -->

Простая утилита для конвертации сессий Telegram Desktop (`tdata`) в форматы сессий, совместимые с библиотеками **Telethon** и **Pyrogram** (`.session`).

Это позволяет вам использовать существующую активную сессию из десктопного клиента Telegram для ваших скриптов или ботов на Python, без необходимости повторной авторизации через код или QR-код.

## ✨ Возможности

*   Конвертация папки `tdata` Telegram Desktop в файл сессии `.session`.
*   Поддержка сессий для [Telethon](https://github.com/LonamiWebs/Telethon).
*   (Опционально) Поддержка сессий для [Pyrogram](https://github.com/pyrogram/pyrogram).
*   Простой интерфейс командной строки.
*   Кроссплатформенность (Windows, macOS, Linux).

## ⚠️ Важное Предупреждение

*   **Безопасность**: Папка `tdata` содержит ваши **личные ключи авторизации**. Никогда **не делитесь** этой папкой или сгенерированными файлами `.session` с кем-либо. Используйте эту утилиту только для собственных нужд и на свой страх и риск.
*   **Изменения в Telegram**: Формат `tdata` может измениться с обновлениями Telegram Desktop, что может потребовать обновления этого конвертера.
*   **Риск блокировки**: Использование пользовательских аккаунтов для автоматизации может нарушать Условия Обслуживания Telegram и привести к блокировке аккаунта. Используйте ответственно.

## ⚙️ Требования

*   **Python** 3.7+
*   Установленные зависимости (см. `requirements.txt`)
*   Доступ к папке `tdata` вашего Telegram Desktop.

## 💾 Установка

1.  **Клонируйте репозиторий:**
    ```bash
    git clone https://github.com/ВАШ-USERNAME/tdata-converter.git
    cd tdata-converter
    ```
2.  **Установите зависимости:**
    ```bash
    pip install -r requirements.txt
    # Или: python -m pip install -r requirements.txt
    ```

## 🚀 Использование

1.  **Найдите папку `tdata`:**
    *   **Windows:** `%APPDATA%\Telegram Desktop\tdata`
    *   **macOS:** `~/Library/Application Support/Telegram Desktop/tdata`
    *   **Linux:** `~/.local/share/TelegramDesktop/tdata`
    *   *(Пути могут незначительно отличаться в зависимости от версии или способа установки Telegram)*

2.  **Запустите конвертер:**
    Откройте терминал или командную строку в папке с клонированным репозиторием и выполните:

    ```bash
    python converter.py --tdata /путь/к/вашей/папке/tdata --output my_telegram_session.session
    ```
    *   Замените `/путь/к/вашей/папке/tdata` на реальный путь к вашей папке `tdata`.
    *   Замените `my_telegram_session.session` на желаемое имя выходного файла сессии.
    *   (Опционально) Добавьте флаги, если ваша утилита поддерживает разные форматы вывода или другие опции (например, `--pyrogram` или `--telethon`). Пример:
        ```bash
        # Если есть явный выбор формата
        python converter.py --tdata C:\Users\User\AppData\Roaming\Telegram Desktop\tdata --output my_telethon.session --telethon
        # Или
        python converter.py --tdata ~/.local/share/TelegramDesktop/tdata --output my_pyrogram.session --pyrogram
        ```

3.  **Используйте файл `.session`:**
    Сгенерированный файл `my_telegram_session.session` теперь можно использовать с Telethon или Pyrogram. Обычно его нужно поместить в ту же директорию, где запускается ваш Python-скрипт, или указать путь к нему при инициализации клиента.

    **Пример для Telethon:**
    ```python
    from telethon.sync import TelegramClient

    api_id = 123456 # Ваш API ID
    api_hash = 'YOUR_API_HASH' # Ваш API Hash

    # Клиент будет использовать существующий файл 'my_telegram_session.session'
    client = TelegramClient('my_telegram_session', api_id, api_hash)

    async def main():
        await client.connect()
        if await client.is_user_authorized():
            print("Успешно вошли с использованием сессии!")
            me = await client.get_me()
            print(me.first_name)
        else:
            print("Не удалось войти. Сессия может быть недействительной.")
        await client.disconnect()

    with client:
        client.loop.run_until_complete(main())
    ```

## 🤝 Участие в разработке (Contributing)

Мы приветствуем любой вклад! Если вы хотите улучшить `tdata-converter`:

1.  Сделайте форк репозитория (`Fork`).
2.  Создайте новую ветку (`git checkout -b feature/ваша-фича`).
3.  Внесите свои изменения и сделайте коммит (`git commit -am 'Добавлена новая фича'`).
4.  Отправьте изменения в свой форк (`git push origin feature/ваша-фича`).
5.  Создайте Pull Request.

Пожалуйста, сообщайте об ошибках и предлагайте улучшения через раздел [Issues](https://github.com/ВАШ-USERNAME/tdata-converter/issues).

## 📜 Лицензия

Этот проект лицензирован под лицензией MIT - см. файл [LICENSE](LICENSE) для подробностей.

---

*Используйте с осторожностью и уважением к условиям использования Telegram.*
