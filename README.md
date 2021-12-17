# quick-configs
My preference of config files

## Throw it in a `bash`

Caveats:

- You should read this command to make sure it's not malicious
- The `LICENSE.md` created credits my name, change it to yours
- The command sets up a SvelteKit project
- The command will install `adapter-netlify`
- "X could have been done more efficiently with the foo command" it doesn't matter

```sh
npm init svelte@next ;\
git init ;\
nvm use node ;\
node -v > .nvmrc ;\
rm tsconfig.json ;\
echo -e "{\n  \"compilerOptions\": {\n    \"alwaysStrict\": true,\n    \"allowJs\": true,\n    \"allowSyntheticDefaultImports\": true,\n    \"baseUrl\": \".\",\n    \"declaration\": true,\n    \"checkJs\": true,\n    \"esModuleInterop\": true,\n    \"forceConsistentCasingInFileNames\": true,\n    \"generateCpuProfile\": \"profile.cpuprofile\",\n    \"importsNotUsedAsValues\": \"error\",\n    \"isolatedModules\": true,\n    \"lib\": [\"ESNext\", \"DOM\"],\n    \"moduleResolution\": \"node\",\n    \"module\": \"ESNext\",\n    \"noImplicitAny\": true,\n    \"noUnusedLocals\": true,\n    \"noUnusedParameters\": true,\n    \"pretty\": true,\n    \"paths\": {\n      \"$lib\": [\"src/lib\"],\n      \"$lib/*\": [\"src/lib/*\"]\n    },\n    \"removeComments\": false,\n    \"resolveJsonModule\": true,\n    \"skipLibCheck\": true,\n    \"sourceMap\": true,\n    \"strictBindCallApply\": true,\n    \"strictFunctionTypes\": true,\n    \"target\": \"ES2017\"\n  },\n  \"include\": [\"src/**/*.d.ts\", \"src/**/*.js\", \"src/**/*.ts\", \"src/**/*.svelte\", \"src/**/*.svx\"]\n}\n" > tsconfig.json ;\
rm .prettierrc ;\
echo -e "{\n  \"arrowParens\": \"always\",\n  \"bracketSpacing\": true,\n  \"cursorOffset\": -1,\n  \"embeddedLanguageFormatting\": \"auto\",\n  \"endOfLine\": \"lf\",\n  \"filepath\": \"\",\n  \"htmlWhitespaceSensitivity\": \"css\",\n  \"insertPragma\": false,\n  \"jsxSingleQuote\": true,\n  \"printWidth\": 100,\n  \"proseWrap\": \"preserve\",\n  \"quoteProps\": \"as-needed\",\n  \"requirePragma\": false,\n  \"semi\": true,\n  \"singleQuote\": false,\n  \"trailingComma\": \"all\",\n  \"tabWidth\": 2,\n  \"useTabs\": false,\n  \"svelteAllowShorthand\": true,\n  \"svelteBracketNewLine\": true,\n  \"svelteIndentScriptAndStyle\": true,\n  \"svelteStrictMode\": false,\n  \"svelteSortOrder\": \"options-scripts-markup-styles\"\n}" > .prettierrc ;\
rm LICENSE.md ;\
echo -e "MIT License Copyright (c) 2021 Will Johnson\n\nPermission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the \"Software\"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE." > LICENSE.md ;\
rm README.md ;\
touch README.md ;\
rm svelte.config.js ;\
echo "import preprocess from \"svelte-preprocess\";\nimport { mdsvex } from \"mdsvex\";\nimport netlify from \"@sveltejs/adapter-netlify\";\n\n/** @type {import('@sveltejs/kit').Config} */\nconst config = {\n  /** @type {import(\"svelte/types/compiler/interfaces\").CompileOptions} */\n  compilerOptions: {\n    css: false,\n    accessors: true,\n    dev: process.env.NODE_ENV !== \"production\",\n  },\n  preprocess: [preprocess(), mdsvex()],\n  extensions: [\".svelte\", \".svx\"],\n  kit: {\n    package: {\n      exports: (f) => /^([^\/]+)?\/?index\.ts$/.test(f),\n      files: (f) =>\n        !/^_|\/_|docs\.svx$|internals\.ts$|test\.ts$/.test(f) &&\n        /props\.d\.ts$|\.svelte$|types\.d\.ts$|index\.ts/.test(f),\n    },\n    adapter: netlify(),\n    files: {\n      assets: \"src/assets\",\n    },\n    target: \"body\",\n  },\n};\nexport default config;\n" > svelte.config.js ;\
mv static src/assets ;\
rm src/app.html ;\
echo "<!DOCTYPE html>\n<html lang="en">\n  <head>\n    <meta charset="utf-8" />\n    <meta name="description" content="" />\n    <link rel="icon" href="/favicon.png" />\n    <meta name="viewport" content="width=device-width, initial-scale=1" />\n    %svelte.head%\n  </head>\n  <body>\n    %svelte.body%\n  </body>\n</html>\n" > src/app.html ;\
rm .gitignore ;\
echo ".DS_Store\nnode_modules\n/build\n/.svelte-kit\n/package\n.env\n.env.*\n!.env.example\n.netlify" > .gitignore ;\
rm .prettierignore ;\
echo ".DS_Store\nnode_modules\n/build\n/.svelte-kit\n.env\n.env.*\n.*\n.netlify" > .prettierignore ;\
rm package.json ;\
echo "{\n  \"name\": \"hitomezashi\",\n  \"version\": \"0.0.1\",\n  \"scripts\": {\n    \"dev\": \"svelte-kit dev\",\n    \"build\": \"svelte-kit build\",\n    \"package\": \"svelte-kit package\",\n    \"preview\": \"svelte-kit preview\",\n    \"check\": \"svelte-check --tsconfig ./tsconfig.json\",\n    \"check:watch\": \"svelte-check --tsconfig ./tsconfig.json --watch\",\n    \"lint\": \"prettier --ignore-path .prettierignore --check --plugin-search-dir=. .\",\n    \"format\": \"prettier --ignore-path .prettierignore --write --plugin-search-dir=. .\"\n  },\n  \"devDependencies\": {\n    \"@sveltejs/adapter-auto\": \"next\",\n    \"@sveltejs/kit\": \"next\",\n    \"prettier\": \"^2.4.1\",\n    \"prettier-plugin-svelte\": \"^2.4.0\",\n    \"svelte\": \"^3.44.0\",\n    \"svelte-check\": \"^2.2.6\",\n    \"svelte-preprocess\": \"^4.9.4\",\n    \"tslib\": \"^2.3.1\",\n    \"typescript\": \"^4.4.3\"\n  },\n  \"type\": \"module\"\n}" > package.json ;\
npm i ;\
npm i -D mdsvex @sveltejs/adapter-netlify@next ;\
mkdir src/hooks ;\
echo "import type { Handle } from \"@sveltejs/kit\";\n\nexport const handle: Handle = async ({ request, resolve }) => await resolve(request);" > src/hooks/index.ts
```
