# Настройки для VSCode
- Нажать комбинацию клавишь `CTRL+SHIFT+P`
- Ввести `>settings.json`
- Открыть файл `settings.json`
- Вставить настройки показаные ниже в файл `settings.json` вашей IDE
```rb
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "editor.codeLens": 2,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "terminal.integrated.defaultProfile.windows": "PowerShell",
  "editor.fontLigatures": false,
  "[vue]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "files.autoSave": "afterDelay",
  "diffEditor.ignoreTrimWhitespace": false,
  "window.zoomLevel": -1,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "vue",
  ],
  "[jsonc]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  }
}
```

# Добавление eslint в проект Vue
**`ОБЯЗАТЕЛЬНО УСТАНОВИТЬ ПЛАГИН ESLINT ОТ Microsoft!!!`**

### Установка зависимостей

### JS
- `npm install --save-dev eslint eslint-plugin-vue`

### TS
- `npm install --save-dev eslint eslint-plugin-vue @vue/eslint-config-typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin`

Создаем файл в корневой директории проекта с название:
- `.eslintrc.js`

Добавляем в него следующий код:

### TS

```rb
// eslint-disable-next-line no-undef
module.exports = {
  extends: [
    'plugin:vue/recommended',
    'eslint:recommended',
    '@vue/typescript/recommended'
  ],
  parserOptions: {
    parser: '@typescript-eslint/parser'
  },
  rules: {
    semi: ['error', 'never'],
    "vue/html-self-closing": "off",
    'vue/no-multiple-template-root': 'off'
  }
}
```

### JS

```rb
module.exports = {
  extends: [
    'plugin:vue/recommended',
    'eslint:recommended',
  ],
  rules: {
    semi: ['error', 'never'],
    "vue/html-self-closing": "off",
    'vue/no-multiple-template-root': 'off'
  }
}
```



# Добавляем alias
Файл vite.config должен выглядеть так
```rb
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import { resolve } from 'path'

export default defineConfig({
  resolve: {
    alias: {
      '@': resolve(__dirname, 'src')
    }
  },
  plugins: [vue()]
})
```