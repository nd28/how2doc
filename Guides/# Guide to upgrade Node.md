# Guide to upgrade Node.js 20

#### Step 1
Install Node.js version 20.10.0 (Long Term Support (LTS) release)

#### Step 2
Use "npm" as the project package manager, which comes with Node.js

#### Step 3
Fix any of the dependency vulnerabilities by the running this command:
`npm audit fix`
- this step automatically updates react-scripts (and webpack to version 5) and other dependencies
- if this doesn't work use `--force` flag
`npm audit fix --force`

#### Step 4
Use `craco` to add node pollyfill.
> node polyfill is set of packages/functions that you need to use in browser but isn't available in browser.

- Install `craco` by running this command: `npm install -D @craco/craco`
- Create config file named `craco.config.js` (read more from official website of `cracojs`)
- Install `node-pollyfill-webpack-plugin`. and add the plugin to config file.
```js
var NodePollyfill = require('node-pollyfill-webpack-plugin')
module.exports = {
    webpack:{
        plugins:[new NodePollyfill()]
    }
}
```

#### Step 5
Modify scripts in `package.json` file. Replace `react-scripts` with `craco`
- `react-scripts start` -> `craco start`
- `react-scripts build` -> `craco build`
- `react-scripts test` -> `craco test`

#### Step 6
If using `dotenv` as dependency, you will need to remove it from the dependency
> As it is no longer need to install explicitly, it comes with the Node.js

#### Step 7
Try running the following commands to see if everything works as expeceted.
- `npm run start` -> start dev server 
- `npm run build` -> create production bundle. 

#### Step 8
Test the application flow, and fix any runtime error


# Tech stack of our LOS Application