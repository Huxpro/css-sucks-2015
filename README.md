# CSS Still Sucks 2015

### (都 2015 年了，CSS 怎么还是这么糟糕)


### [Watch Slides → ](http://huangxuan.me/css-sucks-2015)

<img src="http://huangxuan.me/css-sucks-2015/attach/qrcode.png" width="300" />

### Catalog

- Document Times
    - Frameworks
    - Style Guide
        - OOCSS
        - SMACSS
    - Pre-processer
    - PostCSS
- Application Times
    - Shadow DOM
    - CSS "4"
    - Naming Convention
        - BEM
        - SUIT
    - CSS in JS
    - CSS Modules  
        - Interoperable CSS
    - PostCSS, again
- My Opinionated Proposal
    - Page Override Components

## Page Override Components

### 1. Scoping Components <br><small style="line-height:2em;">*CSS Blocks should only be used inside a component of the same name.*</small>

```scss
// Component/index.scss
.ComponentName {
    &--mofierName {}
    &__decendentName {
        &--modifierName {}
    }
    .isStateOfComponent {}
}
```

```javascript
// Component/index.js
require('./index.scss');
```

CSS is *always bundled* with components<br>(from loading, mount to unmount)

### 2. Components can be Overrode by Pages <br><small style="line-height:2em;">*There is always requirements to rewrite styles of components in pages*</small>

```scss
// Pages/PageA.scss
#PageA {
    .pagelet-name {
        .pagelet-descendent-name {}
    }
    .ComponentName{ /* override */ }
}
```

```javascript
// Pages/index.js
require('./PageA.scss');
```

- *#Page* for absolutely scoping between pages
- *.pagelet-name* should be lowercase to prevent conflicting with components

### Why POC?

- It's technology-agnostic<br>
<small>
    *One css framework can be played with whatever technology stacks*<br>
    *You can combined Scss, PostCSS and whatever you want*
</small>

- Solving problems, and easy<br>
<small>
    *Makes reading and teamwork much easier*<br>
    *Get all benefit from BEM, SUITCSS and others*
</small>

- Leverage the power of cascading properly<br>
<small>
    *Scoping components but allow reasonable overriding*<br>
    *It's pragmatic, flexible and hitting the sweet spot*
</small>

### Thanks

[Reveal.js](http://lab.hakim.se/reveal-js)
