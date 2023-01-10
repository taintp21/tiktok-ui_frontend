# Thư viện đã cài đặt trong dự án

## normalize.css

Normalize.css là một tệp CSS nhỏ cung cấp tính chất nhất quán trên nhiều trình duyệt. Normalize CSS sẽ giúp cho các phần tử HTML có tính thống nhất với nhau hơn. Normalize CSS là công cụ hiện đại và rất phù hợp với HTML 5. Nó có thể thay thế hoàn toàn cho các thiết lập lại CSS truyền thống.

<ul>
    <li>GitHub: https://github.com/necolas/normalize.css</li>
    <li>Homepage: https://necolas.github.io/normalize.css</li>
</ul>

**Cài đặt:**

```bash
npm install --save normalize.css
```

## SASS

SASS (Syntactically Awesome StyleSheets) là một CSS Preprocessor hỗ trợ viết CSS nhanh hơn và có cấu trúc rõ ràng hơn.

<ul>
    <li>GitHub: https://github.com/sass/dart-sass</li>
    <li>Homepage: https://sass-lang.com/dart-sass</li>
</ul>

**Cài đặt:**

```bash
npm i sass --save-dev
```

## customize-cra & react-app-rewired & babel-plugin-module-resolver

Đơn giản hoá khi import, override lại settings đã có sẵn khi tạo dự án với create-react-app

<ul>
    <li>GitHub <code>customize-cra</code>: https://github.com/arackaf/customize-cra</li>
    <li>GitHub <code>react-app-rewired</code>: https://github.com/timarney/react-app-rewired</li>
    <li>GitHub <code>babel-plugin-module-resolver</code>: https://github.com/tleunen/babel-plugin-module-resolver</li>
</ul>

**Cài đặt:**

```bash
npm i customize-cra react-app-rewired --dev
```

```bash
npm i babel-plugin-module-resolver --save-dev
```

**Hướng dẫn**

#### 1) Điều chỉnh gọi scripts đã cho sẵn sang `react-scripts` trong `npm` scripts

```diff
  /* package.json */

  "scripts": {
-   "start": "react-scripts start",
+   "start": "react-app-rewired start",
-   "build": "react-scripts build",
+   "build": "react-app-rewired build",
-   "test": "react-scripts test",
+   "test": "react-app-rewired test",
    "eject": "react-scripts eject"
}
```

#### 2) Override configs mặc định của webpack

-   Tạo file `config-overrides.js` tại thư mục root:

```js
/* config-overrides.js */

const { override, useBabelRc } = require('customize-cra');

module.exports = override(
    // eslint-disable-next-line react-hooks/rules-of-hooks
    useBabelRc(),
);
```

-   Docs: https://github.com/arackaf/customize-cra/blob/master/api.md

#### 3) Custom alias, đơn giản hoá trong việc import

-   Tạo file `.babelrc` tại thư mục root:

```js
{
    "plugins": [
        [
            "module-resolver",
            {
                "alias": {
                    "~": "./src"
                }
            }
        ]
    ]
}
```

# Chỉnh sửa trong VS Code

## Custom

-   Tạo file `jsconfig.json` tại thư mục root:

```js
{
    "compilerOptions": {
        "baseUrl": ".",
        "paths": {
            "~/*": [
                "src/*"
            ]
        }
    }
}
```

-   Tạo thư mục/file `.vscode/settings.json` tại thư mục root:

```js
{
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

## Prettier Extension

-   GitHub: https://github.com/prettier/prettier
-   Homepage: https://prettier.io/docs/en
    Cài đặt Prettier. Tạo file `.prettierrc` tại thư mục root:

```js
{
    "tabWidth": 4,
    "printWidth": 120,
    "semi": true,
    "singleQuote": true,
    "quoteProps": "as-needed",
    "jsxSingleQuote": true,
    "trailingComma": "all",
    "bracketSpacing": true,
    "arrowParens": "always",
    "proseWrap": "preserve",
    "htmlWhitespaceSensitivity": "css",
    "embeddedLanguageFormatting": "auto"
}
```
