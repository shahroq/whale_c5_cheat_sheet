# Whale Concrete5 V8+ Cheat Sheet

This is a collection of Concrete5 cheat sheets, based on the C5 8+ source code. 

**Contributions are welcome via [issues](https://github.com/shahroq/whale_c5_cheat_sheet/issues) and [pull requests](https://github.com/shahroq/whale_c5_cheat_sheet/pulls).**

## Table of Contents
* [Pages (Collections)](#pages)
* [Files](#files)
* [Users](#users)
* [Single Pages](#single-pages)
* [Blocks](#blocks)
* [Stacks](#stacks)
* [Language](#language)
* [Constants](#constants)
* [Configs](#configs)
* [Helpers](#helpers)

## Pages (Collections)
### A page

#### Get Current page
```PHP
$page = \Page::getCurrentPage();
```
#### Get a page by a unique identifier
```PHP
$page = \Page::getByID(1); //by ID
$page = \Page::getByPath('/path/to/page'); //by path
```
#### Get page data
```PHP
echo $page->getCollectionName();
echo $page->getCollectionDescription();
echo $page->getCollectionDateAdded();
echo $page->getCollectionDatePublic();
echo $page->getCollectionUserID();
```

#### Get page type/template
```PHP
//Page Template
$pt = $page->getPageTemplateObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTemplateID(); //print($ptID);
    $ptName = $pt->getPageTemplateName(); //print($ptName);
    $ptHandle = $pt->getPageTemplateHandle(); //print($ptHandle);
}        

//Page Type (not working)
$pt = $page->getPageTypeObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTypeID(); //print($ptID);
    $ptName = $pt->getPageTypeName(); //print($ptName);
    $ptHandle = $pt->getPageTypeHandle(); //print($ptHandle);
}        
```

#### Get page attributes
```PHP
//attribute
$attr = $page->getAttribute('attribute_handle');

//Option List: get options
foreach ((object)$attr as $option) {
    $optionID = $option->getSelectAttributeOptionID(); //print($optionID);
    $optionValue = $option->getSelectAttributeOptionValue(); //print($optionValue);
}

//Image/File
if ($attr) {
    $attrURL = $attr->getURL(); //print($attrURL);
    $attrDownloadURL = $attr->getDownloadURL(); //print($attrDownloadURL);
    $attrForceDownloadURL = $attr->getForceDownloadURL(); //print($attrForceDownloadURL);
    $attrSize = $attr->getSize(); //print($attrSize);
    $attrExtension = $attr->getExtension(); //print($attrExtension);

    //image thumbnail
    $im = Core::make('helper/image');
    $thumb = $im->getThumbnail($attr, 100, 100)->src; //print_r($thumb);
}
```

#### Get list of attributes of a page
```PHP

```



### List of pages



## Files

## Users

## Attributes

### Get a Collection/Page attribute
```PHP
$attr = CollectionAttributeKey::getByID(1); //by ID
$attr = CollectionAttributeKey::getByHandle('attribute_handle'); //by handle

$attrID = $attr->getAttributeKeyID(); //print($attrID);
$attrHandle = $attr->getAttributeKeyHandle(); //print($attrHandle);
$attrName = $attr->getAttributeKeyName(); //print($attrName);
```

### Get options of an 'Option List' attribute
```PHP
$attr = CollectionAttributeKey::getByHandle('attribute_handle'); //by handle
$controller = $attr->getController();
$attrOptions = $controller->getOptions();
foreach ((object)$attrOptions as $attrOption) {
    $attrOptionID = $attrOption->getSelectAttributeOptionID(); //print($attrOptionID);
    $attrOptionValue = $attrOption->getSelectAttributeOptionValue(); //print($attrOptionValue);
}
```

### Attrubute Set
#### Get a set
```PHP
$attrSet = AttributeSet::getByID('attribute_set_id'); //by ID
$attrSet = AttributeSet::getByHandle('attribute_set_handle'); //by handle
```

#### Get attributes in a set
```PHP
$attrs = $attrSet->getAttributeKeys();
foreach($attrs as $attr) {
  	$attrID = $attr->getAttributeKeyID(); //print($attrID);
	$attrHandle = $attr->getAttributeKeyHandle(); //print($attrHandle);
	$attrName = $attr->getAttributeKeyName(); //print($attrName);
}
```
## Single Pages

## Blocks

## Stacks

## Language

## Constants

## Configs

## Helpers
