# MyAppNg

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 10.1.7.

Created simply as POC, to use the Angular with Jest, as a unit test.

# Setting up Jest

Hi Guys!!!!

So, this is little tutorial of configurations Jest Unit Test (This is a quick guide to setup Jest in your new Angular 10 application).

## 1. Install Jest

`npm install jest @types/jest jest-preset-angular --save-dev`

## 2. Uninstall Karma

After installing Jest, we will remove Karma and its dependencies:
`npm uninstall karma karma-chrome-launcher karma-coverage-istanbul-reporter karma-jasmine karma-jasmine-html-reporter @types/jasmine @types/jasminewd2 jasmine-core jasmine-spec-reporter`

## 3. Remove test from angular.json

Remove the test section from angular.json, this section looks like the following:

```

"test": { "builder": "@angular-devkit/build-angular:karma", "options": { "main": "src/test.ts", "polyfills": "src/polyfills.ts", "tsConfig": "tsconfig.spec.json", "karmaConfig": "karma.conf.js", "assets": [ "src/favicon.ico", "src/assets" ], "styles": [ "src/styles.scss" ], "scripts": [] } },```
```

## 4. Now, let's remove files:

``` karma.conf.js and src/test.ts```


## 5. Create `setupJest.ts` file

This file should have the following:

```
import 'jest-preset-angular';
```


## 6. Modify `tsconfig.spec.json`

```
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jest",
      "node"
    ]
  },
  "files": [
    "src/test.ts",
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}
```


## 7. Modify `package.json` file

Modify the test scripts to the following:

```
"test": "jest",
 "test:coverage": "jest --coverage",
```

Create jest.config.json and add Jest configuration in the file::

```mermaid
{
    "preset": "jest-preset-angular",
    "setupFilesAfterEnv": [
      "<rootDir>/setupJest.ts"
    ],
    "testPathIgnorePatterns": [
      "<rootDir>/node_modules/",
      "<rootDir>/dist/",
      "<rootDir>/src/test.ts"
    ],
    "globals": {
      "ts-jest": {
        "tsConfig": "<rootDir>/tsconfig.spec.json",
        "stringifyContentPathRegex": "\\.html$"
      }
    }
}
```


## 8 - after of the define the configurations, execute:

```npm test
npm test
```


## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Jest](https://jest.io).

## Running end-to-end tests

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
