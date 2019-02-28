# Visual Studio Code


## Type

[FiraCode-Retina](https://github.com/tonsky/FiraCode/blob/master/distr/ttf/FiraCode-Retina.ttf)


## Extensions

ESLint - Dirk Baeumer

ES7 React/Redux/GraphQL/React-Native snippets - dsznajder

React Native Tools - Visual Studio Mobile Tools

Vetur - Pine Wu

language stylus - sysoev

Cucumber (Gherkin) Full Support - Alexander Krechik

GitLens — Git supercharged (eamodio.gitlens) - Eric Amodio

VS Live Share - Microsoft

Debugger for Chrome (msjsdiag.debugger-for-chrome) - Microsoft

Docker (peterjausovec.vscode-docker) - Microsoft


## User Settings

```
{
    "languageStylus.useSeparator": false,
    "window.zoomLevel": 0,
    "workbench.startupEditor": "newUntitledFile",
    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "scope": [
                    "comment",
                    "entity.name.type.class",
                    "keyword",
                    "constant",
                    "storage.modifier",
                    "constant.numeric.css",
                    "storage.type.class.js"
                ],
                "settings": {
                        "fontStyle": "italic",
                    }
            },
            {
                "scope": [
                    "invalid",
                    "keyword.operator",
                    "keyword.other.unit.px.css",
                    "constant.numeric.decimal.js",
                    "constant.numeric.json"
                ],
                "settings": {
                    "fontStyle": "",
                }
            }
        ]
    },
    "editor.fontFamily": "Fira Code",
    "editor.fontLigatures": true,
    "editor.fontSize": 14,
    "editor.tabSize": 2,
    "editor.detectIndentation": false,
    "gitlens.advanced.messages": {
        "suppressShowKeyBindingsNotice": true
    },
    "gitlens.defaultDateStyle": "absolute",
    "gitlens.defaultDateFormat": "YYYY-MM-DD, HH:mm:ss",
    "emmet.includeLanguages": {
        "javascript": "javascriptreact"
    },
    "emmet.triggerExpansionOnTab": true,
    "eslint.packageManager": "yarn"
}

```
