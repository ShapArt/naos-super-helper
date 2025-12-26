## NAOS Super Helper — как вынести в отдельный репозиторий

Этот скрипт лучше хранить в отдельном публичном/приватном репозитории, чтобы проще выпускать версии и обновлять через `@updateURL`. Ниже — минимальный чек‑лист.

### Структура репозитория
- `NAOS Super Helper.js` — единственный артефакт, готовый к установке в Tampermonkey.
- `README.md` — что делает скрипт, как ставить и обновлять, требования (Tampermonkey, backend.naos.ru).
- `CHANGELOG.md` — краткие записи по версиям (синхронизировать с `@version` в мета‑блоке).
- `docs/` — гайды и скриншоты (опционально).

### Создание репо
1. Создай новый репозиторий на GitHub, например `naos-super-helper` (без лишних файлов).
2. Локально:
   ```bash
   git clone <ssh-or-https-url>
   cd naos-super-helper
   cp ../Script/NAOS\ Super\ Helper.js .
   echo "# NAOS Super Helper" > README.md
   git add .
   git commit -m "feat: initial release v2.1.0"
   git push origin main
   ```
3. В `NAOS Super Helper.js` не забывай обновлять `@version`, `@updateURL`, `@downloadURL` на сырой линк репозитория (raw GitHub).

### Релизы и обновления
- Перед пушем: обнови `@version` и Changelog.
- Тег: `git tag v2.1.0 && git push origin v2.1.0`.
- Тампер: пользователи получают автообновление по `@updateURL`/`@downloadURL`.

### Полезные политики
- Без секретов в коде и истории (проверяй `git status` и `git diff`).
- Кодировка UTF‑8, конца строк LF.
- Формат: один файл, без сборки/зависимостей, чтобы обновления были мгновенными.

Этого достаточно, чтобы держать скрипт в отдельном, «чистом» репозитории и выпускать версии по всем правилам. 
