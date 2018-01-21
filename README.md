#Angular

##Intro
Angular

##Tutorial
In order to use TypeScript on a specific machine, it needs to be installed. This can be done using the following commands and making sure that Node is already installed:

###The Application Shell
The *ng serve* command builds the app, starts the development server, watches the source files, and rebuilds the app as you make changes to those files.

The *--open* flag opens a browser to http://localhost:4200/.

**Components** are the fundamental building blocks of Angular applications. They display data on the screen, listen for user input, and take action based on that input.

You always import the Component *symbol* from the Angular core library and annotate the component class with @Component. **@Component** is a decorator function that specifies the Angular metadata for the component.

**Component** decorator allows you to mark a class as an Angular component and provide additional metadata that determines how the component should be processed, instantiated and used at runtime.
Components are the most basic building block of an UI in an Angular application. An Angular application is a tree of Angular components. Angular components are a subset of directives. Unlike directives, components always have a template and only one component can be instantiated per an element in a template.

A component must belong to an *NgModule* in order for it to be usable by another component or application. To specify that a component is a member of an NgModule, you should list it in the declarations field of that NgModule.
In addition to the *metadata* configuration specified via the Component decorator, components can control their runtime behavior by implementing *various Life-Cycle hooks*.

```
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```

One important metadata property includes the CSS element **selector**, which matches the name of the HTML element that identifies this component within a parent component's template.
The **ngOnInit** is a lifecycle hook. Angular calls ngOnInit shortly after creating a component. It's a good place to put initialization logic.
Always **export** the component class so you can import it elsewhere

```
<h2>{{ hero.name | uppercase }} Details</h2>
```
The word uppercase in the interpolation binding, right after the pipe operator ( | ), activates the built-in *UppercasePipe*.
**Pipes** are a good way to format strings, currency amounts, dates and other display data. Angular ships with several built-in pipes and you can create your own.

```
<input [(ngModel)]="hero.name" placeholder="name">
```
**[(ngModel)]** is Angular's two-way data binding syntax. Here it binds the hero.name property to the HTML textbox so that data can flow in both directions: from the hero.name property to the textbox, and from the textbox back to the hero.name.
Although ngModel is a valid Angular directive, it isn't available by default. It belongs to the optional **FormsModule** and you must opt-in to using it.

Styles and stylesheets identified in @Component metadata are scoped to that specific component.

####NgModules
**NgModules** configure the injector and the compiler and help organize related things together.

An NgModule is a class marked by the *@NgModule* decorator. @NgModule takes a metadata object that describes how to compile a component's template and how to create an injector at runtime. It identifies the module's own components, directives, and pipes, making some of them public, through the exports property, so that external components can use them. @NgModule can also add service providers to the application dependency injectors.

Modules are a great way to organize an application and extend it with capabilities from external libraries. Angular libraries are NgModules, such as *FormsModule*, *HttpClientModule*, and *RouterModule*. Many third-party libraries are available as NgModules such as *Material Design*, *Ionic*, and *AngularFire2*.

NgModules consolidate components, directives, and pipes into cohesive blocks of functionality, each focused on a feature area, application business domain, workflow, or common collection of utilities.

Modules can also add services to the application. Such services might be internally developed or come from outside sources. Modules can be loaded eagerly when the application starts or lazy loaded asynchronously by the router. NgModule metadata does the following:

* Declares which components, directives, and pipes belong to the module.
Makes some of those components, directives, and pipes public so that other module's component templates can use them.
* Imports other modules with the components, directives, and pipes that components in the current module need.
* Provides services at the other application components can use.

The root module is all you need in a simple application with a few components. As the app grows, you refactor the root module into feature modules that represent collections of related functionality. You then import these modules into the root module.


```
// imports
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { HttpModule } from '@angular/http';

import { AppComponent } from './app.component';
import { ItemDirective } from './item.directive';


// @NgModule decorator with its metadata
@NgModule({
  declarations: [
    AppComponent,
    ItemDirective
  ],
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
At the top are the *import* statements. The next section is where you configure the *@NgModule* by stating what components and directives belong to it (*declarations*) as well as which other modules it uses (*imports*).

####ngFor
The ***ngFor** is Angular's repeater directive. It repeats the host element for each element in a list. Don't forget the asterisk in front of ngFor. It's a critical part of the syntax.

####Symbols
Starting with ECMAScript 2015, **symbol** is a primitive data type, just like number and string. symbol values are created by calling the Symbol constructor. Symbols are immutable, and unique.

```
let sym1 = Symbol();
```
####Class Binding
The Angular class binding makes it easy to add and remove a CSS class conditionally. Just add [class.some-css-class]="some-condition" to the element you want to style.
