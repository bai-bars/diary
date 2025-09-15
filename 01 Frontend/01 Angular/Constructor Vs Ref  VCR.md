Difference between a constructor-injected `ViewContainerRef` and an `ng-container` reference `ViewContainerRef`:

### Constructor Injected `ViewContainerRef`

- **What:** Refers to the container of the component itself. Refers to the component’s host view
- **Use:** Manipulates the view of the component.

```typescript
constructor(private vcr: ViewContaienRef) {}
```

[[Component HostView]]
### `ng-container` Reference `ViewContainerRef`

- **How:** Obtained via `@ViewChild` referencing an `ng-container` with a template reference variable.
- **What:** Refers to the location of the `ng-container` in the template.
- **Use:** Manipulates views at the position of the `ng-container` (e.g., insert templates/components at a specific spot).
- **Example:**
  
```html
<ng-container #container></ng-container>
```

```typescript
@ViewChild('container', { read: ViewContainerRef }) vcr!: ViewContainerRef;
```
### Summary

- **Constructor:** Refers to the component’s host view.
- **ng-container:** Refers to a specific spot in the template.

Use `ng-container` reference when you need precise control over where dynamic content appears. Use constructor injection for general view manipulation within the component.
