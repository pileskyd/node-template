# Project

## Lint and fmt

> VS Code

Для автоматического выполнения линтинга и форматирования при сохранении кода в VSCode, выполните следующие шаги:

1. **Установите необходимые расширения для VSCode**:

   - **ESLint**: Это расширение добавляет поддержку ESLint в редактор VSCode.
   - **Prettier - Code formatter**: Это расширение позволяет автоматически форматировать код при сохранении.

   Чтобы установить эти расширения, откройте VSCode и перейдите в раздел "Extensions" (расширения), затем найдите и установите "ESLint" и "Prettier - Code formatter".

2. **Настройте VSCode для автоматического выполнения линтинга и форматирования**:

   Откройте настройки VSCode и добавьте следующие конфигурации:

   - Откройте командную палитру (Ctrl+Shift+P или Cmd+Shift+P на macOS) и выберите "Preferences: Open Settings (JSON)".
   - Добавьте следующие настройки:

     ```json
     {
       "editor.formatOnSave": true,
       "editor.codeActionsOnSave": {
         "source.fixAll": true
       },
       "eslint.validate": [
         "javascript",
         "javascriptreact",
         "typescript",
         "typescriptreact"
       ],
       "prettier.requireConfig": true
     }
     ```

     Эти настройки делают следующее:
     - `"editor.formatOnSave": true` включает автоматическое форматирование при сохранении файла.
     - `"editor.codeActionsOnSave": { "source.fixAll": true }` включает автоматическое исправление всех ошибок линтинга при сохранении файла.
     - `"eslint.validate"` определяет, какие языки будут проверяться с помощью ESLint.
     - `"prettier.requireConfig": true` указывает Prettier использовать только те файлы, для которых имеется конфигурационный файл.

3. **Настройте проект для использования локально установленных пакетов ESLint и Prettier**:

   В корне вашего проекта создайте или обновите файл `.vscode/settings.json` с следующими настройками:

   ```json
   {
     "eslint.packageManager": "npm",
     "eslint.nodePath": "node_modules",
     "prettier.prettierPath": "./node_modules/prettier",
     "eslint.options": {
       "extensions": [".js", ".ts"]
     }
   }
   ```

   Эти настройки указывают VSCode использовать локальные установки ESLint и Prettier, что обеспечивает единообразие в разных окружениях разработчиков.

Теперь при сохранении файлов в VSCode будет автоматически запускаться линтинг и форматирование кода в соответствии с вашими настройками ESLint и Prettier.

> JetBrains IDEs

Для настройки автоматического выполнения линтинга и форматирования кода при сохранении в редакторах JetBrains (например, WebStorm, IntelliJ IDEA) выполните следующие шаги:

### 1. Установите необходимые плагины

Для JetBrains существует поддержка плагинов ESLint и Prettier:

- **ESLint**: Плагин для интеграции ESLint.
- **Prettier**: Плагин для интеграции Prettier.

Обычно эти плагины предустановлены в WebStorm и других редакторах JetBrains, но если их нет, установите их через меню `File > Settings > Plugins`.

### 2. Настройте ESLint

1. **Включите поддержку ESLint**:
   - Откройте `File > Settings > Languages & Frameworks > JavaScript > Code Quality Tools > ESLint`.
   - Включите опцию `Enable`.
   - Убедитесь, что выбран параметр `Automatic ESLint configuration` или укажите путь к конфигурационному файлу `.eslintrc.json`.

2. **Укажите путь к ESLint**:
   - Если вы используете локально установленный ESLint, укажите путь к вашему локальному ESLint (например, `node_modules/eslint`).

### 3. Настройте Prettier

1. **Включите поддержку Prettier**:
   - Откройте `File > Settings > Languages & Frameworks > JavaScript > Prettier`.
   - Включите опцию `On code reformat` и `On save`.
   - Убедитесь, что выбран параметр `Automatic Prettier configuration` или укажите путь к конфигурационному файлу `.prettierrc.json`.

2. **Укажите путь к Prettier**:
   - Если вы используете локально установленный Prettier, укажите путь к вашему локальному Prettier (например, `node_modules/prettier`).

### 4. Настройка автоматического форматирования при сохранении

Для автоматического форматирования и линтинга при сохранении:

1. **Автоматическое форматирование с помощью Prettier**:
   - Откройте `File > Settings > Tools > Actions on Save`.
   - Включите опцию `Reformat code` и убедитесь, что Prettier выбран как форматтер.

2. **Автоматическое исправление проблем с помощью ESLint**:
   - В том же разделе `Actions on Save`, включите опцию `Run eslint --fix` для запуска ESLint с автоматическим исправлением ошибок при сохранении.
