The **Teensy Weensy Testing Library** (*twtl*) is a tiny (1.6k) testing library for in-browser testing.

It outputs to your browser's console. It currently supports:

 * Opera Dragonfly
 * Firebug
 * Firefox Web Console
 * Webkit Web Inspector (Safari & Chrome)

*twtl* is not for asynchronous or server-side testing. It's just a small script for in-browser testing. It has rudimentary support for node.js but that's really not its purpose. Asynchronous support will be added when I figure out a way to do it without adding too much weight. I would like for it to remain simple.

### Output

*twtl* uses the console's already very-powerful object introspection to make the unit-testing process easier. In addition it will give you the file and line-number of failed assertions.

![Example output](http://i.imgur.com/M3tZG.png)

### API

It comes with two asserters by default:

 * toBe: Asserts that `a` is identical (`===`) to `b`
 * toEqual: Asserts that `a` is equal (by sensible measures) to `b`

*plus their `not` counterparts*

```js
test('Something I need to test', function() {

  expect(1).toBe(2);             // ✘
  expect({a:1}).toBe({a:1});     // ✘
  expect({a:1}).toEqual({a:1});  // ✔

  expect(1).not.toBe(2);         // ✔
  expect(1).not.toBe(1);         // ✘

});

// Augment functionality
twtl.augment('toMatch', function(a,b) { return b.test(a); });

test('Something else', function() {

  expect('abc').toMatch(/.+/);     // ✔
  expect('abc').not.toMatch(/.+/); // ✘

});
```

### Inspirations

 * API inspired by Jasmine.
 * Size inspired by Thumbilina.
 * Name inspired by Itsy Bitsy Spider.
