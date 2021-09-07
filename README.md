# TestUniversal

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 12.0.5.

The intention of this project is to replicate an issue found on the jarallax library while trying to build and run the app with SSR. Also, you can find this usefull for an example of how to use jarallax with angular.

If you run the project with `npm start` all is going to work as expected. However when you build (`npm run build:ssr`) and run (`npm run serve:ssr`) you will get this error:

"TypeError: Cannot destructure property 'navigator' of 'global__WEBPACK_IMPORTED_MODULE_1__.window' as it is undefined."

In order to integrate Jarallax I did the following:

1- npm i jarallax
2- in angular.json:

    "styles": [
        "src/styles.sass",
        "node_modules/jarallax/dist/jarallax.css"
    ],
    "scripts": [
        "node_modules/jarallax/dist/jarallax.min.js",
        "node_modules/jarallax/dist/jarallax-element.min.js",
        "node_modules/jarallax/dist/jarallax-video.min.js"
    ]

3- in polyfills.ts I added:
    
    (window as any).global = window;
4- I imported jarallax on the app.component.ts
5- Added last 3 lines into app.component.html

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
