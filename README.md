# Partial Renderer for Processwire 2.5

"Calls" and renders an external php template injecting variables as an
alternative to standard php global functions.

## Usage inside a ProcessWire template:

- parameter 1 : string, template path relative to the site templates
- parameter 2 : optional array of variables to pass to the template
- parameter 3 : optional boolean, true => echo the result. Default to false => return the result

```
$posts = $pages->find('template=blog-container, sort=-post_date');

//...

$out = $this->renderPartial('partial/pagination', array(
    'pageArray' => $posts,
));

//...

echo $out;
```

or directly echo the result adding a 3rd boolean parameter set to TRUE:

```
$this->renderPartial('partial/pagination', array(
    'pageArray' => $posts,
), true);
```

in this example the template to be rendered is located in

WEB_ROOT/site/templates/partial/pagination.php

and could look like this (a foundation 5 styled pager):

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
$this->renderPartial('partial/pagination.phtml', array(
    'pageArray' => $posts,
), true);
```

Accepted extensions are: "php", "phtml", "inc", "tpl".
If omitted - as in the example - it defaults to "php".
Templates are supposed to be standard php/html template files.

## Install

- Place the files from this module in /site/modules/TemplatePartialRenderer/
- In ProcessWire Admin > Modules, click *check for new modules*, and click *install*.
