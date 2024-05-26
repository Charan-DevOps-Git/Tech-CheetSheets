# Introduction

Angular is a platform and framework for building single-page client applications using HTML and TypeScript. Angular is written in TypeScript and offers a rich set of libraries for developing various functionalities.

# Basic Setup
1. Install Angular CLI:
```
npm install -g @angular/cli
```

2. Create a New Angular Project:
```
ng new my-angular-app
cd my-angular-app
ng serve
```

# Project Structure

1. src/app: Contains the application code.
- app.module.ts: Main application module.
- app.component.ts: Root component.
- app.component.html: Root component template.
- app.component.css: Root component styles.

# Modules

- Creating a Module:
```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

- Importing Modules:
```
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [FormsModule]
})
```

# Components

- Generating a Component:
```
ng generate component my-component
```

- Component Decorator:
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
export class MyComponent {
  title = 'My Angular Component';
}

```

- Component Template:
```
<h1>{{ title }}</h1>
```

- Component Styles:
```
h1 {
  color: blue;
}
```

# Data Binding

- Interpolation:
```
<p>{{ title }}</p>
```

- Property Binding:
```
<img [src]="imageUrl">
```

- Event Binding:
```
<button (click)="onClick()">Click me</button>
```

- Two-Way Binding:

html
```
<input [(ngModel)]="name">
<p>Hello, {{ name }}!</p>
```
typescript
```
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [FormsModule]
})
```

# Directives

1. Structural Directives:

- *ngIf:
```
<p *ngIf="isVisible">Visible</p>
```

- *ngFor:
```
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>
```

2. Attribute Directives:

- ngClass:
```
<p [ngClass]="{'class-name': isClassActive}">Text</p>
```

- ngStyle:
```
<p [ngStyle]="{'color': isRed ? 'red' : 'blue'}">Text</p>
```

# Services and Dependency Injection

- Creating a Service:
```
ng generate service my-service
```
```
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class MyService {
  getValue() {
    return 'Service Value';
  }
}
```

- Using a Service in a Component:
```
import { Component } from '@angular/core';
import { MyService } from './my-service.service';

@Component({
  selector: 'app-my-component',
  templateUrl: './my-component.component.html',
  styleUrls: ['./my-component.component.css']
})
export class MyComponent {
  value: string;

  constructor(private myService: MyService) {
    this.value = myService.getValue();
  }
}
```

# Routing

- Setting Up Routes:
```
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

- Router Outlet:
```
<router-outlet></router-outlet>
```

- Router Links:
```
<a routerLink="/">Home</a>
<a routerLink="/about">About</a>
```

# HTTP Client

- Importing HttpClientModule:
```
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  imports: [HttpClientModule]
})
```

- Making HTTP Requests:
```
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class DataService {
  constructor(private http: HttpClient) { }

  getData() {
    return this.http.get('https://api.example.com/data');
  }
}
```

- Using HttpClient in a Component:

```
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-data',
  template: `
    <ul>
      <li *ngFor="let item of data">{{ item }}</li>
    </ul>
  `
})
export class DataComponent implements OnInit {
  data: any[];

  constructor(private dataService: DataService) { }

  ngOnInit() {
    this.dataService.getData().subscribe((response: any) => {
      this.data = response;
    });
  }
}
```

# Forms

- Template-Driven Forms:
```
<form #myForm="ngForm" (ngSubmit)="onSubmit(myForm)">
  <input name="name" ngModel required>
  <button type="submit">Submit</button>
</form>
```
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-form',
  templateUrl: './form.component.html'
})
export class FormComponent {
  onSubmit(form: any) {
    console.log(form.value);
  }
}
```

- Reactive Forms:
```
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({
  selector: 'app-reactive-form',
  templateUrl: './reactive-form.component.html'
})
export class ReactiveFormComponent implements OnInit {
  myForm: FormGroup;

  constructor(private fb: FormBuilder) { }

  ngOnInit() {
    this.myForm = this.fb.group({
      name: ['', Validators.required]
    });
  }

  onSubmit() {
    console.log(this.myForm.value);
  }
}
```
html
```
<form [formGroup]="myForm" (ngSubmit)="onSubmit()">
  <input formControlName="name" required>
  <button type="submit">Submit</button>
</form>
```

# Pipes

- Using Built-In Pipes:

```
<p>{{ today | date }}</p>
<p>{{ 1234.56 | currency }}</p>
```

- Creating a Custom Pipe:
```
ng generate pipe my-pipe
```
```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'myPipe'
})
export class MyPipe implements PipeTransform {
  transform(value: string): string {
    return value.toUpperCase();
  }
}
```
html
```
<p>{{ 'hello' | myPipe }}</p>
```

# Resources
[Angular Official Documentation](https://v17.angular.io/docs)

