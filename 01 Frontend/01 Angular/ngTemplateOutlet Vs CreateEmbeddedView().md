
`ngTemplateOutlet` cannot solve cases where you need to **dynamically insert, remove, or reorder templates based on complex runtime logic** that is only available in your component class.

**Example Case:**  
Suppose we need to insert a template at a specific position in a list, remove it later, or move it elsewhere—all based on user actions or asynchronous events.  
`ngTemplateOutlet` only renders templates declaratively in the template and cannot manage their lifecycle or position programmatically.

**Solution:**  
Use `ViewContainerRef` methods like `createEmbeddedView()`, `insert()`, `remove()`, and `move()` in your component class for such scenarios.

**Example:**
````typescript

@ViewChild('itemTemplate', { read: TemplateRef }) itemTemplate!: TemplateRef<any>;
constructor(private viewContainer: ViewContainerRef) {}

addItem(position: number, context: any) {
  this.viewContainer.insert(
    this.viewContainer.createEmbeddedView(this.itemTemplate, context),
    position
  );
}

removeItem(position: number) {
  this.viewContainer.remove(position);
}
````

**Summary:**  
Use `ViewContainerRef` and `createEmbeddedView()` when we need **dynamic, programmatic control** over template insertion, removal, or reordering—something `ngTemplateOutlet` cannot do.