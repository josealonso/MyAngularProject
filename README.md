# MiPrimeraApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.4.3.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.
du dist/ -h
Antes ------> 4.8M    dist/
Después ----> 324K    dist/

Para probarlo en tu navegado --->
ng build --prod --base-href="misitio"

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

---------------------------------------------------
Mi primera aplicación en Angular
Versiones: node 8.4.0   Typescript: 2.3.3   Angular: 4.2

Source: https://coursetro.com/posts/code/112/Angular-5-Deployment---Deploy-your-Angular-App


---------------------------------------------------
How to make it smaller. Source: https://github.com/angular/angular-cli/issues/8280

```
const express = require('express'),http = require('http'),path = require('path'),compression = require('compression');

const app = express();

app.use(express.static(path.join(__dirname, 'dist')));
app.use(compression()) //compressing dist folder 
app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, 'dist/index.html'));
})

const port = process.env.PORT || '4201';
app.set('port', port);

const server = http.createServer(app);
server.listen(port, () => console.log('Running at port ' + port))
```

```
Make sure you install dependencies;

npm install compression --save
npm install express --save;
Now build the app

ng build --prod --build-optimizer
If you want to further compress the build say reduce 300kb(approx)
from , then follow the below process;

Create a folder called vendor inside the src folder and inside vendor folder create a file rxjs.ts and paste the below code in it;

export {Subject} from 'rxjs/Subject';
export {Observable} from 'rxjs/Observable';
export {Subscription} from 'rxjs/Subscription';
And then add the follwing in the tsconfig.json file in your angular-cli application;

"paths": {
      "rxjs": [
        "./vendor/rxjs.ts"
      ]
    }
```

This will make your build size way too smaller. In my project I reduced the size from 11mb to 1mb.




ng new MiPrimeraApp
npm i -g angular-cli-ghpages

ng build -prod --base-href="https:/josealonso/github.io/MyAngularProject/"
git add .
git commit -m "first commit"
git remote add origin git@github.com:yourinfo/yourgit.git (I used https, not git).
git push -u origin master
Just to make sure: git remote -v

Then, finally, we can use the Github-pages CLI to push our project to github-pages:
angular-cli-ghpages
> Successfully published!

