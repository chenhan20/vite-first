# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

### 部屬github網頁須注意

### vite.config.js defineConfig須設定靜態專案的網址 官方說這樣做 但感覺有點鳥蛋==


```json
 base: '/vite-first'
 
 //新方法 執行這兩行 就會把build的推到gh-pages 不用再開一個專案 用同一個就可以了
 npm run build
 git add dist
 git commit -m 'update gh-pages'
 git subtree push --prefix dist origin gh-pages
 

```

### 參考資料
(Github靜態頁面設定) [https://gist.github.com/sunjc826/3ab0cb60be87935a0809b66e57bf9d79]