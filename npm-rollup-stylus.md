# package.json

```
{
	"name": "projectname",
	"version": "1.0.0",
	"description": "description",
	"main": "./assets/scripts/main.js",
	"scripts": {
		"clear": "rm -r build/*",
		"build:js": "rollup -c",
		"watch:js": "rollup -c -w",
		"build:css": "stylus ./assets/styles/main.styl -o ./build/styles.css",
		"watch:css": "stylus -w ./assets/styles/main.styl -o ./build/styles.css",
		"build": "stylus ./assets/styles/main.styl -o ./build/styles.css && rollup -c",
		"watch": "parallelshell 'stylus -w ./assets/styles/main.styl -o ./build/styles.css' 'rollup -c -w'"
	},
	"repository": {
		"type": "git",
		"url": "git+ssh://git@gitlab.com/belo/xxxxxxx.git"
	},
	"author": "João Belo",
	"license": "ISC",
	"bugs": {
		"url": "https://gitlab.com/belo/xxxxxxx/issues"
	},
	"homepage": "https://gitlab.com/belo/xxxxxxx#README",
	"dependencies": {},
	"devDependencies": {
		"babel-core": "^6.26.0",
		"babel-plugin-external-helpers": "^6.22.0",
		"babel-preset-latest": "^6.24.1",
		"parallelshell": "^3.0.2",
		"rollup-plugin-babel": "^3.0.2",
		"rollup-plugin-commonjs": "^8.2.6",
		"rollup-plugin-eslint": "^4.0.0",
		"rollup-plugin-node-resolve": "^3.0.0"
	}
}

```



# .editorconfig

```
# EditorConfig helps developers define and maintain consistent
# coding styles between different editors and IDEs
# editorconfig.org

root = true

[*]

# Change these settings to your own preference
indent_style = tab
tab_width = 4


# We recommend you to keep these unchanged
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
```



# .eslintrc.json

```
{
    "env": {
        "browser": true,
        "es6": true
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "sourceType": "module"
    },
    "rules": {
        "indent": [
            "error",
            "tab"
        ],
        "linebreak-style": [
            "error",
            "unix"
        ],
        "quotes": [
            "error",
            "single"
        ],
        "semi": [
            "error",
            "always"
        ]
    }
}
```



# .jscsrc

```
{
  "validateIndentation": "\t"
}
```



# .jshintrc

``` 
{ "esversion":6 }
```



# rollup.config.js

```
import babel from 'rollup-plugin-babel';
import eslint from 'rollup-plugin-eslint';
import resolve from 'rollup-plugin-node-resolve';
import commonjs from 'rollup-plugin-commonjs';

export default {
	input: './assets/scripts/main.js',
	output: {
		file: './build/scripts.js',
		format: 'iife'
	},
	sourcemap: 'inline',
	plugins: [
		resolve({
			jsnext: true,
			main: true,
			browser: true
		}),
		commonjs(),
		eslint(),
		babel({
			exclude: 'node_modules/**'
		})
	]
};
```










