# ngx-ellipsis

Plugin for angular (>= 4.0.0) providing a directive to display an ellipsis if the containing text would overflow.

Supports text only (no html contents)!

## Installation

For use in an existing angular project run `npm install ngx-ellipsis --save`.

Then add the installed module to your `app.module.ts`:

```typescript
import { EllipsisModule } from 'ngx-ellipsis';

// ...

@NgModule({
  // ...
  imports: [
    // ...
    EllipsisModule
  ]
  // ...
})
export class AppModule {}

```

## Usage

Anywhere in your template:

```html
<div ellipsis>Your very long text</div>
```

### Extra options

You may add the following attributes to change the directive's behavior:

| attribute | meaning |
| ---- | ---- |
| __ellipsis__ | _required_ If you pass an attribute value (e.g. `ellipsis=" More ..."`) you can override the text that will be appended, should it be necessary to truncate the text (_default_: "...")|
| __ellipsis-content__ | Use this for dynamic content, that will be subject to asynchronous changes (e.g.: `[ellipsis-content]="myVar"`) |
| __ellipsis-word-boundaries__ | If you pass this attribute, the text won't be truncated at just any character but only at those in the attribute's value. For example `ellipsis-word-boundaries=" \n"` will allow the text to break at spaces and newlines only |
| __ellipsis-resize-detection__ | How resize events should be detected - these are the possible values: <ul><li>__element-resize-detector__: _default_ Use [wnr/element-resize-detector](https://github.com/wnr/element-resize-detector) with its `scroll` strategy. (-> Even when you change the element's width using javascript, the ellipsis will auto-adept)</li><li>__element-resize-detector-object__: _deprecated_ Use [wnr/element-resize-detector](https://github.com/wnr/element-resize-detector) with its `object` strategy</li><li>__window__: Only check if the whole window has been resized/changed orientation by using angular's built-in `HostListener` (Possibly better performance, but obviously won't trigger on resize caused directly or indirectly by javascript.)</li></ul> |
| __ellipsis-click-more__ | Event emitter - If set, the text defined by the `ellipsis`  attribute will be converted into a clickable link. For example `(ellipsis-click-more)="moreClicked()"` will call your component's `moreClicked()` method when the user clicks on the link.|


## Build & publish on npm

In case you want to contribute/fork:

`npm install && npm run build` outputs the build to `./dist`.
Then you can publish by adepting version and author in `./dist/package.json`, adding your modified `README.md` to `./dist/` and running `cd dist && npm publish`.


## Running unit tests

Run `npm run test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Thank you...

- ... __Cyrille Tuzi__ for creating a very [comprehensive tutorial on how to build and publish angular modules](https://medium.com/@cyrilletuzi/how-to-build-and-publish-an-angular-module-7ad19c0b4464).
- ... __Lucas Wiener__ for writing the [element-resize-detector](https://github.com/wnr/element-resize-detector) packages which is internally used by this module.

## License

MIT
