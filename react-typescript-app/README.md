# react-typescript-app
React/Typescript starter app.

Steps taken to create this starter app:
1. Create a directory for app, `md <your app name>` and clone this folder.
2. Run npm install
3. Install typescript globally and link it `npm install -g typescript`, then `npm link typescritpt`
4. The tsconfig.json file contains the object below. Adding the jsx line, is similar to `tsc-jsx react` command  Webpack will be configured to handle include entry file. Use "es5" for target, if you need this app to work in IE.
   ```json
   {
      "compilerOpions": {
         "target": "es5", 
         "jsx": "react",
         "module": "commonjs"
      },
      "exclude": [
         "node_modules"
      ]
   }
   ```
5. Install webpack and the ts-loader plugin, which is the typescript loader for webpack.
   `npm install webpack ts-loader`
6. Install webpack-cli as dev. dependency
   `npm install webpack-cli --save-dev`
8. The webpack.config.js code is explained very well on Ogundipe Samuel's <a href="https://blog.logrocket.com/how-why-a-guide-to-using-typescript-with-react-fffb76c61614">LogRocket</a> site. But as an overview, this file configures the entry file, what output path and filename should be used, extensions to look for and loaders to use for which file extensions. I included watch and set it to true, so that any changes made are automatically recompiled, but you can remove or set this to false if you don't want to watch for changes. Also, if you already have react and react-dom saved in your environment and don't want them included in the bundle, for example with SharePoint development, include the externals object and reference them in the index.html file. (/\.tsx?$/ means all files that end with .ts or .tsx) 
   ```javascript
   var path = require("path");
   var config = {
     entry: ["./app.tsx"],
     output: {
       path: path.resolve(__dirname, "build"),
       filename: "bundle.js"
     },  
     resolve: {
       extensions: [".ts", ".tsx", ".js"]
     },
     watch: true,
     externals: {
        "react": "React",
        "react-dom": "ReactDOM"
    },
     module: {
       rules: [
          {
             test: /\.tsx?$/,
             loader: "ts-loader",
             exclude: /node_modules/
         }
       ]
     }     
   };
   
   module.exports = config;
   ```
  7) Install react and react-dom and type definitions for each library. The type definitions are used to describe react and react-dom types to the TypeScript compiler.
  ```
  npm install react react-dom @types/react @types/react-dom
  ```
  8) Entry .html and .tsx (index.html and app.tsx)
  9) Component files (HeaderComponent.tsx, BodyComponent.tsx, FooterComponent.tsx)
  10) Interface file (IFooter.ts)
  
  
