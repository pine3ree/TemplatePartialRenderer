# Partial Renderer for Processwire 2.4

> "Calls" and renders an external php template injecting variables

## Usage inside a processire template

```
$out = $page->renderPartial('partial/pagination', array(
    'pages' => $posts,
));

//...

echo $out;
```

or directly echo the result:

```
$page->renderPartial('partial/pagination', array(
    'pages' => $posts,
), true);
```


## Install

- Place the files from this module in /site/modules/TemplatePartialRenderer/
- In ProcessWire Admin > Modules, click *check for new modules*, and click *install*.
