# ConfigTag Jekyll Plugin

This is a plugin designed to help other plugins make configuration available to Javascript through HTML5 data attributes.

## Installation

Copy `config_tag.rb` into your Jekyll plugins directory.

## Liquid tag usage

Given the following yaml configuration:

```
site_author:
  name: Bob Loblaw
  profession: Lawyer

sandwich: [avacado, bacon, lettuce, tomato]

url: http://j.mp/Ze0u3D
```

The following config tags:

```
{% config_tag site_author %}
{% config_tag sandwich tag:span %}
{% config_tag url classname:rick-roll %}
```

Will produce:
```html
<div class='site-author' data-name='Bob Loblaw' data-profession='Lawyer'></div>
<span class='sandwich' data-value='avacado,bacon,lettuce,tomato'></span>
<div class='rick-roll' data-value='http://j.mp/Ze0u3D'></div>
```

### Of Note

This is best when used with nested configurations like the first example. When a value contains an array, it will be joined with a comma; if it is a hash, it will be converted to JSON which can be parsed in Javascript with `JSON.parse(json)`.

Most of the work happens in the `config_tag` method, which can be used directly by other Jekyll plugins if they want to wrap this within some other feature.

## License MIT

Copyright 2013, Brandon Mathis.
Released under an [MIT license](http://opensource.org/licenses/MIT).
