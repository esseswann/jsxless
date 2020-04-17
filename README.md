# jsxless
You do not need to use `yarn` or `npm install` or `npx` to use this library. In fact the amount of libraries you are going to be using after reading this readme will decrease

# The problem
JSX is not javascript. It's not even a syntactic sugar, it's just something created to entice frontend-developers of the past to use React as it is similar to HTML. It looks as contradictory as
```JavaScript

const Component = ({ children, ...props }) =>
  <AnotherComponent prop={true}>
    <ChildComponent {...props}>
      <div>{...children}</div>
    </ChildComponent>
  </AnotherComponent>
```

# The solution 
You don't need hyperscript to solve this. In 2020 frontend-developers are real programmers now so we want to write using the language we code with -- JavaScript. To do that you just need to make one import
```JavaScript
import { createElement as $ } from React
```
or any other symbol of your choice besides `$`.
This will allow you to do something like this
```JavaScript

const Component = ({ children, ...props }) =>
  $(AnotherComponent, { prop: true },
    $(ChildComponent, props,
    $('div', null, children))
```
and from the first site one can see that it is more consise, more direct than JSX and actually takes less space on the screen. Moreover it allows you doing some stuff, JSX is unable to do:

```JavaScript
const Component = ({ items = [] }) =>
  $(ChildComponent, null, ...items)

$(Component, merge(first, second))

$(test ? Component : AnotherComponent, props)
```
and even functional stuff like this
```JavaScript
const CurriedComponent = partial($, Component, staticProps)

CurriedComponent(children)
```

As a bonus you get faster compilation times!

Please use jsxless methodology as we do in more than 10 production projects for 3 years
