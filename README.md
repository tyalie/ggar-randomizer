# Go Get A Roomie Randomizer

Small pages that automatically redirects to a random Go Get a Roomie panel to read.

See the original comic at [gogetaroomie.com][2]

I really really love this comic and I found so many thoughts, conversations, themes,
… in it with which I could identify. I noticed that for mental health that I would
sometimes skip to a pseudo-random location in the comic and read from there.

Sadly the page itself doesn't have this feature, so I was mostly just scrolling
through the archive and hit enter at some point. As the comic has more than a
thousand strips, I of course missed a lot of parts.

## The solution

When you open this page, it automatically redirects to a random panel on
gogetaroomie.com. Simple as that ^^

## Development

### Fill the comic list

Get the panel list by opening [the archive][1] and executing the following script in
the browser console

```js
// first select all option elements
let option_list = Array.from(document.querySelectorAll("#middle select > option"));
// remove elements without a value (e.g. "Select a comic") and convert to map
let data = Object.fromEntries(
    // the resulting array is Dict["comic-name", "sub-page"]
    option_list.filter(e => e.value.length > 0).map(e => [e.text, e.value])
);
// `copy` is part of the Console Utilities API
copy(JSON.stringify(data, null, 2));
```

Paste the result in a file named `comics.json`.

### Deploy

Deploy using GitHub Pages

[1]: https://www.gogetaroomie.com/comic/archive
[2]: gogetaroomie.com
