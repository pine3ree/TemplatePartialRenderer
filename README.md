# Partial Renderer for Processwire 2.4

"Calls" and renders an external php template injecting variables as an
alternative to standard php global functions.

## Usage inside a processire template

```
$out = $page->renderPartial('partial/pagination', array(
    'pageArray' => $posts,
));

//...

echo $out;
```

or directly echo the result:

```
$page->renderPartial('partial/pagination', array(
    'pageArray' => $posts,
), true);
```

in this example the template to be rendered is located in

WEB_ROOT/site/templates/partial/pagination.php

and could look like this:

```
<?php
echo $pageArray->renderPager(array(
    'listMarkup' => '<ul class="pagination pagination-sm">{out}</ul>',
    'itemMarkup' => '<li class="{class}">{out}</li>',
    'linkMarkup' => '<a href="{url}">{out}</a>',
    'currentLinkMarkup' => '<a href="{url}">{out}</a>',

    'nextItemLabel' => '<i class="fa fa-angle-right"></i>',
    'previousItemLabel' => '<i class="fa fa-angle-left"></i>',
    'separatorItemLabel' => '<a href="#">&hellip;</a>',

    'separatorItemClass' => 'disabled',
    'firstItemClass' => 'first arrow',
    'firstNumberItemClass' => '',
    'nextItemClass' => 'next arrow',
    'previousItemClass' => 'prev arrow',
    'lastItemClass' => 'last arrow',
    'lastNumberItemClass' => '',
    'currentItemClass' => 'active current',
));
```

In this example the same styled pagination can be used for different pageArray
variables, using a partial template instead of a global function call.

You can also specify a different file extension.

```
$page->renderPartial('partial/pagination.phtml', array(
    'pageArray' => $posts,
), true);
```

Accepted extensions are: "php", "phtml", "inc", "tpl".
If omitted - as in the example - it defaults to "php".
Templates are supposed to be standard php/html template files.

## Install

- Place the files from this module in /site/modules/TemplatePartialRenderer/
- In ProcessWire Admin > Modules, click *check for new modules*, and click *install*.
