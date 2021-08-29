# Boxwork
This is a collection of utility classes that 

My imagined use case is a blog or article where all the content is contained in a fixed-width, centered **main-content** element, with no sidebar elements on the left or right.

Please note that this is
- **not a grid system**. You can't build 

## Basics
- **breakout container:** An element that expands outside the main-content element. Any element with a class of `bw-breakout` will break out of the main-content element and extend across the entire screen by default. You can adjust that width using max-width classes below. Breakout containers are good for things like pull quotes, large images, etc.

## Out of the...box

Boxwork provides utility classes for the following:
- padding
- margin
- max-width. Typically you'd use this on elements that you want to extend outside of the main content area. So if your main content area has a max-width of 48em, and you want to insert a pull quote that extends outside of it, you'd apply a class of `breakout` followed by a max-width class.
- grid-gap
- columns


### Breakpoints
Specify your breakpoints as follows:
```
$boxwork__breakpoints: (
  sm: 40em,
  md: 50em,
  lg: 60em
);
```


### Padding
Define padding values as follows:
```
$boxwork__padding: 0 1em 1.4em 2em 2.4em;
```

#### Examples
- `padding-2` Applies a padding of `2`. 
- `padding-inner-3` Applies a padding of `3` to the inner container of the element the class is applied to.
- `l-padding-4@lg` Applies a left padding of `4` at the largest screen size

### Margin
Define margin values as follows:
```
$boxwork__margin: 0 1em 1.4em 2em 2.4em;
```

#### Examples
- `margin-2` Applies a margin of `2`. 
- `margin-inner-3` Applies a margin of `3` to the inner container of the element the class is applied to.
- `l-margin-4@lg` Applies a left margin of `4` at the largest screen size

### Max-width
Max-width classes are what you'd apply to a breakout container. These classes are intended for elements that are wider than the main-content area. 

Define max-width values as follows:
```
$boxwork__max-width: 40em 44em 50em 60em;
```

#### Examples
- `mw-2` Applies a max-width of `2`. 
- `mw-inner-3` Applies a max-width of `3` to the inner container of the element the class is applied to.
- `mw-4@lg` Applies a max-width of `4` at the largest screen size

### Inner widths
Inner-width classes 


### Columns
Boxwork provides a simple grid system that allows you to 

This is not a full-fledged grid system; you can't at this time specify different-width columns. This would be useful for a three-column layout, a grid of cards, etc.

### Outdenting
Boxwork includes a set of classes to shift elements outside the left or right edges of the main content area by a certain amount. This can range from extending slightly outside—perhaps for an image or blockquote—to falling entirely outside the main content area, similar to marginal annotations. (As the window narrows, the element will shift back inside the main content area, and the main content will flow around it.)

You can outdent an element one of two ways: standard, or percentage-based.

- Standard: This follows the format of things like `padding` and `margin`: 
- Percentage: this is a percentage of the element. `outdent-50-pct` outdents the element by half of its width. `outdent-100-pct` outdents the element by its entire width, placing it right outside the main-content area (good for things like margin notes at larger screen sizes).

**Note:** Do not include the % sign when specifying outdent values as percentages.


### Setup
This describes what config variables you will need to set. (Boxwork comes with default values, and will work with none of these set, but you'll probably want to customize the breakpoints at the least.)

#### Unit-based helper classes
The following config variables are lists of `em` values (or `px`, `%`, or any other CSS unit):
- `$boxwork__padding`
- `$boxwork__margin`
- `$boxwork__max-width`
- `$boxwork__grid-gap`

#### Inner widths

## Basics
- **Format:** Utility classes function similar to those in Bootstrap: `padding-3`, `l-margin-2`, etc. `2` is not itself an amount; it represents an amount of padding that you specified.
- **Inner container:** In some cases, you might want to apply these classes to an element contained within an element; say, an inner container whose markup you don't have access to. Any classes with `-inner` will target a child element whose classname you will define via the `$boxwork__inner-container` config variable. (If you want to target multiple inner elements, you might need to generate those classes yourself using the `boxwork__makeRules()` mixin.)

The pattern is as follows, with optional tokens wrapped in curly brackets:

`[{direction}]-[property]-[{inner}]-[amount]{@[breakpoint]}`

- `direction`: this is an optional prefix for some properties, like margin or padding, that specifies which side/direction they should be applied to. (These do not apply to properties like `width`, and if you specify a direction in the class-generating mixin, you'll get non-standard properties like `width-right`.)
	- `t-`: top
	- `r-`: right
	- `b-`: bottom
	- `l-`: left
	- `x-`: left and right
	- `y-`: vertical and horizontal
- `property`: The property you're targeting. Can be any CSS property, although as mentioned above, only specific CSS properties have modifiers such as `-top`, `-right`, etc.
- `inner`: This targets a child element of the container it's applied to. The child element can be anything you pass as a `child` parameter in the `boxwork__makeRules()` mixin.

### Examples:
- `padding-2` Applies a padding of `2`. 
- `padding-inner-3` Applies a padding of `3` to the inner container of the element the class is applied to.
- `l-margin-4@lg` Applies a left margin of `4` at the largest screen size



## Mixins
Using the mixins, you can import the Boxwork library and generate utility classes for any CSS properties that aren't already included in Boxwork.

## The `--current-` var
The fluid indent code has to perform calculations to know how to position the element. In order to perform these accurately, it needs to know what padding and margins are currently being applied to the element. The `--current-XXX` variable contains the values of whatever a utility class is applying to an element.

## Properties
