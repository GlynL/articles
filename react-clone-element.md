react.cloneElement (https://reactjs.org/docs/react-api.html#cloneelement)
```
cloneElement()

React.cloneElement(
  element,
  [config],
  [...children]
)

Clone and return a new React element using element as the starting point. config should contain all new props, key, or ref. The resulting element will have the original element’s props with the new props merged in shallowly. New children will replace existing children. key and ref from the original element will be preserved if no key and ref present in the config.

React.cloneElement() is almost equivalent to:

<element.type {...element.props} {...props}>{children}</element.type>

However, it also preserves refs. This means that if you get a child with a ref on it, you won’t accidentally steal it from your ancestor. You will get the same ref attached to your new element. The new ref or key will replace old ones if present.
```

Thanks to Chakra UI for the idea. Heavily influenced  by their Tooltip component.

Previously used a wrapping div inside the <Tooltip /> component to apply the tooltip on hover. Causes styling issues in certain cases e.g. a flex child not filling the correct space.

Using clone element on the children of the tooltip means that there is no wrapping div interferign with styling.

Limitations
- doesn't work if the children is multiple components 
e.g. 
<Tooltip><div>one</div><div>two</div></Tooltip> no good 
<Tooltip><div><div>one</div><div>two</div></div><Tooltip> good

- relies on mouse events of child element. e.g. you can't have a tooltip for a disabled button (link resolution)
  
## Using with Tooltip
* add mouse in/out
* text
* shouldWrap prop (linked by limitation)
  
