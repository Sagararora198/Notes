


# Angular Notes

## Installation

### Download Angular Globally
```bash
npm install -g @angular/cli
```

### Create a New Project
```bash
ng new name_of_project
```

### Run the Project
```bash
ng serve
```

## File Structure

### Important Files
- **.editorconfig**: Used to set the coding standards defined by the manager.
- **angular.json**: Contains all the Angular-related configuration of your project.
- **assets folder**: All files under this folder will be publicly accessible.
- **polyfills.js**: Ensures modern JavaScript works in older browsers.

### Bootstrapping of Angular Program
```
Angular Project
    |
   index.js
    |
  angular.js
    |
   main.ts
    |
 AppModule
    |
 AppComponent
    |
 View Template (app.components.html)
```

## Data Binding

### From Component to View Template
- **String Interpolation**: `{{}}`
- **Property Binding**: `[property]="data"`

### From Template to Component
- **Event Binding**: Wrap the event in `()`

### Difference Between HTML Attribute and Property
- **Attribute**: Fixed values (e.g., `<input value="Phone No:">`)
- **Property**: Dynamic values that can change (e.g., user input in an input field)

## Directives

### Types of Directives
1. **Component Directive**: Components in the DOM.
2. **Attribute Directive**: Change behavior in the DOM.
3. **Structural Directive**: Change the DOM by adding and removing components (start with `*`).

## Component Communication

- **@Input**: Equivalent to props in Angular.
- **@Output**: For communication from child to parent.
- **@defer**: Load your component after some time or based on some logic.

## Routing in Angular

- Create a `router.ts` where all the routes are defined.
- Add the routes to the configuration file and use them in the component.

## Forms in Angular

### Types of Forms
1. **Template-Driven Forms**
2. **Reactive Forms**: Manage forms programmatically.

### Two-Way Data Binding
- Use `[(ngModel)]` for two-way data binding.

## Pipes

- Functions used to transform data in templates.
- Example: `{{loudMessage | uppercase}}` will transform `loudMessage` to uppercase.

## Services in Angular

- Functions or objects used to share data and behavior across the application.

## Event Handling

- **@HostListener**: Listen to events on the host element.
- **viewProviders**: Specify providers that are visible only to the view.

## Observables in RxJS

- **Observable**: Sends data.
- **Observer**: Watches the data using `.subscribe`.
- **Subject**: Can be used instead of `EventEmitter`.

### Unsubscribe from Observables
- Always unsubscribe from observables to prevent memory leaks.

## Component Lifecycle Hooks

1. **ngOnChanges**: Invoked when input properties change (`@Input`).
2. **ngOnInit**: Invoked when the component is initialized.
3. **ngDoCheck**: Invoked whenever changes are detected in the component.
4. **ngAfterContentInit**: Invoked when HTML content is projected into the view.
5. **ngAfterContentChecked**: Invoked after the projected content is checked.
6. **ngAfterViewInit**: Invoked after the component's view has been initialized.
7. **ngAfterViewChecked**: Invoked after the component's view has been checked.
8. **ngOnDestroy**: Invoked just before the component is destroyed.

## ElementRef and TemplateRef in Angular

- **ElementRef**: Similar to `document.getElementById`.
- **TemplateRef**: Represents an embedded template that can be used to create embedded views.

## Service Hierarchy

- **App Module**: If a service is provided here, the same instance will be shared throughout the application.
- **App Component**: If a service is provided here, the same instance will be available in all child components but not in other services.
- **Child Component**: Each child component will have different instances of the service.

