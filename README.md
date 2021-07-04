# A very basic and most effective SCSS guide

### SCSS Variables : A closer look at how to define variables

As we know that it is possible to define variables into scss file so that we can use them anywhere as needed. So in this section, we will see how can we define a variable into a scss file.

Defining variables is very straightforward as other programming languages. Every variable should start with $ sign. So let's say we want to define a variable name color and in this variable, we want to have a value that is blue. Here is an example of how to achieve this thing in code.

```tsx
$color: blue;
```

So we successfully write our very first variable that is great. Now the question is how do we use this variable right? Take a look at the next code example you will understand how.

```tsx
p {
    color: $color;
}
```

This is all CSS and you can see how simple it is. Cool right? Anyways, have you noticed a thing that we did not place the value blue into any quote whether single quote ' ' or double quote " " ?. Because unlike other programming languages like javascript, there is no need to place any quote between string values. You can easily write the value without quotes.

Another thing is instead of (=) sign we used (:) sign in order to assign a value into a color variable. So this is how things work in scss. Hopefully, we got a clear understanding of how to define a scss variables.

### CSS nesting : How do we nest css into SCSS?

```tsx
<nav>
  <ul>
    <li>
      {" "}
      <a href="#"> Something </a>{" "}
    </li>
    <li>
      {" "}
      <a href="#"> Another thing </a>{" "}
    </li>
  </ul>
</nav>
```

If you see the HTML code above you can see this a simple Navigation markup right? Let's say we want to style this nav with css, so we will do something like that.

```tsx
nav {
    background-color: blue;
}
nav ul {
    list-style: none;
}
nav ul li {
    border-right: 1px solid #000;
}
nav ul li a {
    text-decoration:none;
}
```

This is something we will do in order to make some style for our navbar. Now we will take a look at how we can achieve similar things in SCSS.

```tsx
nav {
    background-color: blue;
    ul {
        list-style: none;
        li {
            border-right: 1px solid #000;
            a {
                text-decoration:none;
            }
        }
    }
}
```

This code is identical as we wrote code before in css. So when we compile our SCSS code to css this code will compile into css code as we showed. This is how we write nested code into SCSS.

### @mixin in SCSS : How to write function?

You might be wondering, what function is doing inside SCSS. This is the truth. You can write your own function as you do in other programming languages and use it as many times as you needed.

Here this is called @mixin. You see we put (@) sign before mixin keyword. This is because of the way SCSS define mixin like that. Now we will see how can we define our own @mixin and how we can use them in code.

```tsx
@mixin font-color($color) {
    color: $color;
}
```

This is how we declare function or @mixin in SCSS. As with any other function in programming languages, we have to give a function name. In this case, the name of the function is font-color. You can name a function whatever you want. It takes a parameter $color which we will pass via our function argument. We will see this in a second.

```tsx
p {
    @include font-color(blue);
    font-size: 15px;
}
```

So here we called the font-color mixin or function inside p. You can see we used @include in front of our function call. And we pass the blue value inside the function calls. Which is the real value of the font color of P. This the way calling functions in SCSS. The compiled css would be like below.

```tsx
p {
    color: blue;
    font-size: 15px;
}
```

### Condition in SCSS : How to write logical conditions?

It is possible that you can render css based on some conditions. And to achieve this there is some syntax for this they are called directives. You might be familiar with these directives from some templating engine or other javascript frameworks. They are similar to that.

```tsx
@if and @else
```

These are two directives for writing logical conditions in SCSS. Using these two directives we can achieve many complex things easily. We can see this from the code below.

```tsx
@mixin draw-border($name) {
    @if $name == light-border {
        border: 1px solid #000;
    }
    @else if $name == medium-border {
        border: 5px solid #000;
    }
    @else if $name == dark-border {
        border: 10px solid #000;
    }
    @else {
        border: 2px solid #000;
    }
}
```

We have just written a mixin for a border. Now we will take a look at how we can use them and how conditions will apply according to our mixin argument.

```tsx
.mini-container {
    @include draw-border(dark-border);
    height: 200px;
    width: 200px;
    background-color: #fff;
}
```

The above code will generate a similar css code like below.

```tsx
.mini-container {
    border: 10px solid #000;
    height: 200px;
    width: 200px;
    background-color: #fff;
}
```

So we can see how we can reduce our code and energy by writing conditional code. Now we can use the `draw-border` mixin with three different conditions.

### For loop in SCSS : How to write for loop?

This is a game-changing thing in SCSS. The biggest advantage of any programming language is a loop. This is one of the important things in the programming world. And you can know by now already we can use for loop into our scss file. Which is crazy in my opinion.

```tsx
@for $size from 1 through 6 {
    .text-size-#{$size} {
        font-size: 15 * $size px;
    }
}

@for $size from 1 to 7 {
    .text-size-#{$size} {
        font-size: 15 * $size px;
    }
}
```

The above two loops will produce identical results. But there is a reason, why I wrote two examples. If you give a closer look at the first loop you will see I have used `from 1 through 6` but on the other hand in the second loop, I used `from 1 to 7`.

One thing you have to notice that I have used `#{}` for rendering the `$size` variable. And another thing is for this loop SCSS has `@for` directive.

There are two things you have to consider for sake of understanding what is going on there. If I describe the first one you will understand the second one also. `through` does not exclude the end number from the loop whereas `to` excludes the end number from the loop. So now you understand what's the fact about these two loops. The compiled css code should look as below.

```tsx
.text-size-1 {
    font-size: 15 px; // ( 15 * 1 )
}
.text-size-2 {
    font-size: 30 px; // ( 15 * 2 )
}
.text-size-3 {
    font-size: 45 px; // ( 15 * 3 )
}
.text-size-4 {
    font-size: 60 px; // ( 15 * 4 )
}
.text-size-5 {
    font-size: 75 px; // ( 15 * 5 )
}
.text-size-6 {
    font-size: 90 px; // ( 15 * 6 )
}
```

### Map in SCSS : How to map over items?

So far we have seen how to loop through in SCSS. In this section, we will see how to map over items. This will be more interesting and fun. SCSS is amazing and this is why it is so popular now a day.

```tsx
@each $color in red, green, blue {
  .text-#{$color} {
      color: #{$color};
  }
}

// The above code will generate similar css code below
.text-red {
    color: red;
}
.text-green {
    color: green;
}
.text-blue {
    color: blue;
}
```

However, we can take it to the next label.

```tsx
$colors: (primary: blue, danger: red, success: green);

@each $key, $color in $colors {
  .text-#{$key} {
    color: $color;
  }
}

// The above code will generate similar css code below
.text-primary {
    color: blue;
}
.text-danger {
    color: red;
}
.text-success {
    color: green;
}
```

At this point, we have a clear understanding of how to map through the items in scss. This is like some other programming languages. If you have some programming background then it is very easy to understand at a glance.

### While loop in SCSS : How to map over items depending on some condition?

While loop works if a certain condition meets. This is very straightforward. It is very technical so I won't go through all these. The while loop looks something like the code below.

```tsx
$heading: 1;
@while $heading < 7 {
  .heading-#{$heading} {
      font-size: 15 * $heading px;
  }
  $heading: $heading + 1;
}

// The above code will generate similar css code below
.heading-1 {
  font-size: 15 px;
}
.heading-2 {
  font-size: 30 px;
}
.heading-3 {
  font-size: 45 px;
}
.heading-4 {
  font-size: 60 px;
}
.heading-5 {
  font-size: 75 px;
}
.heading-6 {
  font-size: 90 px;
}
```

In this example, we have seen a condition `$heading < 7`. This means if $heading is less than 7 run the loop.

### Partials in SCSS : How to import another .SCSS file into a .SCSS file?

If you are familiar with including files, for example, we can include as many CSS files into our html file via link tag as we want right? This technique is very handy when it comes to managing our large projects.

This is the same concept about Partials in scss. Using partials we can easily split our code into different .scss file and include into our any file when needed.

There is a way to write partials, that the partials should start with ( \_ ). So now we will see an example that how we can use partials.

Let's say we have a partials file named `_hero.scss` and we want to use the partials into our `main.scss` file. So inside the main.scss file the code would be like below.

```tsx
@import 'hero'
```

Have you noticed one thing that when we `@import 'hero'` partials into main.css file we did not put _ in front of the name? Yes, you are right? This _ should not put, we have to remember that.

This way we can import all the code written into `_helo.scss` file into the `main.scss` file. This is all about partials in SCSS.

### Extend in SCSS : How to reuse our code by extend feature?

SCSS comes with so many features as we know by now. Last, but not least, the thing I want to talk about is Extend feature in SCSS. This a one of the powerful features of SCSS. And I loved it.

With this feature, we can easily clone a block of code form other code block. What I mean by that I will show an example and you will understand easily.

Let's say I have a class named `.mini-container` with some property and I want to use all the property of the `.mini-container` inside another class named `.mini-blue-container`.

```tsx
.mini-container {
    height: 300px;
    width: 300px;
    border: 1px solid red;
}

.mini-blue-container {
    @extend .mini-container;
    background-color: blue;
}

// The compiled code would look something like
.mini-container, .mini-blue-container {
  height: 300px;
  width: 300px;
  border: 1px solid red;
}
.mini-blue-container {
  background-color: blue;
}
```

So we can see that using the `@extend` feature we reduced our code size and saved time as well.

## Conclusion

SCSS is awesome. I did not grab all that, to be honest. But hopefully, this article will help you with a better understanding of SCSS.
