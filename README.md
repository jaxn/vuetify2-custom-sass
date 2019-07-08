# Vuetify 2 with Sass

Currently demonstrates error caused by including `lang="scss"` in a Single File Component.

If you run `yarn serve` you will get the following error:

```
$ vue-cli-service serve
 INFO  Starting development server...
 ERROR  Failed to compile with 1 errors12:38:27 PM

 error  in ./src/components/ScssComponent.vue?vue&type=style&index=0&lang=scss&

Module build failed (from ./node_modules/sass-loader/lib/loader.js):

<template>
                          ^
      Expected ";".
  ╷
1 │ @import "~@/sass/main.scss"
  │                            ^
  ╵
  stdin 1:28  root stylesheet
      in /home/jackson/Code/vuetify-theme/src/components/ScssComponent.vue (line 1, column 28)

 @ ./node_modules/vue-style-loader??ref--8-oneOf-1-0!./node_modules/css-loader??ref--8-oneOf-1-1!./node_modules/vue-loader/lib/loaders/stylePostLoader.js!./node_modules/postcss-loader/src??ref--8-oneOf-1-2!./node_modules/sass-loader/lib/loader.js??ref--8-oneOf-1-3!./node_modules/vuetify-loader/lib/loader.js!./node_modules/cache-loader/dist/cjs.js??ref--0-0!./node_modules/vue-loader/lib??vue-loader-options!./src/components/ScssComponent.vue?vue&type=style&index=0&lang=scss& 4:14-491 14:3-18:5 15:22-499
 @ ./src/components/ScssComponent.vue?vue&type=style&index=0&lang=scss&
 @ ./src/components/ScssComponent.vue
 @ ./node_modules/cache-loader/dist/cjs.js??ref--12-0!./node_modules/babel-loader/lib!./node_modules/vuetify-loader/lib/loader.js!./node_modules/cache-loader/dist/cjs.js??ref--0-0!./node_modules/vue-loader/lib??vue-loader-options!./src/App.vue?vue&type=script&lang=js&
 @ ./src/App.vue?vue&type=script&lang=js&
 @ ./src/App.vue
 @ ./src/main.js
 @ multi (webpack)-dev-server/client?http://localhost:8081/sockjs-node (webpack)/hot/dev-server.js ./src/main.js
```

## Attempted workarounds

-  Adding a semicolon to the import in `vue.config.js` results in an error about indentation.
-  Converting the `style` block in `ScssComponent` to Sass syntax "works", but wrong for the future