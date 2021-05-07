# HTML-CSS-Sass-Boilerplate

## Development
``` 
npm install
```
```
npm start
```

## Production
```
npm run build
```

## Tips
- If you need to add vendor css files to project, like icon-font style file, you must do the some changes, for example if you want to add `icon-font.css` to project you must do:

  1. Install concat as a dev dependency ( `npm install concat --save-dev` )
  2. Add below line to package.json scripts and add vendor css file(s) path:
      ```
      "concat:css": "concat -o css/style.concat.css <VENDOR CSS FILE(S) PATH> css/style.comp.css"
      ```
      in our example:
      ```
      "concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css"
      ```
  3. prefix `style.concat.css` file instead of `style.comp.css`, in our example `prefix:css` script should change to:
      ```
      "prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css"
      ``` 
  4. And finally add `concat:css` command to `build:css` script:
      ```
      "build:css": "npm-run-all compile:sass concat:css prefix:css compress:css"
      ```
      
- Default browsers list for prefixing, set to `last 10 versions` in `prefix:css` script, you can change it for your needs.
