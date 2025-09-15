### What is a "Ref"?

Think of a "Ref" as a **reference** or a **handle** to something in Angular. It's like having a remote control for different parts of your application.

### 1. `ViewContainerRef` - The Container

**What it is**: A reference to a **container** where you can dynamically insert views (components/templates).

**Think of it as**: A picture frame where you can swap in different pictures.

```html
<ng-container #vcr></ng-container>
```

```typescript
@ViewChild('vcr', { read: ViewContainerRef }) vcr!: ViewContainerRef;
```

```typescript
constructor(private vcr: ViewContaienRef) {}
```

**What we can do with it**:
- `createEmbeddedView()` - Insert a template
- `createComponent()` - Insert a component
- `clear()` - Remove everything
- `insert()`, `remove()` - Manage views
  
link: [[Constructor Vs Ref  VCR]]
### 2. `TemplateRef` - The Blueprint

**What it is**: A reference to an `<ng-template>` - it's like a **blueprint** or **stamp** that can be used to create views.

**Think of it as**: A cookie cutter - it defines the shape, but doesn't create the actual cookie until you use it.
```html
<ng-template #template></ng-template>
```

```typescript
@ViewChild('template', { read: TemplateRef }) template!: TemplateRef<{ name: string }>;
```

**What we can do with it**:
- Pass it to `createEmbeddedView()` to create actual views
- It's just a template definition - not a visible element until used

### 3. `EmbeddedViewRef` - The Actual View

**What it is**: A reference to an **actual rendered view** created from a template.

**Think of it as**: The actual cookie made from the cookie cutter.

```typescript
const view = this.vcr.createEmbeddedView(this.tpl, { name: 'Sazin' }); 
// this 'view' is an EmbeddedViewRef
```

**What you can do with it**:
- `detectChanges()` - Force change detection
- `destroy()` - Remove the view
- `markForCheck()` - Mark for change detection

link: [[ngTemplateOutlet Vs CreateEmbeddedView()]]
### 4. `ApplicationRef` - The Entire App

**What it is**: A reference to the **entire Angular application**.

**Think of it as**: The manager of the entire building (your app).

**What you can do with it**:
- `attachView()` - Attach views directly to the app
- `tick()` - Trigger change detection globally
- `bootstrap()` - Start the app
