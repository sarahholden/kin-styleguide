# Kin Styleguide

The purpose of this document is to provide guidelines for writing CSS. Code conventions are important for the long-term maintainability of code. The goal is to have everyone’s code look the same, which allows any developer to easily work on another developer’s code.



## Table of contents

1. [General principles](#general-principles)
2. [Whitespace](#whitespace)
3. [Format](#format)
4. [Comments](#comments)
5. [Order of Properties](#order-of-properties)
6. [SCSS](#scss)



<a name="general-principles"></a>
## 1. General principles

* Don't try to prematurely optimize your code; keep it readable and
  understandable.
* All code should look like a single person typed it, even
  when many people are contributing to it.
* Strictly enforce the agreed-upon style.


<a name="whitespace"></a>
## 2. Whitespace

Each indentation level is made up of one 2-space tab
```css
/* Good */
.class {
  color: #fff;
  background-color: #000;
}

/* Bad - four spaces */
.class {
    color: #fff;
    background-color: #000;
}

/* Bad - all on one line */
.class {color: #fff; background-color: #000;}
```

In Sublime, go to View>Indendation>Tab Width: 2, also uncheck "Indent Using Spaces." Also install Sublime's "Trailing Spaces" plugin through package control to be able to see/trim trailing white space easily.

<a name="format"></a>
## 3. Format

* Use one discrete selector per line in multi-selector rulesets.
* Include a space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* Use double quotes e.g., `content: ""`.
* Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Place the closing brace of a ruleset in the same column as the first
  character of the ruleset.
* Separate each ruleset by a blank line.
* For classes, always use dashes and never camel case or underscores

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  display: block;
  font-family: helvetica, arial, sans-serif;
  color: #333;
  background: #fff;
  background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
  padding: 10px;
}
```

```css
/* Good */
.class-name {
  background-color: blue;
  color: red;
}

/* Bad - missing spaces after colons */
.class-name {
  background-color:blue;
  color:red;
}

/* Bad - missing last semicolon */
.class-name {
  background-color: blue;
  color:red
}
```

```css
/* Good */
.class-name {
  color: #fff;
}

/* Bad - closing brace is in the wrong place */
.class-name {
  color: #fff;
  }

/* Bad - no space before opening brace */
.class-name{
  color: #fff;
}
```

```css
/* Good - Use dashes */
.this-is-good {}

/* Good - don't use camel case */
.thisIsBad {}

/* Bad - don't use underscores */
.this_is_bad {}
```
<a name="comments"></a>
## 4. Comments

Always comment your code!

* Place comments on a new line above their subject.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use "sentence case" comments and consistent text indentation.

Example:

```css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

/* Basic comment */
```

<a name="order-of-properties"></a>
## 5. Order of Properties

Order properties grouped by type using CSSComb. This keeps our code base clean and allows for others to scan and understand your css a bit faster.

Example:

```css
.selector {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  z-index: 10;

  /* Display & Box Model */
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  margin: 10px;
  padding: 10px;
  width: 100px;
  height: 100px;
  border: 10px solid #333;

  /* Color */
  background: #000;
  color: #fff
  
  /* Text */
  font-family: sans-serif;
  text-align: right;
  font-size: 16px;
  line-height: 1.4;

  /* Other */
  cursor: pointer;
}
```


<a name="scss"></a>
## 6. SCSS

Keep nesting to 3 levels deep!!! This prevents overly-specific CSS selectors. Avoid large numbers of nested rules. Break them up when readability starts to be affected. Preference to avoid nesting that spreads over more than 20 lines.

```scss
/* Good */
.class-name {
  .inner {
    ...

      .title {
       ....

          .subtxt {
          ...

           }
       }
   }
}

/* Bad - more than 3 levels of nesting */
.class-name {
  .inner {
    ...

      .title {
       ....

          .subtxt {
              ...

              .element {
                  ...

               }
           }
       }
   }
}
```


Declare `@extend` followed by `@include` statements first in a declaration block.

```scss
/* Good */
.class-name {
    @extend .company;
    @include font-size(14);
    color: #555;
    font-size: 11px;
}

/* Bad */
.class-name {
    color: #555;
    @extend .company;
    font-size: 11px;
    @include font-size(14);
}
```


Based on a work at
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
