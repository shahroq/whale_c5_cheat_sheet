# [concrete5](https://www.concrete5.org) Cheat Sheet V8+

This is a collection of concrete5 cheat sheets, based on the C5 V8+ source code. 

**Contributions are welcome via [issues](https://github.com/shahroq/whale_c5_cheat_sheet/issues) and [pull requests](https://github.com/shahroq/whale_c5_cheat_sheet/pulls).**

## Table of Contents <!-- omit in toc -->
- [Application (`$app`)](#application-app)
  - [`$app` in a controller](#app-in-a-controller)
  - [`$app` in a custom class](#app-in-a-custom-class)
  - [`$app` in other places](#app-in-other-places)
- [Superglobals](#superglobals)
  - [`$request` in a controller](#request-in-a-controller)
  - [`$request` in a custom class](#request-in-a-custom-class)
  - [`$request` in other places](#request-in-other-places)
- [Pages (Collections)](#pages-collections)
  - [A page](#a-page)
    - [Get Current page](#get-current-page)
    - [Get a page by a unique identifier](#get-a-page-by-a-unique-identifier)
    - [Get a page data](#get-a-page-data)
    - [Get a page type/template](#get-a-page-typetemplate)
    - [Get a page attribute](#get-a-page-attribute)
    - [Get list of attributes of a page](#get-list-of-attributes-of-a-page)
    - [Checking if a page is in Edit Mode](#checking-if-a-page-is-in-edit-mode)
    - [Get all Blocks Objects on a page](#get-all-blocks-objects-on-a-page)
    - [Get an Area Object on a Page](#get-an-area-object-on-a-page)
  - [List of pages](#list-of-pages)
    - [Get list of pages](#get-list-of-pages)
    - [Get list of pages with pagination](#get-list-of-pages-with-pagination)
    - [Filter a page list](#filter-a-page-list)
    - [Sort a page list](#sort-a-page-list)
  - [Page operations](#page-operations)
    - [Add a page](#add-a-page)
    - [Update a page](#update-a-page)
    - [Delete a page](#delete-a-page)
    - [Move a page](#move-a-page)
    - [Copy a Page](#copy-a-page)
    - [Add an extra location URL](#add-an-extra-location-url)
    - [Set/Update an attribute of a page](#setupdate-an-attribute-of-a-page)
    - [Clear an attribute of a page](#clear-an-attribute-of-a-page)
    - [Refresh page cache](#refresh-page-cache)
  - [Attributes](#attributes)
    - [Get an attribute](#get-an-attribute)
    - [Add an attribute](#add-an-attribute)
    - [Delete an attribute](#delete-an-attribute)
    - [Get all attribute keys](#get-all-attribute-keys)
  - [Attribute Sets](#attribute-sets)
    - [Get an attribute set](#get-an-attribute-set)
    - [Get an attribute set data](#get-an-attribute-set-data)
    - [Add an attribute set](#add-an-attribute-set)
  - [Page Types](#page-types)
    - [Get a page type](#get-a-page-type)
    - [Add a page type](#add-a-page-type)
    - [Update a page type](#update-a-page-type)
  - [Page Templates](#page-templates)
    - [Get a page template](#get-a-page-template)
    - [Add a page template](#add-a-page-template)
  - [Single Page](#single-page)
    - [Get a single page](#get-a-single-page)
    - [Add a single page](#add-a-single-page)
- [Files](#files)
  - [A Files](#a-files)
    - [Get a file by a unique identifier](#get-a-file-by-a-unique-identifier)
    - [Get a file data](#get-a-file-data)
    - [Get a file attribute](#get-a-file-attribute)
    - [Get list of attributes of a file](#get-list-of-attributes-of-a-file)
  - [List of files](#list-of-files)
    - [Get list of files](#get-list-of-files)
    - [Get list of files with pagination](#get-list-of-files-with-pagination)
    - [Filter a file list](#filter-a-file-list)
    - [Get files inside a folder](#get-files-inside-a-folder)
    - [Sort a file list](#sort-a-file-list)
    - [Get a file set](#get-a-file-set)
    - [Get a file folder](#get-a-file-folder)
  - [File Operation](#file-operation)
    - [Importing a file](#importing-a-file)
    - [Delete a file](#delete-a-file)
    - [Set/Update an attribute to a file](#setupdate-an-attribute-to-a-file)
    - [Clear an attribute of a file](#clear-an-attribute-of-a-file)
    - [Create a file set](#create-a-file-set)
    - [Add a file to a set](#add-a-file-to-a-set)
    - [Create a file folder](#create-a-file-folder)
    - [Add a file to a folder](#add-a-file-to-a-folder)
  - [Attributes](#attributes-1)
    - [Get an attribute](#get-an-attribute-1)
    - [Add an attribute](#add-an-attribute-1)
    - [Add an attribute set](#add-an-attribute-set-1)
- [Users](#users)
  - [A User](#a-user)
    - [Get/Check current user](#getcheck-current-user)
    - [Get a user by a unique identifier](#get-a-user-by-a-unique-identifier)
    - [Get a user data](#get-a-user-data)
    - [Get user info object](#get-user-info-object)
    - [Get user info data](#get-user-info-data)
    - [Get a user (info) attributes](#get-a-user-info-attributes)
  - [List of users](#list-of-users)
    - [Get list of users](#get-list-of-users)
    - [Get list of users with pagination](#get-list-of-users-with-pagination)
    - [Filter a user list](#filter-a-user-list)
    - [Sort a user list](#sort-a-user-list)
  - [User operation](#user-operation)
    - [Add a user](#add-a-user)
    - [Update a user](#update-a-user)
    - [Activate/Deactivate a user](#activatedeactivate-a-user)
    - [Delete a user](#delete-a-user)
    - [Set/Update an attribute to a user](#setupdate-an-attribute-to-a-user)
    - [Clear an attribute of a user](#clear-an-attribute-of-a-user)
  - [Attributes](#attributes-2)
    - [Get an attribute](#get-an-attribute-2)
    - [Add an attribute](#add-an-attribute-2)
    - [Add an attribute set](#add-an-attribute-set-2)
- [Topics](#topics)
    - [Schema](#schema)
    - [Get a Topic Tree](#get-a-topic-tree)
    - [List of Topic Trees](#list-of-topic-trees)
    - [Get children (Categories, Nodes) of a Topic Tree](#get-children-categories-nodes-of-a-topic-tree)
    - [Topic Tree operations](#topic-tree-operations)
    - [Get a Category/Node](#get-a-categorynode)
    - [Add a Category/Node](#add-a-categorynode)
- [Attributes](#attributes-3)
    - [List of attribute set categories (collection/user/file/site/event)](#list-of-attribute-set-categories-collectionuserfilesiteevent)
    - [List of sets in a category](#list-of-sets-in-a-category)
  - [Attrubute Set](#attrubute-set)
    - [A set](#a-set)
    - [Attributes in a set](#attributes-in-a-set)
    - [List of sets](#list-of-sets)
- [Themes](#themes)
  - [Page types](#page-types-1)
    - [Adding areas in a Page Template](#adding-areas-in-a-page-template)
    - [Embedding Blocks in a Page Template](#embedding-blocks-in-a-page-template)
- [Blocks](#blocks)
  - [A Block Type](#a-block-type)
    - [Get a Block Type](#get-a-block-type)
    - [Get a Block Type data](#get-a-block-type-data)
    - [Install a Block Type](#install-a-block-type)
  - [Working with Blocks](#working-with-blocks)
    - [Hard-coding a Block with Custom Template](#hard-coding-a-block-with-custom-template)
    - [get data of an instance of a Block](#get-data-of-an-instance-of-a-block)
- [Stacks](#stacks)
- [Packages](#packages)
  - [A Package](#a-package)
    - [Get a package](#get-a-package)
    - [Get a package data](#get-a-package-data)
    - [Check dependencies](#check-dependencies)
- [Express Entries](#express-entries)
  - [Express Entity](#express-entity)
    - [Create the entity](#create-the-entity)
    - [Adding Associations to the Object](#adding-associations-to-the-object)
    - [Create the Form](#create-the-form)
    - [Add attributes](#add-attributes)
  - [Express Entry](#express-entry)
    - [Get list of entries in an entity](#get-list-of-entries-in-an-entity)
    - [Get list of entries in an entity with pagination](#get-list-of-entries-in-an-entity-with-pagination)
    - [Filter a list of entries](#filter-a-list-of-entries)
    - [Sort a list of entries](#sort-a-list-of-entries)
    - [Create an entry](#create-an-entry)
    - [Update an entry](#update-an-entry)
    - [Delete an entry](#delete-an-entry)
- [Language](#language)
    - [Get active locale](#get-active-locale)
    - [Get all added locales](#get-all-added-locales)
- [Constants](#constants)
    - [Get all constants](#get-all-constants)
- [Configs](#configs)
  - [Basics](#basics)
    - [Key](#key)
    - [Value](#value)
  - [Different places for storing data](#different-places-for-storing-data)
    - [Database](#database)
    - [FileSystem](#filesystem)
  - [Different ways to read and write config values](#different-ways-to-read-and-write-config-values)
    - [1: Using a Package object](#1-using-a-package-object)
    - [2: Using a service provider](#2-using-a-service-provider)
    - [3: Using Config](#3-using-config)
- [Aliases](#aliases)
    - [List of all aliases](#list-of-all-aliases)
- [Helpers](#helpers)
    - [General](#general)
    - [Number helper](#number-helper)
    - [Text helper](#text-helper)
    - [URL helper](#url-helper)
    - [Array helper](#array-helper)
    - [Arrays validation helper](#arrays-validation-helper)
    - [Numbers validation helper](#numbers-validation-helper)
    - [Strings validation helper](#strings-validation-helper)
    - [JSON helper](#json-helper)
    - [Ajax helper](#ajax-helper)
    - [HTML helper](#html-helper)
    - [Navigation helper](#navigation-helper)
    - [Date helper](#date-helper)
    - [Form helper](#form-helper)
    - [Form (editor/richtext editor/Redactor) helper](#form-editorrichtext-editorredactor-helper)
    - [Form (color picker) helper](#form-color-picker-helper)
    - [Form (date/time) helper](#form-datetime-helper)
    - [Form (page selector) helper](#form-page-selector-helper)
    - [Form (user selector) helper](#form-user-selector-helper)
    - [Form (group selector) helper](#form-group-selector-helper)
    - [Form (rating) helper](#form-rating-helper)
    - [Form (attribute) helper](#form-attribute-helper)
    - [Form (typography) helper](#form-typography-helper)
    - [Concrete URL helper](#concrete-url-helper)
    - [Asset library (file manager) helper](#asset-library-file-manager-helper)
    - [Validation error helper](#validation-error-helper)
    - [User Interface helper](#user-interface-helper)
    - [Image helper](#image-helper)
    - [List of all helper](#list-of-all-helper)
- [System Operations](#system-operations)
  - [Database](#database-1)
    - [Current database](#current-database)
    - [Another database](#another-database)
  - [Misc.](#misc)
    - [URL](#url)
    - [Logging](#logging)
    - [Get environment](#get-environment)
    - [Clear site cache](#clear-site-cache)


## Application (`$app`)

### `$app` in a controller

```php
$app = $this->app;
```

### `$app` in a custom class

```php
/** @var \Concrete\Core\Application\Application */
protected $app;
public function __construct(\Concrete\Core\Application\Application $app)
{
    $this->app = $app;
}
public function myMethod()
{
    $app = $this->app;
}
```
(create instances of custom classes with `$app->make(\ClassName::class)`) 

### `$app` in other places

```php
$app = \Concrete\Core\Support\Facade\Application::getFacadeApplication();
```

Since concrete5 version 8.5.2, you can also use the `app()` global function:
```php
$app = app();
```

You can also use `app()` to create instances:

```php
$token = app('token');
// By default, $token is an instance of Concrete\Core\Validation\CSRF\Token
```

## Superglobals

Direct access to PHP superglobals (that is, `$_REQUEST`, `$_POST`, `$_GET`, `$_SERVER`, `$_FILES`) should be avoided: concrete5 have a nicer way to work with them with the `$request` instance.

- instead of `$_GET['key']`: use `$request->query->get('key', $default = null)`
- instead of `$_POST['key']`: use `$request->request->get('key', $default = null)`
- instead of `$_REQUEST['key']`: use `$request->get('key', $default = null)`
- instead of `$_SERVER['key']`: use `$request->server->get('key')`
- instead of `$_FILES['key']`: use `$request->files->get('key')`

For more options check `\concrete\vendor\symfony\http-foundation\ParameterBag.php` or [`here`](https://symfony.com/doc/current/components/http_foundation.html)

### `$request` in a controller

```php
$request = $this->request;
```

### `$request` in a custom class

```php
/** @var \Concrete\Core\Http\Request */
protected $request;
public function __construct(\Concrete\Core\Http\Request $request)
{
    $this->request = $request;
}
public function myMethod()
{
    $request = $this->request;
}
```
(create instances of custom classes with `$app->make(\ClassName::class)`) 


### `$request` in other places

```php
$request = $app->make(\Concrete\Core\Http\Request::class);
```


## Pages (Collections)


### A page


#### Get Current page
```PHP
$page = \Page::getCurrentPage();
```

#### Get a page by a unique identifier
```PHP
$page = \Page::getByID(1); // by ID
$page = \Page::getByPath('/path/to/page'); // by path
```

#### Get a page data
```PHP
echo $page->getCollectionID();
echo $page->getCollectionName();
echo $page->getCollectionDescription();
echo $page->getCollectionDateAdded();
//echo date('F jS, Y h:i:s  a', strtotime($page->getCollectionDateAdded())); // change format of the date
echo $page->getCollectionDatePublic(); // the date the current version was made public
echo $page->getVersionObject()->getVersionDateCreated(); // get last modified date
echo $page->getCollectionUserID();
//echo Page::getByID($page->getCollectionID(), 1)->getVersionObject()->getVersionAuthorUserName(); // get username of the original author

echo $page->getCollectionPath();
echo $page->getCollectionLink();
echo $page->getCollectionHandle();

echo $page->getCollectionParentID();
//echo Page::getByID($page->getCollectionParentID())->getCollectionName(); // get the parent name

echo $page->getCollectionTypeID();
echo $page->getCollectionTypeHandle();
echo $page->getCollectionTypeName();

echo $page->getPageTypeID();
echo $page->getPageTypeHandle();
echo $page->getPageTypeName();
echo $page->getPageTypeObject();

echo $page->getPageTemplateID();
echo $page->getPageTemplateHandle();
echo $page->getPageTemplateObject();

echo $page->isSystemPage();

// get all the page paths of this page
foreach ($page->getPagePaths() as $path) {
    echo $path->getPagePath();
    echo $path->getPagePathID();
    echo $path->isPagePathCanonical();
}
$page->getAdditionalPagePaths(); // get all the non-canonical page paths of this page
$page->addAdditionalPagePath($cPath, $commit = true); // add a non-canonical page path to the current page
$page->setCanonicalPagePath($cPath, $isAutoGenerated = false); // set the canonical page path for a page. (it Adds and Sets)
$page->clearPagePaths(); //clears all page paths for a page.

// check whether a page selected
if($page->isError()) ...

//\concrete\src\Page\Page.php
```

#### Get a page type/template
```PHP
// Page Template
$pt = $page->getPageTemplateObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTemplateID(); //echo $ptID;
    $ptName = $pt->getPageTemplateName(); //echo $ptName;
    $ptHandle = $pt->getPageTemplateHandle(); //echo $ptHandle;
}        

// Page Type
$pt = $page->getPageTypeObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTypeID(); //echo $ptID;
    $ptName = $pt->getPageTypeName(); //echo $ptName;
    $ptHandle = $pt->getPageTypeHandle(); //echo $ptHandle;
}        
```

#### Get a page attribute
```PHP
// Attribute
$attr = $page->getAttribute('attribute_handle');


// Image/File
$attr = $page->getAttribute('thumbnail');
if ($attr) {
    $attrTitle = $attr->getTitle(); //echo $attrTitle;
    $attrURL = $attr->getURL(); //echo $attrURL;
    $attrDownloadURL = $attr->getDownloadURL(); //echo $attrDownloadURL;
    $attrForceDownloadURL = $attr->getForceDownloadURL(); //echo $attrForceDownloadURL;
    $attrSize = $attr->getSize(); //echo $attrSize;
    $attrExtension = $attr->getExtension(); //echo $attrExtension;

    // image thumbnail
    $ih = $app->make('helper/image');
    $thumbSrc = $ih->getThumbnail($attr, 100, 100)->src; //echo $thumbSrc;
}


// Option List: get option(s):
// Single option: cast to `string`
$optionValue = (string) $attr;

// Multiple options: cast to `object` and iterate
foreach ((object) $attr as $option) {
    $optionValue = $option->getSelectAttributeOptionValue(); //echo $optionValue;
    // $optionID = $option->getSelectAttributeOptionID(); //echo $optionID;
}


// Topics
$topics = $page->getAttribute('attribute_handle');
foreach ((object) $topics as $topic) {
    echo $topic->getTreeNodeID(); 
    echo $topic->getTreeNodeName(); 
}    
```

#### Get list of attributes of a page
```PHP
// get a list of the attribute keys for which the page has values
$attrKeys = $page->getSetCollectionAttributes();
if (count($attrKeys)) {
    foreach ($attrKeys as $key) {
        //each $key is an instance of \Concrete\Core\Entity\Attribute\Key\Key
        echo $attrHandle = $key->getAttributeKeyHandle();
        echo $attrName = $key->getAttributeKeyName();
    }
}
```

#### Checking if a page is in Edit Mode
```PHP
if ($page->isEditMode()) {
    // ...
}
```

#### Get all Blocks Objects on a page
```PHP
$blocks = $page->getBlocks(); // all block on a page
$blocks = $page->getBlocks('Area name'); // all block on an area
foreach ($blocks as $block) {
    // ...
}
```

#### Get an Area Object on a Page
```PHP
$area = $c->getArea('Area name');
```

### List of pages


#### Get list of pages
```PHP
$pageList = new PageList();

$pages = $pageList->getResults();

//echo count($pages);
foreach ((array) $pages as $page) {
    echo $page->getCollectionID();
}
```

#### Get list of pages with pagination
```PHP
$pageList = new PageList();

$pagination = $pageList->getPagination();
$pagination->setMaxPerPage(5);
$pages = $pagination->getCurrentPageResults();

//echo count($pages);
foreach ((array) $pages as $page) {
    echo $page->getCollectionID() . '-' . $page->getCollectionName() . '<br/>';
}

// pagination buttons
echo $pagination->renderDefaultView(); // outputs HTML for Bootstrap 3

// pagination functions
$pagination->setCurrentPage(1);
//$pagination->setCurrentPage($_GET['ccm_paging_p'] ?? 1); // in case the result is not generated rightly based on the current page number
echo $pagination->getTotalResults(); // total number of results
echo $pagination->getTotalPages(); // total number of pages
echo $pagination->hasNextPage(); // to determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
```
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a page list
```PHP
$pageList->filter(false, 'p.cID IN ($cID1, $cID2)'); // by cIDs
// OR: $pageList->getQueryObject()->where('p.cID != 1');

$pageList->filterByName($cName); // by name
$pageList->filterByParentID($cParentID); // by parent ID
$pageList->filterByPath($cPath); // by path

$pageList->filterByCollectionTypeID($cTypeID); // by collection type ID
$pageList->filterByCollectionTypeHandle($cTypeHandle); // by collection type handle
$pageList->filterByPageTypeHandle(['blog_entry', 'press_release']); // by page typeS

$pageList->filterByKeywords('foobar'); // by keyword
$pageList->filterByFulltextKeywords('foobar'); // more advanced search by keyword

$pageList->filterByPageTypeID($ctID); // by a page type ID
$pageList->filterByPageTypeHandle('blog_entry'); // by a page type handle

$pageList->filterByUserID($uID); // by user ID
$pageList->filterByIsApproved($cvIsApproved); // by is approved
$pageList->filterByIsAlias($ia); // by alias

$pageList->filterByDateAdded($date, $comparison = '='); // by date added
$pageList->filterByPublicDate($date, $comparison = '='); // by public date
$pageList->filterByDateLastModified($date, $comparison = '='); // by last modified date
$pageList->filterByNumberOfChildren($num, $comparison = '>'); // by number of children
//$pageList->filterByPublicDate(date('Y-m-d H:i:s', $end), "<=");
//filterByAttribute('special_offer_end_date', date('Y-m-d H:i:s', $start), ">=");

// by attribute:
$pageList->filterByAttribute($column, $value, $comparison = '=');
// OR
$pageList->filterByAttributeHandle($value, $comparison = '='); // for 'attribute_handle' => filterByAttributeHandle/ 'is_featured' => filterByIsFeatured(true);

// by attribute: checkbox(boolean)
$pageList->filterByAttribute('attribute_handle', true);
$pageList->filterByAttribute('attribute_handle', false);

// by attribute: string (text/text area/email/URL, Phone NUmber, etc)
$pageList->filterByAttribute('attribute_handle', 'cat'); // equal to 'cat'
$pageList->filterByAttribute('attribute_handle', '%'.'cat'.'%', 'LIKE'); // has 'cat' anywhere in the string

// by attribute: number
$pageList->filterByAttribute('attribute_handle', 5); // equal to 5
$pageList->filterByAttribute('attribute_handle', 5, '>='); // greater than or equal to 5

// by attribute: date/time
$pageList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start)); // equal to $stat
$pageList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start), '>='); // greater than or equal to $start

// by attribute: option list
//$pageList->filterBySelectAttribute($akHandle, $value); // legacy. not working

// for filter based on a single option:
$pageList->filterByAttribute('attribute_handle', $value1);

// for filter based on multiple options: it seems not working properly for array with multiple options. use manual method instead.
$pageList->filterByAttribute('attribute_handle', array($value1, $value2)); 

// have either $value1 OR $value2 value
$pageList->getQueryObject()->where("ak_attribute_handle LIKE '%\n" . $value1 . "\n%'");
$pageList->getQueryObject()->orWhere("ak_attribute_handle LIKE '%\n" . $value2 . "\n%'");

// have both $value1 AND $value2 values
$pageList->getQueryObject()->where("ak_attribute_handle LIKE '%\n" . $value1 . "\n%'");
$pageList->getQueryObject()->andWhere("ak_attribute_handle LIKE '%\n" . $value2 . "\n%'");

// by attribute: topics
// first get nodes:
//use \Concrete\Core\Tree\Node\Node as TreeNode;
$topicNode1 = TreeNode::getByID(1);
$topicNode2 = TreeNode::getByID(2);

$pageList->filterByAttribute('attribute_handle', array($topicNode1, $topicNode2));
// OR send the nodeIDs directly
$pageList->filterByAttribute('attribute_handle', array(1,2));

// OR category
$topicCategory1 = TreeNode::getByID(1);
$pageList->filterByAttribute('attribute_handle', array($topicCategory1));
// OR send the nodeIDs directly
$pageList->filterByAttribute('attribute_handle', array(1));

//\concrete\src\Page\PageList.php
```

#### Sort a page list
```PHP
$pageList->sortByRelevance()

$pageList->sortByDisplayOrder();
$pageList->sortByDisplayOrderDescending()

$pageList->sortByCollectionIDAscending()

$pageList->sortByPublicDate();
$pageList->sortByPublicDateDescending();

$pageList->sortByName();
$pageList->sortByNameDescending();

$pageList->sortBy('ak_attribute_handle', 'desc'); // by an attribute: 'ak_' + attribute_handle

//\concrete\src\Page\PageList.php
```

### Page operations


#### Add a page
```PHP
//$parentPage = \Page::getByID(1);
$parentPage = \Page::getByPath('/blog');
$pageType = \PageType::getByHandle('blog_entry'); // dashboard/pages/types 
$pageTemplate = \PageTemplate::getByHandle('blog_entry'); // dashboard/pages/templates
$page = $parentPage->add(
    $pageType, 
    array(
        'cName' => 'Hello All!',
        'cDescription' => 'Just a quick blog post.',
        'cHandle ' => 'hello-all',
        //'cDatePublic' => '2019-01-02 20:21:22',
        //'cDateCreated' => date('Y-m-d H:i:s'), // updates the posting date of the page to now
        //'pkgID ' => 1,
        //'uID ' => 1,
    ),
    $pageTemplate
);
```

#### Update a page
```PHP
$page->update(
    array(
        'cName' => 'My new page name',
        'cDescription' => 'My new page description', 
        //'cDatePublic' => '2019-01-02 20:21:22',
        //'cDateCreated' => date('Y-m-d H:i:s'),
        //'pkgID' => 1,
        //'uID' => 1,
        
        //'pTemplateID' => 1,
        //'cHandle' => 'new-handle',
        //'cCacheFullPageContent' => false,
        //'cCacheFullPageContentOverrideLifetime' => false,
        //'cCacheFullPageContentLifetimeCustom' => false,
    )    
);
// this should be run afterwards if the handle is changed
$page->rescanCollectionPath();
```

#### Delete a page
```PHP
$page->delete(); // delete it immediately
$page->moveToTrash(); // move to trash
```

#### Move a page
```PHP
$moveTo = \Page::getByPath('/archives');
$page->move($moveTo);
```

#### Copy a Page
```PHP
$copyTo = \Page::getByPath('/archives');
$page->duplicate($copyTo);
```

#### Add an extra location URL
```PHP
//$page = \Page::getByID(1);
$page = \Page::getByPath('/blog');
$page->addAdditionalPagePath('/blog-path-alternative');
```

#### Set/Update an attribute of a page
```PHP
$page = \Page::getByID(1); // by ID
$page->setAttribute('attribute_handle', 'value');

// multiple values (option list)
$page->setAttribute('attribute_handle', array('value1', 'value2'));

// multiple values (topics)
//use Concrete\Core\Entity\Attribute\Value\Value\TopicsValue;
//use Concrete\Core\Entity\Attribute\Value\Value\SelectedTopic;
$treeNodeIDs = [1, 2, 3];
$topicsValue = new TopicsValue();
foreach ($treeNodeIDs as $treeNodeID) {
  $topicsValueNode = new SelectedTopic();
  $topicsValueNode->setAttributeValue($topicsValue);
  $topicsValueNode->setTreeNodeID($treeNodeID);
  $topicsValue->getSelectedTopics()->add($topicsValueNode);
}
$page->setAttribute('attribute_handle', $topicsValue);
```

#### Clear an attribute of a page
```PHP
$page = \Page::getByID(1); // by ID
$page->clearAttribute('attribute_handle');
```

#### Refresh page cache
```PHP
$page = \Page::getByID(1); // by ID
$page->refreshCache();
```

### Attributes


#### Get an attribute
```PHP
$attr = CollectionAttributeKey::getByID(1); // by ID
$attr = CollectionAttributeKey::getByHandle('attr_handle'); // by handle

$attrID = $attr->getAttributeKeyID(); //echo $attrID;
$attrHandle = $attr->getAttributeKeyHandle(); //echo $attrHandle;
$attrName = $attr->getAttributeKeyName(); //echo $attrName;

// options of an 'Option List' attribute
$controller = $attr->getController();
$attrOptions = $controller->getOptions();
foreach ((object) $attrOptions as $attrOption) {
    $attrOptionID = $attrOption->getSelectAttributeOptionID(); //echo $attrOptionID;
    $attrOptionValue = $attrOption->getSelectAttributeOptionValue(); //echo $attrOptionValue;
}
```

#### Add an attribute
```PHP
//use Concrete\Core\Attribute\Type as AttributeType;
//use Concrete\Attribute\Select\Option as SelectAttributeTypeOption;

$attr = CollectionAttributeKey::getByHandle('attr_handle'); // by handle
if (!is_object($attr)) {
    $type = AttributeType::getByHandle('text'); 
    //$type = AttributeType::getByHandle('textarea');
    //$type = AttributeType::getByHandle('boolean'); // Checkbox 
    //$type = AttributeType::getByHandle('date_time'); 
    //$type = AttributeType::getByHandle('image_file');
    //$type = AttributeType::getByHandle('number'); 
    //$type = AttributeType::getByHandle('select'); // Option List
    //$type = AttributeType::getByHandle('telephone'); // Phone Number
    //$type = AttributeType::getByHandle('url'); 
    //$type = AttributeType::getByHandle('email'); 
    //$type = AttributeType::getByHandle('rating'); 
    //$type = AttributeType::getByHandle('topics'); 
    //$type = AttributeType::getByHandle('express'); // Express Entity
    //$type = AttributeType::getByHandle('calendar'); 
    //$type = AttributeType::getByHandle('calendar_event'); 
    //$type = AttributeType::getByHandle('page_selector'); 
    //$type = AttributeType::getByHandle('address'); // NOT available for collections
    //$type = AttributeType::getByHandle('social_links'); // NOT available for collections

    $args = array ( 
        'akHandle' => 'attr_handle',
        'akName'=> t('Attribute Name'),
        //'asID' => $asID, // attribute set ID: check 'Get a set/Create a set' on how to get $asID
        //'akIsSearchableIndexed' => true, // Content included in search index. Default: false
        //'akIsSearchable' => false, // Field available in advanced search. Default: true

        /** ATRIBUTE TYPES WITH SETTINGS: */

        /** text attribute (table: `atTextSettings`) */
        //'akTextPlaceholder' => 'placeholder', // Placeholder Text

        /** textarea attribute (table: `atTextareaSettings`) */
        //'akTextareaDisplayMode' => 'rich_text', // Input Format: 'text', 'rich_text'

        /** boolean attribute (table: `atBooleanSettings`) */
        //'akCheckedByDefault' => true, // default Value: true, false
        //'akCheckboxLabel'=> t('Attribute Label'), // Label

        /** date_time attribute (table: `atDateTimeSettings`) */
        //'akUseNowIfEmpty' => true, //Suggest the current date/time if empty: true, false
        //'akDateDisplayMode' => 'date_time', //Ask User For: 'date_time', 'date', 'date_text', 'text'
        //'akTextCustomFormat' => 'Y-m-d H:i:s', //Custom format: PHP date function values (https://www.php.net/manual/en/function.date.php)
        //'akTimeResolution' => 60, //Time Resolution: 1, 5, 10, 15, 30, 60, 300, 600, 900, 1800, 3600, 10800, 14400, 21600, 43200

        /** image_file attribute (table: `atFileSettings`) */
        //'akFileManagerMode' => 0, // Input Format: 0 (File Manager Selector), 5 (HTML Input)

        /** select attribute (table: `atSelectSettings`) */
        //'akSelectAllowMultipleValues' => false, // Multiple Values: true, false
        //'akDisplayMultipleValuesOnSelect' => false, // Single Value: true, false
        //'akHideNoneOption' => false, // Hide None Option: true, false
        //'akSelectAllowOtherValues' => false, // User Submissions: true, false
        //'akSelectOptionDisplayOrder' => 'display_asc', // Option Order: 'display_asc', 'alpha_asc', 'popularity_desc'
        /** Adding Options: check below this code block */

        /** topic attribute (table: `atTopicSettings`) */
        //'topicTreeID' => $topicTreeID, // Topic Tree: find id here: /index.php/dashboard/system/attributes/topics OR in the table: `TopicTrees`
        //'akTopicParentNodeID' => $topicParentNodeID, // Topic Default Parent Node: find id in the table: `TreeNodes`
        //'akTopicAllowMultipleValues' => true, // Allow multiple nodes to be chosen: true, false

        /** express entity attribute (table: `atExpressSettings`) */
        //'exEntityID' => $entityID, // Entity: find id in the table: `ExpressEntities`

        /** address attribute (table: `atAddressSettings`) */
        //'akDefaultCountry ' => '', // Available Countries
        //'akHasCustomCountries ' => '', // Default Country
        //'customCountries ' => '', 
        //'akGeolocateCountry ' => '', // Suggest the Country from the user IP address: true, false
    );
    $attr = CollectionAttributeKey::add($type, $args, $pkg = null);

    // add options to the 'option list' attribute
    //$attrOption = SelectAttributeTypeOption::add($attr, 'Option 1'); //add options
    //$attrOption = SelectAttributeTypeOption::add($attr, 'Option 2'); //"
}
```

#### Delete an attribute
```PHP
...

// delete options of an 'option list' attribute
...
```

#### Get all attribute keys
```PHP
$pageCategory = $this->app->make(\Concrete\Core\Attribute\Category\PageCategory::class);
$attributes = $pageCategory->getList();

foreach ($attributes as $attr) {
    $attrID = $attr->getAttributeKeyID(); //echo $attrID;
    $attrHandle = $attr->getAttributeKeyHandle(); //echo $attrHandle;
    $attrName = $attr->getAttributeKeyName(); //echo $attrName;
}
```

### Attribute Sets


#### Get an attribute set
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;
$as = AttributeSet::getByHandle('my_set');
```

#### Get an attribute set data
```PHP
$asID = $as->getAttributeSetID(); //echo $asID;
$asHandle = $as->getAttributeSetHandle(); //echo $asHandle;
$asName = $as->getAttributeSetName(); //echo $asName;
```

#### Add an attribute set
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;

$akc = AttributeKeyCategory::getByHandle('collection');
$akc->setAllowAttributeSets(AttributeKeyCategory::ASET_ALLOW_SINGLE);
$as = $akc->addSet('my_set', t('My Set'), $pkg = null, $locked = null); 
```


### Page Types


#### Get a page type
```PHP
$newsItem = PageType::getByHandle('news_item');
```

#### Add a page type
```PHP
// get a page template
$leftSide = PageTemplate::getByHandle('left_sidebar');

$newsItem = PageType::getByHandle('news_item');
if (!is_object($newsItem)) {
    $newsItem = PageType::add(
        array(
            'handle' => 'news_item',
            'name' => 'News Item', // note: it does not appear you can pass the t() function in the name
            'defaultTemplate' => $leftSide, // optional item, but wise to add
            'allowedTemplates' => 'C', // A is all, C is selected only, X is not selected only, all referring to the next key, defaults to A if key is not included
            'templates' => array($leftSide), // so, in this case, with C above, ONLY left sidebar can be used
            'ptLaunchInComposer' => false, // optional, defaults to false, but good to know the key in case it needs to be true
            'ptIsFrequentlyAdded' => true // optional, defaults to false, and whether or not it shows up in the add page type frequent list
        ),
        $pkg = null // this would come from the install or upgrade function usually
    );
}
```

#### Update a page type
check [`here`](#update-a-page)

### Page Templates


#### Get a page template
```PHP
$pt = PageTemplate::getByHandle('three_column');
```

#### Add a page template
```PHP
$pt = PageTemplate::getByHandle('three_column');
if(! $pt) {
    PageTemplate::add('three_column', t('Three Column'), 'three_column.png', $pkg = null);
}
```


### Single Page


#### Get a single page
```PHP
$sp = Page::getByPath('/dashboard/pages/my_page');
```

#### Add a single page
```PHP
$sp = Page::getByPath('/dashboard/pages/my_page');
if (! is_object($sp) || $sp->isError()) {
    $sp = SinglePage::add('/dashboard/pages/my_page', $pkg = null, $moveToRoot = false);
    $sp->update(array(
        'cName'=>'My Page', 
        'cDescription'=>'My Page Description'
    ));
}
```


## Files



### A Files


#### Get a file by a unique identifier
```PHP
$file = \File::getByID(1); // by ID
```

#### Get a file data
```PHP
echo $file->getFileID(); // file ID
echo $file->getFileName(); // file name

echo $file->getURL(); // direct url
echo $file->getDownloadURL(); // tracked url
echo $file->getRelativePath();
echo $_SERVER['DOCUMENT_ROOT'] . $file->getRelativePath();

echo $file->getTitle();
echo $file->getDescription();
echo $file->getTags(); // string
print_r($file->getTagsList()); // array

echo $file->getSize();
echo $file->getFullSize();
echo $file->getExtension();
echo $file->getType();
echo $file->getMimeType();
echo $file->getDisplayType();
echo $file->getGenericTypeText();

echo $file->getAttribute('width');
echo $file->getAttribute('height');
echo $file->getAttribute('duration');

// file version
$fileVersion = $file->getApprovedVersion();
```

#### Get a file attribute
```PHP
echo $file->getAttribute('width');
```

#### Get list of attributes of a file
```PHP
// first get the approved version of the file
$version = $file->getApprovedVersion();
$attrValues = $version->getAttributes();

if (count($attrValues)) {
    foreach ($attrValues as $value) {
        $key = $value->getAttributeKey();
        
        echo $attrHandle = $key->getAttributeKeyHandle();
        echo $attrName = $key->getAttributeKeyName();
    }
}
```

### List of files


#### Get list of files
```PHP
$fileList = new FileList();

$files = $fileList->getResults();

//echo count($files);
foreach ((array) $files as $file) {
    echo $file->getFileID();
}
```

#### Get list of files with pagination
```PHP
$fileList = new FileList();

$pagination = $fileList->getPagination();
// $pagination->setMaxPerPage(5); // change default max per page value (10)
$files = $pagination->getCurrentPageResults();

//echo count($files);
foreach ((array) $files as $file) {
    echo $file->getFileID().'-'.$file->getFileName().'<br/>';
}
```
For Pagination buttons & functions check [`here`](#Get-list-of-pages-with-pagination)  
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a file list
```PHP
$FileList->filterByType(\Concrete\Core\File\Type\Type::T_IMAGE); // by type (T_IMAGE, T_TEXT, T_AUDIO, T_DOCUMENT, T_APPLICATION, T_UNKNOWN)
$FileList->filterByExtension('png'); // by extension
$FileList->filterByKeywords('foobar'); // by keywords
$FileList->filterBySize(1024, 2048); // only includes files that are between 1MB and 2MB in Size
$FileList->filterByAttribute('width', 200, '>='); // only include files where "width" is 200 or greater.
$FileList->filterByDateAdded($date, $comparison = '='); // by date added
$FileList->filterByTags($tags); // by tags

//SET
if ($fileSet) $FileList->filterBySet($fileSet); // by set (check 'Get a file set' for how to get a set)
$FileList->filterByNoSet(); // files in No Sets
```

#### Get files inside a folder
```PHP
//use Concrete\Core\Tree\Node\Type\FileFolder;
//use Concrete\Core\File\FolderItemList;

$fileFolder = FileFolder::getNodeByName('Folder Name');
$fileList = new FolderItemList();
if ($fileFolder) { 
    $fileList->filterByParentFolder($fileFolder);
    $files = $fileList->getResults();
}	

//echo count($files);
foreach ((array) $files as $file) {
    $file = $file->getTreeNodeFileObject();
    echo $file->getFileID();
}
```

#### Sort a file list
```PHP
$FileList->sortByFilenameAscending();
$FileList->sortByFileSetDisplayOrder();
```

#### Get a file set
```PHP
$fileSet = FileSet::getByID(1); // by ID
$fileSet = FileSet::getByName('File Set Name'); // name
```

#### Get a file folder
```PHP
$folder = Node::getByID($folderID); // by ID
$folder = Node::getNodeByName('My Folder'); // by name, not working
```

### File Operation


#### Importing a file
```PHP
$filePath = 'path/to/file/filename.jpg';
if (file_exists($filePath)) {
    $importer = new \Concrete\Core\File\Importer();
    $fileVersion = $importer->import($filePath, false); //echo get_class($fileVersion); //file version object
    $file = $fileVersion->getFile(); //echo get_class($file); //file object
}	
```

#### Delete a file
```PHP
$file = File::getByID(1);
$file->delete();
```

#### Set/Update an attribute to a file
```PHP
$file = File::getByID(1);
$file->setAttribute('attribute_handle', 'value');
```

#### Clear an attribute of a file
```PHP
$file = File::getByID(1);
$file->clearAttribute('attribute_handle');
```

#### Create a file set
```PHP
$fileSet = FileSet::createAndGetSet('My File Set', FileSet::TYPE_PUBLIC);
```

#### Add a file to a set
```PHP    
$file = \File::getByID(1); // by ID
$fileSet->addFileToSet($file);
```

#### Create a file folder
```PHP
//use Concrete\Core\File\Filesystem;

$filesystem = new Filesystem();
$folder = $filesystem->getRootFolder();
$folderName = 'My Folder - '.time();
$folder = $filesystem->addFolder($folder, $folderName);	
```

#### Add a file to a folder
```PHP    
$file = \File::getByID(1); // by ID
$fileNode = $file->getFileNodeObject();
if (is_object($fileNode)) $fileNode->move($folder);    
```

### Attributes


#### Get an attribute
Same as [`Collections`](#get-an-attribute). Just replace 'Collection' with 'File'.

#### Add an attribute
Same as [`Collections`](#add-an-attribute). Just replace 'Collection' with 'File'.

#### Add an attribute set
Same as [`Collections`](#add-an-attribute-set). Just replace 'Collection' with 'File'.

## Users



### A User

#### Get/Check current user
```PHP
$u = $app->make(\Concrete\Core\User\User::class);

if ($u->isRegistered()) {
    print 'User is logged in.';
}

if ($u->isSuperUser()) {
    print 'Yes, they are SuperUser!';
}

print $u->getUserID();

$groups = $u->getUserGroupObjects(); 
foreach($groups as $group) {
    print $group->getGroupID();
    print $group->getGroupName();
}
```

#### Get a user by a unique identifier
```PHP
$user = User::getByUserID(1); // by ID
//User::getByUserID(3, true); //now user 3 is logged in.
```



#### Get a user data
```PHP
$userGroups = $user->getUserGroups(); //print_r($userGroups);
$userIsActive = $user->isActive(); //print_r($userIsActive);
$userIsSuperUser = $user->isSuperUser(); //print_r($userIsSuperUser);
$userLastOnline = $user->getLastOnline(); //print_r(date('Y-m-d H:i:s', $userLastOnline));
$userUserName = $user->getUserName(); //print_r($userUserName);
$userIsRegistered = $user->isRegistered(); //print_r($userIsRegistered);
$userUserID = $user->getUserID(); //print_r($userUserID);
$userTimezone = $user->getUserTimezone(); //print_r($userTimezone);
```

#### Get user info object
```PHP
$ui = UserInfo::getByID(1); // by ID
$ui = UserInfo::getByUserName('admin'); // by username
$ui = UserInfo::getByEmail('jane@concrete5.org'); // by email
```

#### Get user info data
```PHP
$uiIsActive = $ui->isActive(); //echo $uiIsActive;
$uiUserName = $ui->getUserName(); //echo $uiUserName;
$uiEmail = $ui->getUserEmail(); //echo $uiEmail;
$uiNumLogins = $ui->getNumLogins(); //echo $uiNumLogins;
$uiLastIPAddress = $ui->getLastIPAddress(); //echo $uiLastIPAddress;
$uiLastLogin = $ui->getLastLogin(); //echo date('Y-m-d H:i:s', $uiLastLogin);
$uiPreviousLogin = $ui->getPreviousLogin(); //echo date('Y-m-d H:i:s', $uiPreviousLogin);
$uiPublicProfileUrl = $ui->getUserPublicProfileUrl(); //echo $uiPublicProfileUrl;
$uiHasAvatar = $ui->hasAvatar(); //echo $uiHasAvatar;
$uiAvatar = $ui->getUserAvatar(); //echo $uiAvatar->getPath();
```

#### Get a user (info) attributes
```PHP
$uiAttr = $ui->getAttribute('attribute_handle'); //echo $uiAttr;
```

### List of users


#### Get list of users
```PHP
$userList = new UserList();

$users = $userList->getResults();

//echo count($users);
foreach ((array) $users as $user) {
    echo $user->getUserID();
}
```

#### Get list of users with pagination
```PHP
$userList = new UserList();

$pagination = $userList->getPagination();
$pagination->setMaxPerPage(5);
$users = $pagination->getCurrentPageResults();

//echo count($users);
foreach ((array) $users as $user) {
    echo $user->getUserID().'-'.$user->getUserName().'<br/>';
}
```
For Pagination buttons & functions check [`here`](#Get-list-of-pages-with-pagination)  
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a user list
```PHP
$userList->filter(false, 'u.uID IN ($uID1, $uID2)'); // by uIDs
$userList->filterByUsername('foobar'); // by username
$userList->filterByFuzzyUsername('foobar'); // by username(fuzzy)
$userList->filterByKeywords('andrew'); // by keywords (simple)
$userList->filterByFulltextKeywords('foobar'); // by keywords (advanced)
$userList->filterByDateAdded($date, $comparison = '='); // by date added
$userList->includeInactiveUsers();
$userList->includeUnvalidatedUsers();
$userList->filterByIsActive($isActive);
$userList->filterByIsValidated($isValidated);

// by group
$userList->filterByGroup('Administrators'); 
// OR send the group object
$group = \Group::getByName('Administrators');
$userList->filterByGroup($group);

$group = \Group::getByName('Administrators');
$userList->filterByGroup($group, false); // return all non-admins

$userList->filterByInAnyGroup($groups, $inGroups = true) // multiple group


// by attribute:
$userList->filterByAttribute($column, $value, $comparison = '=');
// OR
$userList->filterByAttributeHandle($value, $comparison = '='); // for 'attribute_handle' => filterByAttributeHandle/ 'is_featured' => filterByIsFeatured(true);

// by attribute: checkbox(boolean)
$userList->filterByAttribute('attribute_handle', true);
$userList->filterByAttribute('attribute_handle', false);

// by attribute: string (text/text area/email/URL, Phone NUmber, etc)
$userList->filterByAttribute('attribute_handle', 'cat'); // equal to 'cat'
$userList->filterByAttribute('attribute_handle', '%'.'cat'.'%', 'LIKE'); // has 'cat' anywhere in the string

// by attribute: number
$userList->filterByAttribute('attribute_handle', 5); // equal to 5
$userList->filterByAttribute('attribute_handle', 5, '>='); // greater than or equal to 5

// by attribute: date/time
$userList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start)); // equal to $stat
$userList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start), '>='); // greater than or equal to $start

// by attribute: option list
//$userList->filterBySelectAttribute($akHandle, $value); //legacy. not working

// for filtering based on a single option:
$userList->filterByAttribute('attribute_handle', $value1);

// for filtering based on multiple options: It seems not working properly for array with multiple options. use manual method instead.
$userList->filterByAttribute('attribute_handle', array($value1, $value2)); 

// have either $value1 OR $value2 value
$userList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$userList->getQueryObject()->orWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

// have both $value1 AND $value2 values
$userList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$userList->getQueryObject()->andWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

// by attribute: topics
// first get nodes
//use \Concrete\Core\Tree\Node\Node as TreeNode;
$topicNode1 = TreeNode::getByID(1);
$topicNode2 = TreeNode::getByID(2);

$userList->filterByAttribute('attribute_handle', array($topicNode1, $topicNode2));

// OR: Category
$topicCategory1 = TreeNode::getByID(1);
$userList->filterByAttribute('attribute_handle', array($topicCategory1));

```

#### Sort a user list
```PHP
$userList->sortByUserID(); // by ID asc
$userList->sortByUserName(); // by username asc
$userList->sortByDateAdded(); // by date added desc

$userList->sortBy('u.uID', 'desc'); // by ID desc
$userList->sortBy('u.uName', 'asc'); // by username desc
$userList->sortBy('u.uDateAdded', 'asc'); // by date added asc

$userList->sortBy('ak_attribute_handle', 'desc'); // by an attribute: 'ak_' + attribute_handle
```

### User operation


#### Add a user
```PHP
$ui = \UserInfo::add(array(
    'uName' => 'andrew',
    'uEmail' => 'andrew@concrete5.org', 
    'uPassword' => 'kittens',
    //'uDefaultLanguage' => '', // an ISO language code for the user's default language
    //'uIsValidated' => '', // whether the user is validated. 1 for validated, 0 for definitely unvalidated, and -1 for unknown (which is the default on sites that don't employ user validation
));
```

#### Update a user
```PHP
$ui = \UserInfo::getByID(10);
if ($ui) {
    $ui->update(array(
        //'uName' => 'andrew',
        //'uEmail' => 'new@email.com',
        //'uPassword' => 'kittens',
        //'uDefaultLanguage' => ''
        //'uIsValidated' => '',
        //'uTimezone' => 'America/Los_Angeles'
        //'uHasAvatar' => '',
        //'uPasswordConfirm' => '',
    ));
}

// change password
$ui = \UserInfo::getByID(10);
if ($ui) {
    $ui->update(array(
        'uPassword' => 'newpass', 
        'uPasswordConfirm' => 'newpass']
    ));
}
```

#### Activate/Deactivate a user
```PHP
$ui = \UserInfo::getByID(20);
if ($ui) {
    $ui->deactivate();
    $ui->activate();
}    
```

#### Delete a user
```PHP
$ui = \UserInfo::getByID(10);
if ($ui) {
    $ui->delete();
}
```

#### Set/Update an attribute to a user
```PHP
$ui = UserInfo::getByID(1); // by ID
if ($ui) {
    $ui->setAttribute('attribute_handle', 'value');
}    
```

#### Clear an attribute of a user
```PHP
$ui = UserInfo::getByID(1); // by ID
if ($ui) {
    $ui->clearAttribute('attribute_handle');
}    
```

### Attributes


#### Get an attribute
Same as [`Collections`](#get-an-attribute). Just replace 'Collection' with 'User'.

#### Add an attribute
Same as [`Collections`](#add-an-attribute). Just replace 'Collection' with 'User'.

#### Add an attribute set
Same as [`Collections`](#add-an-attribute-set). Just replace 'Collection' with 'User'.

## Topics



#### Schema
- Topic Tree
    - Category
        - Topic (Node)

#### Get a Topic Tree 
```PHP
//use \Concrete\Core\Tree\Type\Topic as TopicTree;

$topicTree = TopicTree::getByID(1); // by ID
$topicTree = TopicTree::getByName('Blog Entries'); // by name

if ($topicTree) echo $topicTree->getTreeName();
```

#### List of Topic Trees
```PHP
//use \Concrete\Core\Tree\Type\Topic as TopicTree;

$topicTrees = TopicTree::getList();
foreach ($topicTrees as $key => $topicTree) {
    echo $topicTree->treeID;
    echo $topicTree->topicTreeName;
    echo $topicTree->treeDateAdded;
    echo $topicTree->rootTreeNodeID;
}
```

#### Get children (Categories, Nodes) of a Topic Tree
```PHP
//use \Concrete\Core\Tree\Type\Topic as TopicTree;

$root = $topicTree->getRootTreeNodeObject();
$root->populateChildren();
$children = $root->getChildNodes();
//print_r($children);
```

#### Topic Tree operations
```PHP
//use \Concrete\Core\Tree\Type\Topic as TopicTree;

//add a Topic Tree
$topicTree = TopicTree::add('Topic Tree Name');

//rename a Topic Tree
$topicTree->setTopicTreeName('New Topic Tree Name');
```

#### Get a Category/Node
```PHP
//use \Concrete\Core\Tree\Node\Node as TreeNode;

// Category
$topicCategory = TreeNode::getByID($catID);
$topicCategory = TreeNode::getNodeByName($catName); // not working (error)

// Topic (Node)
$topicNode = TreeNode::getByID($nodeID);
$topicNode = TreeNode::getNodeByName($nodeName); // not working (error)
```

#### Add a Category/Node
```PHP
//use Concrete\Core\Tree\Type\Topic as TopicTree;
//use Concrete\Core\Tree\Node\Node as TreeNode;
//use Concrete\Core\Tree\Node\Type\Topic as TopicTreeNode;
//use Concrete\Core\Attribute\Key\Category;

// get root Category
$topicCategory = TreeNode::getByID($topicTree->getRootTreeNodeObject()->treeNodeID);
// OR: Get anotehr category by its handle
// from https://documentation.concrete5.org/developers/topics/working-topics -> not working (error)
$topicCategory = new Category();
$topicCategory->getByHandle('Another Category');
// OR:
$topicCategory = TreeNode::getByID($catID);
$topicCategory = TreeNode::getNodeByName($catName); //not working (error)

// add a new topic (node)
$topicNode = TopicTreeNode::add('New Node', $topicCategory);

// add a new category
$topicCategory->add('New Category below seected $topicCategory', $topicCategory);
```

## Attributes



#### List of attribute set categories (collection/user/file/site/event)
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;
$categories = AttributeKeyCategory::getList();		
foreach ((array) $categories as $category) {
    $categoryID = $category->getAttributeKeyCategoryID(); //echo $categoryID;
    $categoryHandle = $category->getAttributeKeyCategoryHandle(); //echo $categoryHandle;
}
```

#### List of sets in a category
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;
$categoryID = 1; 
$category = AttributeKeyCategory::getByID($categoryID);
if (is_object($category)) {
    $sets = $category->getController()->getSetManager()->getAttributeSets();
    foreach ((object) $sets as $set) {
        $setID = $set->getAttributeSetID(); //echo $setID);
        $setHandle = $set->getAttributeSetHandle(); //echo $setHandle;
        $setName = $set->getAttributeSetDisplayName(); //echo $setName;
    }
}	
```

### Attrubute Set


#### A set
```PHP
$as = AttributeSet::getByID('attribute_set_id'); // by ID
$as = AttributeSet::getByHandle('attribute_set_handle'); // by handle
```

#### Attributes in a set
```PHP
$attrs = $as->getAttributeKeys();
foreach($attrs as $attr) {
    $attrID = $attr->getAttributeKeyID(); //echo $attrID;
    $attrHandle = $attr->getAttributeKeyHandle(); //echo $attrHandle;
    $attrName = $attr->getAttributeKeyName(); //echo $attrName;
}
```

#### List of sets
```PHP
```

## Themes



### Page types


#### Adding areas in a Page Template
```PHP
// regular area
$a = new Area("Main");
//$a->enableGridContainer(); //enable grid container in area
//$a->setAreaGridMaximumColumns(12);
//$a->setBlockWrapperStart('<div class="block-wrapper">'); //output content before each block
//$a->setBlockWrapperEnd('</div>'); //output content after each block
//if ($c->isEditMode()); //do something
//if ($a->getTotalBlocksInArea($c) > 0); //do something
$a->display($c);

// global area
$a = new GlobalArea("Main");
$a->display();
```

#### Embedding Blocks in a Page Template
```PHP
$bt = BlockType::getByHandle('block_handle');
$bt->controller->field1 = 'field1';
$bt->render(); //render default template: view.php
//$bt->render('templates/my_template'); //render specific template: my_template.php
```



## Blocks



### A Block Type


#### Get a Block Type
```PHP
$bt = BlockType::getByHandle('my_block');
//$bt = BlockType::getByID(1);
```

#### Get a Block Type data
```PHP
echo $bt->getBlockTypeID();
echo $bt->getBlockTypeName();
echo $bt->getBlockTypeDescription();
```

#### Install a Block Type
```PHP
$bt = BlockType::getByHandle('my_block');
if (!is_object($bt)) {
    BlockType::installBlockType('my_block', $pkg = null);
}
```

### Working with Blocks


#### Hard-coding a Block with Custom Template
```PHP
$bt = BlockType::getByHandle('block_type_handle'); // block_type_handle: autonav, tag, ...
$bt->controller->block_attribute_handle = 'some_attribute'; // block attribute handles can be retrieved by looking at the related table in database (e.g.: btNavigation, btTags)
// ...
$bt->render($view = 'view'); // $view: template name

// Sample code for autonav
$bt = BlockType::getByHandle('autonav');
$bt->controller->orderBy = 'display_asc';
$bt->controller->displayPages = 'top';
$bt->controller->displaySubPages = 'relevant_breadcrumb';
$bt->controller->displaySubPageLevels = 'all';
$bt->render('templates/breadcrumb');
```

#### get data of an instance of a Block
```PHP
//$blockObj = Block::getByID($bID);

// block general data
$bID = $blockObj->bID; //echo $bID;
$btHandle = $blockObj->btHandle; //echo $btHandle; 
$btID = $blockObj->btID; //echo $btID; // block type id
$bFileName = $blockObj->bFileName; //echo $bFileName; // template name

// block specific data
// get instance:
$blockIns = $blockObj->getInstance();
// get the data based on block type. propertirs of each block type can be identified by looking at the corresponding database table

// html block (`btContentLocal`)
$content = $blockIns->content; //echo $content;

// content block (`btContentLocal`)
$content = $blockIns->content; //echo $content;

// image block (`btContentImage`)
$fID = $blockIns->fID; //echo $fID;
$fOnstateID = $blockIns->fOnstateID; //echo $fOnstateID;
$cropImage = $blockIns->cropImage; //echo $cropImage;
//...

// autonav block (`btNavigation`)
$orderBy = $blockIns->orderBy; //echo $orderBy;
$displayPages  = $blockIns->displayPages ; //echo $displayPages ;
$displayPagesCID = $blockIns->displayPagesCID; //echo $displayPagesCID;
//...
```


## Stacks


## Packages


### A Package


#### Get a package
```PHP
$pkg = Package::getByHandle('theme_pixel');
//$pkg = Package::getByID(1);
```

#### Get a package data
```PHP
echo $pkg->getPackageID();
echo $pkg->getPackageHandle();
echo $pkg->getPackageName();
echo $pkg->getPackageDescription();
echo $pkg->getPackageVersion();
echo $pkg->getPackagePath();
print_r($pkg->getPackageDependencies()); 
```

#### Check dependencies
```PHP
$pkg_dependency  = Package::getByHandle('handle_dependency');
if (!is_object($pkg_dependency)){
    throw new Exception(t('Exception: Installation requires as a prerequisite that "X" Add-on is already installed.'));
}
```

## Express Entries



### Express Entity


#### Create the entity
```PHP
$eObj = Express::getObjectByHandle('marina');
if (!is_object($eObj)) {
    
    $eObj = Express::buildObject('marina', 'marinas', 'Marina', $pkg = null);

    /** general checkboxes (HELP WANTED) */
    //use Concrete\Core\Entity\Attribute\Key\Key;
    //'Content included in search index' checkbox 
    //akIsSearchableIndexed --> setIsAttributeKeyContentIndexed()
    //'Field available in advanced search' checkbox 
    //akIsSearchable--> setIsAttributeKeySearchable()

    /** settings */
    // text
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TextSettings();
    $settings->setPlaceholder('Enter Marina Name Here');
    $eObj->addAttribute('text', 'Name', 'marina_name', $settings);

    // textarea
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TextareaSettings();
    $settings->setMode('text'); //values: 'text', 'rich_text'
    $eObj->addAttribute('textarea', 'Description', 'marina_description', $settings);

    // checkbox
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\BooleanSettings();
    $settings->setIsCheckedByDefault(false);
    $settings->setCheckboxLabel('Checkbox Label');
    $eObj->addAttribute('boolean', 'Active', 'marina_active', $settings);

    // date_time
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\DateTimeSettings();
    $settings->setUseNowIfEmpty(false);
    $settings->setMode('date_time');
    $settings->setTextCustomFormat('Y-m-d H:i:s');
    $settings->setTimeResolution(60);
    $eObj->addAttribute('date_time', 'Establishment', 'marina_establishment', $settings);
    
    // image_file
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\ImageFileSettings();
    $settings->setModeToFileManager(); // OR $settings->setModeToHtmlInput();
    $eObj->addAttribute('image_file', 'Image', 'marina_image', $settings);

    // number
    $eObj->addAttribute('number', 'Size', 'marina_size');
    
    // select
    $eObj->addAttribute('select', 'Facilities', 'marina_facilities', $settings);
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\SelectSettings();
    $settings->setAllowMultipleValues(false);
    $settings->setDisplayMultipleValuesOnSelect(false);
    $settings->setHideNoneOption(false);
    $settings->setAllowOtherValues(false);
    $settings->setDisplayOrder('display_asc');
    
    // address
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\AddressSettings();
    $settings->setCustomCountries(array('US','UK'));
    $settings->setHasCustomCountries(true);
    $settings->setDefaultCountry('UK');
    $eObj->addAttribute('address', 'Address', 'marina_address', $settings);
    
    // telephone
    $eObj->addAttribute('telephone', 'Telephone', 'marina_telephone');
    
    // url
    $eObj->addAttribute('url', 'Website', 'marina_website');
    
    // email
    $eObj->addAttribute('email', 'Email', 'marina_email');
    
    // rating
    $eObj->addAttribute('rating', 'Rating', 'marina_rating');
    
    // topics
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TopicsSettings();
    $settings->setTopicTreeID($topicTreeID);
    $settings->setParentNodeID($topicParentNodeID);
    $settings->setAllowMultipleValues(true);
    $eObj->addAttribute('topics', 'District', 'marina_district', $settings);
    
    // social_links
    $eObj->addAttribute('social_links', 'twitter', 'marina_twitter');
    
    // express
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\ExpressSettings();
    $settings->setEntity($entityID);
    $eObj->addAttribute('express', 'Personnels', 'marina_personnels');
    
    // calendar
    $eObj->addAttribute('calendar', 'Calendar', 'marina_calendar');
    
    // calendar_event
    $eObj->addAttribute('calendar_event', 'Event', 'marina_event');
    
    // page_selector
    $eObj->addAttribute('page_selector', 'Info Page', 'marina_info_page');

    $eObj->save();

    // creating an Express Object Form
    $form = $eObj->buildForm('Form');
    $form->addFieldset('Basics')
        ->addAttributeKeyControl('marina_name')
        ->addAttributeKeyControl('marina_description')
        ->addAttributeKeyControl('marina_active') //...
        ->addTextControl('', 'This is just some basic explanatory text.')
        ->addAttributeKeyControl('marina_establishment') //...
        ;
    $form = $form->save();

}
```
For more info on each method and its possible values check [`HERE`](#Add-an-attribute).

#### Adding Associations to the Object
```PHP
$marina = Express::buildObject('marina', 'marinas', 'Marina', $pkg);
$boat = Express::buildObject('boat', 'boats', 'Boat', $pkg);

$builder = $marina->buildAssociation();
$builder->addOneToMany($boat);
$boat = $builder->save();
$marina = $marina->getEntity();
```

#### Create the Form
```PHP
```

#### Add attributes
```PHP
```

### Express Entry



#### Get list of entries in an entity
```PHP
//use Concrete\Core\Express\EntryList;
$entity = Express::getObjectByHandle('entity_handle');
$entryList = new EntryList($entity);
$entries = $entryList->getResults();

//echo count($entities);
foreach ($entries as $entry) {
    echo $entry->getId(); // internal ID
    echo $entry->getAttributeId();
    // OR: echo $entry->getAttribute('attribute_id');
    // OR: echo $entry->getAttributeValueObject('attribute_id');

    print_r($entry->getDateCreated());
    //print_r($entry->getDateCreated()->getTimestamp());
    //print_r($entry->getDateCreated()->format(DateTime::ATOM));
}
```

#### Get list of entries in an entity with pagination
```PHP
//use Concrete\Core\Express\EntryList;
$entity = Express::getObjectByHandle('entity_handle');
$entryList = new EntryList($entity);
$pagination = $entryList->getPagination();
$pagination->setMaxPerPage(5);
$entries = $pagination->getCurrentPageResults();

//echo count($entries);
foreach ($entries as $entry) {
    //
}
```
For Pagination buttons & functions check [`here`](#Get-list-of-pages-with-pagination)  
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a list of entries
```PHP
$entryList->filterByKeywords($keywords = ''); // not working?
$entryList->filterByAttributeHandle($keywords = ''); // not working?

//\concrete\src\Express\EntryList.php
```

#### Sort a list of entries
```PHP
$entryList->sortByDisplayOrderAscending();
$entryList->sortByAttributeHandle('desc'); // by an attribute: asc OR desc

//\concrete\src\Express\EntryList.php
```

#### Create an entry
```PHP
$entry = Express::buildEntry('entity_handle')
    ->setAttribute('attribute_handle', 'Andy')
    ->save();
```

#### Update an entry
```PHP
$entry->setAttribute('attribute_handle', 'Andy'); 
// OR: $entry->setAttributeHandle('Andy');

// if you were to immediately call getAttribute() later in the script, the attribute value in the object might not be updated. To combat this, use the refresh() method in the express Object manager:
//$entry = Express::refresh($entry);
```

#### Delete an entry
```PHP
// delete an entity
Express::deleteEntry($entry);

// delete all entries in an entity
//use Concrete\Core\Express\EntryList;
$entity = Express::getObjectByHandle('faq');
$entryList = new EntryList($entity);
$entries = $entryList->getResults();

foreach ($entries as $entry) {
    Express::deleteEntry($entry->getId());
}
```


## Language



#### Get active locale
```PHP
$activeLocale = \Localization::activeLocale();
echo $activeLocale; // `en_US`
```

#### Get all added locales
```PHP
$app = \Concrete\Core\Support\Facade\Application::getFacadeApplication();
$site = $app->make('site')->getActiveSiteForEditing();
$flag = $app->make(Concrete\Core\Multilingual\Service\UserInterface\Flag::class);

$locales = $site->getLocales(); //echo count($locales);
foreach ($locales as $locale) {
    echo $locale->getLocaleID(); 
    echo $locale->getLanguageText(); // `English`, `Spanish`
    echo $locale->getLocale(); // `en_US`, `es_ES`
    
    // get home page of each locale
    $localeSiteTree = $locale->getSiteTree();
    $home = $localeSiteTree === null ? null : $localeSiteTree->getSiteHomePageObject();
    if (is_object($home)) {
        echo $home->getCollectionLink();
        echo $home->getCollectionName();
    }

    // flag
    echo $flag->getLocaleFlagIcon($locale);
}
```

## Constants



#### Get all constants
```PHP
print_r(get_defined_constants($categorize = true));
```

## Configs



### Basics


#### Key
```PHP
configNamespace::configGroup.configItem
```
#### Value
```PHP
configValue
```

### Different places for storing data


#### Database
Databse Table: *`Config`*

| configNamespace | configGroup | configItem  | configValue |
| --------------- | ----------- | ----------- | ----------- |
| my_package      | front_end   | show_header | 1           |

#### FileSystem
File: *`application\config\generated_overrides\configNamespace\configGroup.php`*
```PHP
return array(
    'configItem' => true,
    'configItem2' => 2,
    'configItem3' => 'Hey!',
);
```

### Different ways to read and write config values


#### 1: Using a Package object
```PHP
$pkg = \Package::getByHandle('my_package');

/** Database */

// save config value
$pkg->getConfig()->save('front_end.show_header', true);
// get config value
$showHeader = $pkg->getConfig()->get('front_end.show_header');
// has config value?
$hasShowHeader = $pkg->getConfig()->has('front_end.show_header');
// set config value
//$pkg->getConfig()->set('front_end.show_header'); //not working
// clear config value
//$pkg->getConfig()->clear('front_end.show_header'); //not working


/** FileSystem */

// save config value
$pkg->getFileConfig()->save('front_end.show_header', true);
// get config value
$showHeader = $pkg->getFileConfig()->get('front_end.show_header');
// has config value?
$hasShowHeader = $pkg->getFileConfig()->has('front_end.show_header');
// set config value
//$pkg->getConfig()->set('front_end.show_header'); //not working
// clear config value
//$pkg->getConfig()->clear('front_end.show_header'); //not working
```

#### 2: Using a service provider
```PHP
$key = 'configNamespace::configGroup.configItem';
$value = '5';
$default = -1;

/** Database */
$configDatabase = \Core::make('config/database');
$configDatabase->save($key, $value);
$configDatabase->get($key, $default);
$configDatabase->has($key);
//$configDatabase->set($key, $value); // not working
//$configDatabase->clear($key); // not working

/**  FileSystem */
$configFile = \Core::make('config');
$configFile->save($key, $value);
$configFile->get($key, $default);
$configFile->has($key);
//$configFile->set($key, $value); // not working
//$configFile->clear($key); // not working
```

#### 3: Using Config
```PHP
$key = 'configNamespace::configGroup.configItem';
$value = '5';
$default = -1;

/** FileSystem */
\Config::save($key, $value);
\Config::get($key, $default);
\Config::has($key);
//\Config::set($key, $value); //not working
//\Config::clear($key); // not working
```

## Aliases



#### List of all aliases
```PHP
//\concrete/config/app.php

'Area' => '\Concrete\Core\Area\Area',
'Asset' => '\Concrete\Core\Asset\Asset',
'AssetList' => '\Concrete\Core\Asset\AssetList',
'AttributeSet' => '\Concrete\Core\Attribute\Set',
'AuthenticationType' => '\Concrete\Core\Authentication\AuthenticationType',
'Block' => '\Concrete\Core\Block\Block',
'BlockType' => '\Concrete\Core\Block\BlockType\BlockType',
'BlockTypeList' => '\Concrete\Core\Block\BlockType\BlockTypeList',
'BlockTypeSet' => '\Concrete\Core\Block\BlockType\Set',
'Cache' => '\Concrete\Core\Cache\Cache',
'Request' => '\Concrete\Core\Http\Request',
'CacheLocal' => '\Concrete\Core\Cache\CacheLocal',
'Collection' => '\Concrete\Core\Page\Collection\Collection',
'CollectionAttributeKey' => '\Concrete\Core\Attribute\Key\CollectionKey',
'CollectionVersion' => '\Concrete\Core\Page\Collection\Version\Version',
'ConcreteAuthenticationTypeController' => '\Concrete\Authentication\Concrete\Controller',
'Controller' => '\Concrete\Core\Controller\Controller',
'Conversation' => '\Concrete\Core\Conversation\Conversation',
'ConversationEditor' => '\Concrete\Core\Conversation\Editor\Editor',
'ConversationFlagType' => '\Concrete\Core\Conversation\FlagType\FlagType',
'ConversationMessage' => '\Concrete\Core\Conversation\Message\Message',
'ConversationRatingType' => '\Concrete\Core\Conversation\Rating\Type',
'Cookie' => '\Concrete\Core\Cookie\Cookie',
'Environment' => '\Concrete\Core\Foundation\Environment',
'FacebookAuthenticationTypeController' => '\Concrete\Authentication\Facebook\Controller',
'File' => '\Concrete\Core\File\File',
'FileAttributeKey' => '\Concrete\Core\Attribute\Key\FileKey',
'FileImporter' => '\Concrete\Core\File\Importer',
'FileList' => '\Concrete\Core\File\FileList',
'FilePermissions' => '\Concrete\Core\Legacy\FilePermissions',
'FileSet' => '\Concrete\Core\File\Set\Set',
'GlobalArea' => '\Concrete\Core\Area\GlobalArea',
'Group' => '\Concrete\Core\User\Group\Group',
'GroupList' => '\Concrete\Core\User\Group\GroupList',
'GroupSet' => '\Concrete\Core\User\Group\GroupSet',
'GroupSetList' => '\Concrete\Core\User\Group\GroupSetList',
'GroupTree' => '\Concrete\Core\Tree\Type\Group',
'GroupTreeNode' => '\Concrete\Core\Tree\Node\Type\Group',
'Job' => '\Concrete\Core\Job\Job',
'JobSet' => '\Concrete\Core\Job\Set',
'Loader' => '\Concrete\Core\Legacy\Loader',
'Localization' => '\Concrete\Core\Localization\Localization',
'Marketplace' => '\Concrete\Core\Marketplace\Marketplace',
'Package' => '\Concrete\Core\Package\Package',
'Page' => '\Concrete\Core\Page\Page',
'PageCache' => '\Concrete\Core\Cache\Page\PageCache',
'PageController' => '\Concrete\Core\Page\Controller\PageController',
'PageEditResponse' => '\Concrete\Core\Page\EditResponse',
'PageList' => '\Concrete\Core\Page\PageList',
'PageTemplate' => '\Concrete\Core\Page\Template',
'PageTheme' => '\Concrete\Core\Page\Theme\Theme',
'PageType' => '\Concrete\Core\Page\Type\Type',
'PermissionAccess' => '\Concrete\Core\Permission\Access\Access',
'PermissionKey' => '\Concrete\Core\Permission\Key\Key',
'PermissionKeyCategory' => '\Concrete\Core\Permission\Category',
'Permissions' => '\Concrete\Core\Permission\Checker',
'Queue' => '\Concrete\Core\Foundation\Queue\Queue',
'QueueableJob' => '\Concrete\Core\Job\QueueableJob',
'Redirect' => '\Concrete\Core\Routing\Redirect',
'RedirectResponse' => '\Concrete\Core\Routing\RedirectResponse',
'Response' => '\Concrete\Core\Http\Response',
'Router' => '\Concrete\Core\Routing\Router',
'SinglePage' => '\Concrete\Core\Page\Single',
'Stack' => '\Concrete\Core\Page\Stack\Stack',
'StackList' => '\Concrete\Core\Page\Stack\StackList',
'StartingPointPackage' => '\Concrete\Core\Package\StartingPointPackage',
'TaskPermission' => '\Concrete\Core\Legacy\TaskPermission',
'User' => '\Concrete\Core\User\User',
'UserAttributeKey' => '\Concrete\Core\Attribute\Key\UserKey',
'UserList' => '\Concrete\Core\User\UserList',
'View' => '\Concrete\Core\View\View',
'Workflow' => '\Concrete\Core\Workflow\Workflow',
```

## Helpers



#### General
```PHP
//\concrete\bootstrap\helpers.php

// Translate text (simple form).
t($text);

// Translate text (plural form).
t2($singular, $plural, $number);

//Translate text (simple form) with a context.
tc($context, $text);

// Security helper.
h($input);

// Returns $string in CamelCase.
camelcase($string, $leaveSlashes = false);

// Returns CamelCase string as camel_case.
uncamelcase($string);

// Fills an object properties from an array.
array_to_object($o, $array);

// Dumps information about a variable in a way that can be used with Doctrine recursive objects.).
var_dump_safe($o, $echo = true, $maxDepth = true);

// Generate the PHPDoc for a set of defined variables.
output_vars(array $get_defined_vars, $valueOfThis = null, $return = false);
```

#### Number helper
```PHP
$nh = $app->make('helper/number');

$nh->flexround($value); // Rounds the value only out to its most significant digit.
$nh->trim($value); // Remove superfluous zeroes from a string containing a number.
$nh->isNumber($string); // Checks if a given string is valid representation of a number in the current locale.
$nh->isInteger($string); // Checks if a given string is valid representation of an integer in the current locale.
$nh->format($number, $precision = null); // Format a number with grouped thousands and localized decimal point/thousands separator.
$nh->unformat($string, $trim = true, $precision = null); // Parses a localized number representation and returns the number (or null if $string is not a valid number representation).
$nh->formatSize($size, $forceUnit = ''); // Formats a size (measured in bytes, KB, MB, ...).
$nh->getBytes($val); // Nice and elegant function for converting memory. Thanks to @lightness races in orbit on Stackoverflow.

//\concrete\src\Utility\Service\Number.php
```

#### Text helper
```PHP
$th = $app->make('helper/text');

$th->encodePath($path); // URL-encodes collection path.
$th->match($pattern, $value); // Determine if a given string matches a given pattern.
$th->lugSafeString($handle, $maxlength = 128); // Remove unsafe characters for URL slug.
$th->sanitize($string, $max_length = 0, $allowed = ''); // Strips tags and optionally reduces string to specified length.
$th->email($email); // Leaves only characters that are valid in email addresses (RFC).
$th->alphanum($string); // Leaves only characters that are alpha-numeric.
$th->entities($v); // always use in place of htmlentites(), so it works with different languages.
$th->decodeEntities($v); // Decodes html-encoded entities (for instance: from '&gt;' to '>').
$th->specialchars($v); // A concrete5 specific version of htmlspecialchars(). Double encoding is OFF, and the character set is set to your site's.
$th->shorten($textStr, $numChars = 255, $tail = '…'); // An alias for shorten().
$th->shortText($textStr, $numChars = 255, $tail = '…'); // Like sanitize, but requiring a certain number characters, and assuming a tail.
$th->camelcase($string); // Takes a string and turns it into the CamelCase or StudlyCaps version.
$th->twitterAutolink($input, $newWindow = 0, $withSearch = 0); // automatically add hyperlinks to any twitter style @usernames in a string.
$th->makenice($input); // Runs a number of text functions, including autolink, nl2br, strip_tags. Assumes that you want simple text comments but with a few niceties.
$th->prettyStripTags($input, $allowedTags = null); // Runs strip_tags but ensures that spaces are kept between the stripped tags.
$th->autolink($input, $newWindow = false, $defaultProtocol = 'http://'); // Scans passed text and automatically hyperlinks any URL inside it.
$th->fnmatch($pattern, $string); // A wrapper for PHP's fnmatch() function, which some installations don't have.
$th->uncamelcase($string); // Takes a CamelCase string and turns it into camel_case.
$th->unhandle($string); // Takes a handle-based string like "blah_blah" or "blah-blah" or "blah/blah" and turns it into "Blah Blah".
$th->handle($handle, $leaveSlashes = false); // Takes a string and turns it into a handle.
$th->sanitizeFileSystem($handle); // Determines whether a string matches a particular pattern.
$th->urlify($handle, $max_length = null, $locale = '', $removeExcludedWords = true); // Takes text and returns it in the "lowercase-and-dashed-with-no-punctuation" format.
$th->asciify($text, $locale = ''); // Takes text and converts it to an ASCII-only string (characters with code between 32 and 127, plus \t, \n and \r).
$th->wordSafeShortText($textStr, $numChars = 255, $tail = '…'); // alias of shortenTextWord().
$th->shortenTextWord($textStr, $numChars = 255, $tail = '…'); // Shortens and sanitizes a string but only cuts at word boundaries.
$th->filterNonAlphaNum($val); // Strips out non-alpha-numeric characters.
$th->highlightSearch($value, $searchString); // Highlights a string within a string with the class ccm-highlight-search.
$th->formatXML($xml); //  Formats a passed XML string nicely.
$th->appendXML(\SimpleXMLElement $root, \SimpleXMLElement $new); // Appends a SimpleXMLElement to a SimpleXMLElement.

//\concrete\src\Utility\Service\Text.php
```

#### URL helper
```PHP
$uh = $app->make('helper/url');

$uh->setVariable($variable, $value = false, $url = false); //
$uh->unsetVariable($variable, $url = false); //
$uh->buildQuery($url, $params); //
$uh->shortenURL($strURL); //Shortens a given url with the tiny url api.

//\concrete\src\Utility\Service\Url.php
```

#### Array helper
```PHP
$ah = $app->make('helper/array');

$ah->get(array $array, $keys, $default = null); //Fetches a value from an (multidimensional) array.
$ah->set(array $array, $keys, $value); //Sets a value in an (multidimensional) array, creating the arrays recursivly.
$ah->parseKeys($keys); //Turns the string keys into an array of keys.
$ah->flatten(array $array); //Takes a multidimensional array and flattens it.
$ah->subset($a, $b); //Returns whether $a is a proper subset of $b.

//\concrete\src\Utility\Service\Array.php
```

#### Arrays validation helper
```PHP
$avh = $app->make('helper/validation/arrays');

$avh->containsString($needle, $haystack = array(), $recurse = true); //Returns true if any string in the "haystack" contains the "needle".

//\concrete\src\Utility\Service\Validation\Arrays.php
```

#### Numbers validation helper
```PHP
$nvh = $app->make('helper/validation/numbers');

$nvh->integer($data, $min = null, $max = null); //Tests whether the passed item is an integer.
$nvh->number($data, $min = null, $max = null); //Tests whether the passed item is an integer or a floating point number.

//\concrete\src\Utility\Service\Validation\Numbers.php
```

#### Strings validation helper
```PHP
$svh = $app->make('helper/validation/strings');

$svh->email($em, $testMXRecord = false, $strict = false); //@deprecated Use Concrete\Core\Validator\String\EmailValidator
$svh->alphanum($value, $allowSpaces = false, $allowDashes = false); //Returns true on whether the passed string is completely alpha-numeric, if the value is not a string or is an empty string false will be returned.
$svh->handle($handle); //Returns true if the passed string is a valid "handle" (e.g. only letters, numbers, or a _ symbol).
$svh->notempty($field); //Returns false if the string is empty (including trim()).
$svh->min($str, $length); //Returns true on whether the passed string is larger or equal to the passed length.
$svh->max($str, $length); //Returns true on whether the passed is smaller or equal to the passed length.
$svh->containsNumber($str); //Returns 0 if there are no numbers in the string, or returns the number of numbers in the string.
$svh->containsUpperCase($str); //Returns 0 if there are no upper case letters in the string, or returns the number of upper case letters in the string.
$svh->containsLowerCase($str); //Returns 0 if there are no lower case letters in the string, or returns the number of lower case letters in the string.
$svh->containsSymbol($str); //Returns 0 if there are no symbols in the string, or returns the number of symbols in the string.

//\concrete\src\Utility\Service\Validation\Strings.php
```

#### JSON helper
```PHP
$jh = $app->make('helper/json');

$jh->decode($string, $assoc = false); //Decodes a JSON string into a php variable.
$jh->encode($mixed); //Encodes a data structure into a JSON string.

//\concrete\src\Http\Service\Json.php
```

#### Ajax helper
```PHP
$ah = $app->make('helper/json');

$ah->isAjaxRequest(Request $request); //Check if a request is an Ajax call.
$ah->sendResult($result); //Sends a result to the client and ends the execution.
$ah->sendError($error); //Sends an error to the client and ends the execution.

//\concrete\src\Http\Service\Ajax.php
```

#### HTML helper
```PHP
$hh = $app->make('helper/html');

$hh->css($file, $pkgHandle = null); //
$hh->javascript($file, $pkgHandle = null); //
$hh->noFollowHref($input); //Takes in a string, and adds rel="nofollow" to any a tags that contain an href attribute.

//\concrete\src\Html\Service\Html.php
```

#### Navigation helper
```PHP
$nh = $app->make('helper/navigation');

$nh->getLinkToCollection($cObj); //Returns a link to a page. Note: this always returns a string.
$nh->getTrailToCollection($c); //Returns an array of collections as a breadcrumb to the current page.
$nh->getCollectionURL($cObj); //Returns the URL of a collection so that it can be clicked on.
$nh->getLogInOutLink(); //

//\concrete\src\Html\Service\Navigation.php
```

#### Date helper
```PHP
$dh = $app->make('helper/date'); 
//$dh = $app->make('date');

$dh->toDB($value = 'now', $fromTimezone = 'system'); //Convert any date/time representation to a string that can be used in DB queries.
$dh->getOverridableNow($asTimestamp = false); //Return the date/time representation for now, that can be overridden by a custom request when viewing pages in a moment specified by administrators (custom request date/time).
$dh->date($mask, $timestamp = false, $toTimezone = 'system'); //Subsitute for the native date() function that adds localized date support.
$dh->getTimezoneName($timezoneID); //Retrieve the display name (localized) of a time zone given its PHP identifier.
$dh->getTimezones(); //Returns a keyed array of timezone identifiers (keys are the standard PHP timezone names, values are the localized timezone names).
$dh->getGroupedTimezones(); //Returns the list of timezones with translated names, grouped by region.
$dh->getTimezoneDisplayName($timezone); //Returns the display name of a timezone.
$dh->timeSince($posttime, $precise = false); //Describe the difference in time between now and a date/time in the past.
$dh->describeInterval($diff, $precise = false); //Returns the localized representation of a time interval specified as seconds.
$dh->getTimezoneID($timezone); //Returns the normalized timezone identifier.
$dh->getUserTimeZoneID(); //
$dh->getTimezone($timezone); //Returns a \DateTimeZone instance for a specified timezone identifier.
$dh->toDateTime($value = 'now', $toTimezone = 'system', $fromTimezone = 'system'); //Convert a date to a \DateTime instance.
$dh->getDeltaDays($from, $to, $timezone = 'user'); //Returns the difference in days between to dates.
$dh->formatDate($value = 'now', $format = 'short', $toTimezone = 'user'); //Render the date part of a date/time as a localized string.
$dh->formatTime($value = 'now', $withSeconds = false, $toTimezone = 'user'); //Render the time part of a date/time as a localized string.
$dh->formatDateTime($value = 'now', $longDate = false, $withSeconds = false, $toTimezone = 'user'); //Render both the date and time parts of a date/time as a localized string.
$dh->formatPrettyDate($value, $longDate = false, $toTimezone = 'user'); //Render the date part of a date/time as a localized string. If the day is yesterday we'll print 'Yesterday' (the same for today, tomorrow).
$dh->formatPrettyDateTime($value, $longDate = false, $withSeconds = false, $timezone = 'user'); //Render both the date and time parts of a date/time as a localized string. If the day is yesterday we'll print 'Yesterday' (the same for today, tomorrow).
$dh->formatCustom($format, $value = 'now', $toTimezone = 'user', $fromTimezone = 'system'); //Render a date/time as a localized string, by specifying a custom format.
$dh->getJQueryUIDatePickerFormat($relatedPHPFormat = ''); //Returns the format string for the jQueryUI DatePicker widget
$dh->getTimeFormat(); //Returns the time format (12 or 24).
$dh->getPHPDatePattern(); //
$dh->getPHPTimePattern(); //Get the PHP date format string for times.
$dh->getPHPDateTimePattern(); //Get the PHP date format string for dates/times.
$dh->getLocalDateTime($systemDateTime = 'now', $mask = null); //@deprecated
$dh->getSystemDateTime($userDateTime = 'now', $mask = null); //@deprecated
$dh->dateTimeFormatLocal($datetime, $mask); //@deprecated

//\concrete\src\Localization\Service\Date.php
```

#### Form helper
```PHP
$form = $app->make('helper/form'); // no need to initiate

$form->setRequest(Request $request); // Set the request instance.
$form->getRequest(); //
echo $form->action($action, $task = null); // Returns an action suitable for including in a form action property.
echo $form->submit($key, $value, $miscFields = [], $additionalClasses = ''); // Creates a submit button.
echo $form->button($key, $value, $miscFields = [], $additionalClasses = ''); // Creates a button.
echo $form->label($forFieldID, $innerHTML, $miscFields = []); // Creates a label tag.
echo $form->file($key, $miscFields = []); // Creates a file input element.
echo $form->hidden($key, $value = null, $miscFields = []); // Creates a hidden form field.
echo $form->checkbox($key, $value, $isChecked = false, $miscFields = []); // Generates a checkbox.
echo $form->textarea($key, $valueOrMiscFields = '', $miscFields = []); // Creates a textarea field.
echo $form->radio($key, $value, $checkedValueOrMiscFields = '', $miscFields = []); // Generates a radio button.
echo $form->getRequestValue($key); // Checks the request (first POST then GET) based on the key passed.
echo $form->text($key, $valueOrMiscFields = '', $miscFields = []); // Renders a text input field.
echo $form->number($key, $valueOrMiscFields = '', $miscFields = []); // Renders a number input field.
echo $form->email($key, $valueOrMiscFields = '', $miscFields = []); // Renders an email input field.
echo $form->telephone($key, $valueOrMiscFields = '', $miscFields = []); // Renders a telephone input field.
echo $form->url($key, $valueOrMiscFields = '', $miscFields = []); // Renders a URL input field.
echo $form->search($key, $valueOrMiscFields = '', $miscFields = []); // Renders a search input field.
echo $form->select($key, $optionValues, $valueOrMiscFields = '', $miscFields = []); // Renders a select field.
echo $form->selectCountry($key, $selectedCountryCode = '', array $configuration = [], array $miscFields = []); // Renders a select menu to choose a Country.
echo $form->selectMultiple($key, $optionValues, $defaultValues = false, $miscFields = []); // Renders a multiple select box.
echo $form->password($key, $valueOrMiscFields = '', $miscFields = []); // Renders a password input field.
echo $form->getAutocompletionDisabler(); // Generates HTML code that can be added at the beginning of a form to disable username/password autocompletion.
echo $form->processRequestValue($key, $type = 'post'); // Checks the request based on the key passed.
echo $form->inputType($key, $type, $valueOrMiscFields, $miscFields); // Internal function that creates an <input> element of type $type. Handles the messiness of evaluating $valueOrMiscFields. Assigns a default class of ccm-input-$type.
echo $form->parseMiscFields($defaultClass, $attributes); // Create an HTML fragment of attribute values, merging any CSS class names as necessary.

//\concrete\src\Form\Service\Form.php
```

#### Form (editor/richtext editor/Redactor) helper 
```PHP
$editor = Core::make('editor');
//$editor->setAllowSitemap(false); //disable SiteMap
//$editor->setAllowFileManager(false); // disable FileManager
echo $editor->outputStandardEditor($key, $content = null);

//\Concrete\src\Editor\RedactorEditor.php

// in 5.7.4.2+, we can include and exclude editor plugins. Here we exclude table, underline, and specialcharacters and include fontsize.
// https://documentation.concrete5.org/developers/interface-customization/rich-text-editor/embedding-rich-text-editor
$editor = Core::make('editor');
$editor->getPluginManager()->deselect(array('table', 'underline', 'specialcharacters'));
$editor->getPluginManager()->select('fontsize');
echo $editor->outputStandardEditor('notes', $notes);
```

#### Form (color picker) helper
```PHP
$cpfh = $app->make('helper/form/color');

echo $cpfh->output($inputName, $value = null, $options = array()); // Creates form fields and JavaScript includes to add a color picker widget.
//echo $cpfh->output('background-color', '#f00');

//\concrete\src\Form\Service\Widget\Color.php
```

#### Form (date/time) helper
```PHP
$dtfh = $app->make('helper/form/date_time');

$dtfh->translate($field, $arr = null, $asDateTime = false); // Takes a "field" and grabs all the corresponding disparate fields from $_POST and translates into a timestamp.
echo $dtfh->datetime($field, $value = null, $includeActivation = false, $calendarAutoStart = true, $classes = null, $timeResolution = 60, array $datePickerOptions = array()); // Creates form fields and JavaScript calendar includes for a particular item (date/time string representations will be converted from the user system-zone to the time-zone).
echo $dtfh->date($field, $value = null, $calendarAutoStart = true, array $datePickerOptions = array()); // Creates form fields and JavaScript calendar includes for a particular item but includes only calendar controls (no time, so no time-zone conversions will be applied).
echo $dtfh->selectNearestValue(array $values, $wantedValue); // Choose an array value nearest to a specified value. Useful when we work with time resolutions.

//\concrete\src\Form\Service\Widget\DateTime.php
```

#### Form (page selector) helper
```PHP
$psfh = $app->make('helper/form/page_selector');

echo $psfh->selectPage($fieldName, $cID = false); //Creates form fields and JavaScript page chooser for choosing a page. For use with inclusion in blocks.
echo $psfh->quickSelect($key, $cID = false, $args = array()); //
echo $psfh->selectMultipleFromSitemap($field, $pages = array(), $startingPoint = 'HOME_CID', $filters = array()); //
echo $psfh->selectFromSitemap($field, $page = null, $startingPoint = 'HOME_CID', SiteTree $siteTree = null, $filters = array()); //

//\concrete\src\Form\Service\Widget\PageSelector.php
```

#### Form (user selector) helper
```PHP
$usfh = $app->make('helper/form/user_selector');

echo $usfh->selectUser($fieldName, $uID = false); //Build the HTML to be placed in a page to choose a user using a popup dialog.
echo $usfh->quickSelect($fieldName, $uID = false, $miscFields = []); //Build the HTML to be placed in a page to choose a user using a select with users pupulated dynamically with ajax requests.
echo $usfh->selectMultipleUsers($fieldName, $users = []); //Build the HTML to be placed in a page to choose multiple users using a popup dialog.

//\concrete\src\Form\Service\Widget\UserSelector.php
```

#### Form (group selector) helper
```PHP
$gsfh = $app->make('\Concrete\Core\Form\Service\Widget\GroupSelector');

echo $gsfh->selectGroup($field, $group = null, $noneText = null); //Build the HTML to be placed in a page to choose a group using a select box.
echo $gsfh->selectGroupWithTree($field, $group = null); //Build the HTML to be placed in a page to choose a group using a tree view.

//\Concrete\src\Form\Service\Widget\GroupSelector.php
```

#### Form (rating) helper
```PHP
$rfh = $app->make('helper/form/rating');

echo $rfh->rating($prefix, $value = null, $includeJS = true);

//\concrete\src\Form\Service\Widget\Rating.php
```

#### Form (attribute) helper
```PHP
$afh = $app->make('helper/form/attribute');

$afh->setAttributeObject($obj); //
$afh->display($key, $required = false, $includeLabel = true, $template = 'composer');


// usage for page(collection) attributes
$afh = $app->make('helper/form/attribute');
$key = CollectionAttributeKey::getByHandle('page_attribute_handle'); // get attribute object
echo $afh->display($key);

// usage for file attributes
$afh = $app->make('helper/form/attribute');
$key = FileAttributeKey::getByHandle('file_attribute_handle'); // get attribute object
echo $afh->display($key);

// usage for userinfo attributes
$afh = $app->make('helper/form/attribute');
$key = UserAttributeKey::getByHandle('user_attribute_handle'); // get attribute object
echo $afh->display($key);

//\concrete\src\Form\Service\Widget\Attribute.php
```

#### Form (typography) helper
```PHP
$tfh = $app->make('helper/form/typography');
// OR
$tfh = $app->make('helper/form/font');

echo $tfh->output($inputName, $value = array(), $options = array()); // Creates form fields and JavaScript includes to add a font picker widget.

//\concrete\src\Form\Service\Widget\Typography.php
```

#### Concrete URL helper
```PHP
$cuh = $app->make('helper/concrete/urls');

$cuh->getPackageIconURL($pkg); // Gets a full URL to an icon for a particular application.
$cuh->getPackageURL($pkg); // Get the package's URL.
$cuh->getToolsURL($tool, $pkgHandle = null); // Gets a URL to reference a script in the tools directory
$cuh->getBlockTypeIconURL($bt); // Gets a full URL to an icon for a particular block type.
$cuh->getBlockTypeAssetsURL($bt, $file = false); // Gets a full URL to the directory containing all of a block's items, including JavaScript, tools, icons, etc...
$cuh->getBlockTypeJavaScriptURL($bt); // Gets a full URL to a block's JavaScript file (if one exists).
$cuh->getBlockTypeToolsURL($bt); // @deprecated: Gets a full URL to a block's tools directory

//\concrete\src\Application\Service\Urls.php
```

#### Asset library (file manager) helper
```PHP
$alh = $app->make('helper/concrete/asset_library');
// OR
$alh = $app->make('helper/concrete/file_manager');

$alh->file($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a file.
$alh->image($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick an image file.
$alh->video($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a video file.
$alh->text($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a text file.
$alh->audio($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick an audio file.
$alh->doc($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a document file.
$alh->app($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a application file.
$alh->fileOfType($type, $inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); // Sets up a form field to let users pick a file of a specific type.

//\concrete\src\Application\Service\FileManager.php
```

#### Validation error helper
```PHP
$errors = $app->make('error');
// OR
$errors = $app->make('helper/validation/error');

$errors->add($e, $fieldName = null, $fieldDisplayName = null); // Add an error message/object or exception to the internal error array (error messages are in plain text if not otherwise specified).
$errors->addHtml($e, $fieldName = null, $fieldDisplayName = null); // Add an error message/object or exception to the internal error array (error messages are in HTML if not otherwise specified).
$errors->getList(); // Get the list of errors contained in this error list.
$errors->has(); // Returns whether or not this error list has more than one error registered within it.
$errors->toText(); // Render this error list as a plain text.
$errors->containsField($field); // Does this list contain error associated to a field?
$errors->getMessage($field); // Get the error message (if any) associated to a field.
$errors->createResponse($errorCode = JsonResponse::HTTP_BAD_REQUEST); // Create a JSON response describing the errors in this list.

//\concrete\src\Error\ErrorList\ErrorList.php
```

#### User Interface helper
```PHP
$uih = $app->make('helper/concrete/ui')

$uih->submit($text, $formID = false, $buttonAlign = 'right', $innerClass = null, $args = []); //Generates a submit button in the Concrete style.
$uih->button($text, $href, $buttonAlign = 'right', $innerClass = null, $args = []); //Generates a simple link button in the Concrete style.
$uih->buttonJs($text, $onclick, $buttonAlign = 'right', $innerClass = null, $args = []); //Generates a JavaScript function button in the Concrete style.
$uih->button_js($text, $onclick, $buttonAlign = 'right', $innerClass = null, $args = []); //"
$uih->buttons($buttons = null); //Outputs button text passed as arguments with a special Concrete wrapper for positioning
$uih->getQuickNavigationLinkHTML($c); //
$uih->showWhiteLabelMessage(); //
$uih->getToolbarLogoSRC(); //
$uih->showNewsflowOverlay(); //@deprecated The Newsflow Overlay feature has been removed
$uih->showHelpOverlay(); //Shall we show the introductive help overlay?
$uih->trackHelpOverlayDisplayed(); //
$uih->clearInterfaceItemsCache(); //Clears the Interface Items Cache (clears the session).
$uih->cacheInterfaceItems(); //Cache the interface items.
$uih->pagetabs($tabs); //
$uih->tabs($tabs, $jstabs = true, $callback = 'ccm_activateTabBar'); //
$uih->renderError($title, $error, $exception = false); //
$uih->buildErrorResponse($title, $error, $exception = false); //
$uih->notify($arguments); //

//\concrete\src\Application\Service\UserInterface.php
```

#### Image helper
```PHP
$ih = $app->make('helper/image');

$ih->getStorageLocation(); //
$ih->setStorageLocation(StorageLocationInterface $storageLocation); //
$ih->setJpegCompression($level); //
$ih->getJpegCompression(); //
$ih->setPngCompression($level); //
$ih->getPngCompression(); //
$ih->setThumbnailsFormat($thumbnailsFormat); //
$ih->getThumbnailsFormat(); //
$ih->create($mixed, $savePath, $width, $height, $fit = false, $format = false); //
$ih->returnThumbnailObjectFromResolver($obj, $maxWidth, $maxHeight, $crop = false); //Checks thumbnail resolver for filename, schedule for creation via ajax if necessary.
$ih->checkForThumbnailAndCreateIfNecessary($obj, $maxWidth, $maxHeight, $crop = false); //Checks filesystem for thumbnail and if file doesn't exist will create it immediately. concrete5's default behavior from the beginning up to 8.1.
$ih->processThumbnail($async, $obj, $maxWidth, $maxHeight, $crop); //
$ih->getThumbnail($obj, $maxWidth, $maxHeight, $crop = false); //
$ih->outputThumbnail($mixed, $maxWidth, $maxHeight, $alt = null, $return = false, $crop = false); //

//\concrete\src\File\Image\BasicThumbnailer.php
```

#### List of all helper
```PHP
'app' instanceof Concrete\Core\Application\Application,
'Concrete\Core\Application\Application' instanceof Concrete\Core\Application\Application,
'Illuminate\Container\Container' instanceof Concrete\Core\Application\Application,
'authentication/community' instanceof \Concrete\Core\Authentication\Type\Community\Service\Community,
'authentication/facebook' instanceof \OAuth\OAuth2\Service\Facebook,
'authentication/google' instanceof \OAuth\OAuth2\Service\Google,
'authentication/twitter' instanceof \OAuth\OAuth1\Service\Twitter,
'cache' instanceof \Concrete\Core\Cache\Level\ObjectCache,
'cache/expensive' instanceof \Concrete\Core\Cache\Level\ExpensiveCache,
'cache/request' instanceof \Concrete\Core\Cache\Level\RequestCache,
'captcha' instanceof \Concrete\Core\Captcha\Service,
'helper/validation/captcha' instanceof \Concrete\Core\Captcha\Service,
'Concrete\Core\Config\Repository\Repository' instanceof \config,
'Concrete\Core\Database\Driver\DriverManager' instanceof \Concrete\Core\Database\Driver\DriverManager,
'Concrete\Core\Http\Request' instanceof \Concrete\Core\Http\Request,
'Concrete\Core\Routing\Router' instanceof \Concrete\Core\Routing\Router,
'Concrete\Core\Routing\RouterInterface' instanceof \Concrete\Core\Routing\Router,
'Concrete\Core\Session\SessionFactoryInterface' instanceof \Concrete\Core\Session\SessionFactory,
'Concrete\Core\Session\SessionValidatorInterface' instanceof \Concrete\Core\Session\SessionValidator,
'config' instanceof Concrete\Core\Config\Repository\Repository,
'config/database' instanceof Concrete\Core\Config\Repository\Repository,
'Illuminate\Config\Repository' instanceof \Concrete\Core\Config\Repository\Repository,
'cookie' instanceof \Concrete\Core\Cookie\CookieJar,
'database' instanceof \Concrete\Core\Database\DatabaseManager,
'Concrete\Core\Database\DatabaseManager' instanceof \Concrete\Core\Database\DatabaseManager,
'database/orm' instanceof \Concrete\Core\Database\DatabaseManagerORM,
'Concrete\Core\Database\DatabaseManagerORM' instanceof \Concrete\Core\Database\DatabaseManagerORM,
'database/structure' instanceof \Concrete\Core\Database\DatabaseStructureManager,
'date' instanceof        \Concrete\Core\Localization\Service\Date,
'helper/date' instanceof \Concrete\Core\Localization\Service\Date,
'device/manager' instanceof \Concrete\Core\Device\DeviceManager,
'director' instanceof \Symfony\Component\EventDispatcher\EventDispatcher,
'Doctrine\DBAL\Connection' instanceof \Concrete\Core\Database\Connection\Connection,
'Concrete\Core\Database\Connection\Connection' instanceof \Concrete\Core\Database\Connection\Connection,
'Doctrine\ORM\EntityManager' instanceof \Doctrine\ORM\EntityManagerInterface,
'Doctrine\ORM\EntityManagerInterface' instanceof \Doctrine\ORM\EntityManager,
'editor' instanceof \Concrete\Core\Editor\RedactorEditor,
'editor/image' instanceof \Concrete\Core\ImageEditor\ImageEditor,
'editor/image/core' instanceof \Concrete\Core\ImageEditor\ImageEditor,
'editor/image/extension/factory' instanceof \Concrete\Core\ImageEditor\ExtensionFactory,
'error' instanceof \Concrete\Core\Error\Error,
'helper/validation/error' instanceof \Concrete\Core\Error\Error,
'help' instanceof \Concrete\Core\Application\Service\UserInterface\Help,
'helper/concrete/ui/help' instanceof \Concrete\Core\Application\Service\UserInterface\Help,
'help/block_type' instanceof \Concrete\Core\Application\Service\UserInterface\Help\BlockTypeManager,
'help/core' instanceof \Concrete\Core\Application\Service\UserInterface\Help\CoreManager,
'help/dashboard' instanceof \Concrete\Core\Application\Service\UserInterface\Help\DashboardManager,
'help/panel' instanceof \Concrete\Core\Application\Service\UserInterface\Help\PanelManager,
'helper/ajax' instanceof \Concrete\Core\Http\Service\Ajax,
'helper/arrays' instanceof \Concrete\Core\Utility\Service\Arrays,
'helper/concrete/avatar' instanceof \Concrete\Core\Application\Service\Avatar,
'helper/concrete/composer' instanceof \Concrete\Core\Application\Service\Composer,
'helper/concrete/dashboard' instanceof \Concrete\Core\Application\Service\Dashboard,
'helper/concrete/dashboard/sitemap' instanceof \Concrete\Core\Application\Service\Dashboard\Sitemap,
'helper/concrete/file' instanceof \Concrete\Core\File\Service\Application,
'helper/concrete/file_manager' instanceof \Concrete\Core\Application\Service\FileManager,
'helper/concrete/asset_library' instanceof \Concrete\Core\Application\Service\FileManager,
'helper/concrete/ui' instanceof \Concrete\Core\Application\Service\UserInterface,
'helper/concrete/ui/menu' instanceof \Concrete\Core\Application\Service\UserInterface\Menu,
'helper/concrete/upgrade' instanceof \Concrete\Core\Application\Service\Upgrade,
'helper/concrete/urls' instanceof \Concrete\Core\Application\Service\Urls,
'helper/concrete/user' instanceof \Concrete\Core\Application\Service\User,
'helper/concrete/validation' instanceof \Concrete\Core\Application\Service\Validation,
'helper/encryption' instanceof \Concrete\Core\Encryption\EncryptionService,
'helper/feed' instanceof \Concrete\Core\Feed\FeedService,
'helper/file' instanceof \Concrete\Core\File\Service\File,
'helper/form' instanceof \Concrete\Core\Form\Service\Form,
'helper/form/attribute' instanceof \Concrete\Core\Form\Service\Widget\Attribute,
'helper/form/color' instanceof \Concrete\Core\Form\Service\Widget\Color,
'helper/form/date_time' instanceof \Concrete\Core\Form\Service\Widget\DateTime,
'helper/form/font' instanceof \Concrete\Core\Form\Service\Widget\Typography,
'helper/form/typography' instanceof \Concrete\Core\Form\Service\Widget\Typography,
'helper/form/page_selector' instanceof \Concrete\Core\Form\Service\Widget\PageSelector,
'helper/form/rating' instanceof \Concrete\Core\Form\Service\Widget\Rating,
'helper/form/user_selector' instanceof \Concrete\Core\Form\Service\Widget\UserSelector,
'helper/html' instanceof \Concrete\Core\Html\Service\Html,
'helper/image' instanceof \Concrete\Core\File\Image\BasicThumbnailer,
'image/thumbnailer' instanceof \Concrete\Core\File\Image\BasicThumbnailer,
'helper/json' instanceof \Concrete\Core\Http\Service\Json,
'helper/lightbox' instanceof \Concrete\Core\Html\Service\Lightbox,
'helper/mime' instanceof \Concrete\Core\File\Service\Mime,
'helper/navigation' instanceof \Concrete\Core\Html\Service\Navigation,
'helper/number' instanceof \Concrete\Core\Utility\Service\Number,
'helper/pagination' instanceof \Concrete\Core\Legacy\Pagination,
'helper/rating' instanceof \Concrete\Attribute\Rating\Service,
'helper/security' instanceof \Concrete\Core\Validation\SanitizeService,
'helper/seo' instanceof \Concrete\Core\Html\Service\Seo,
'helper/text' instanceof \Concrete\Core\Utility\Service\Text,
'helper/url' instanceof \Concrete\Core\Utility\Service\Url,
'helper/validation/antispam' instanceof \Concrete\Core\Antispam\Service,
'helper/validation/banned_words' instanceof \Concrete\Core\Validation\BannedWord\Service,
'helper/validation/file' instanceof \Concrete\Core\File\ValidationService,
'helper/validation/form' instanceof \Concrete\Core\Form\Service\Validation,
'helper/validation/identifier' instanceof \Concrete\Core\Utility\Service\Identifier,
'helper/validation/numbers' instanceof \Concrete\Core\Utility\Service\Validation\Numbers,
'helper/validation/strings' instanceof \Concrete\Core\Utility\Service\Validation\Strings,
'helper/xml' instanceof \Concrete\Core\Utility\Service\Xml,
'html/image' instanceof \Concrete\Core\Html\Image,
'helper/zip' instanceof \Concrete\Core\File\Service\Zip,
'image/gd' instanceof \Imagine\Gd\Imagine,
'image/imagick' instanceof \Imagine\Imagick\Imagine,
'import/value_inspector' instanceof \Concrete\Core\Backup\ContentImporter\ValueInspector\ValueInspector,
'import/value_inspector/core' instanceof \Concrete\Core\Backup\ContentImporter\ValueInspector\ValueInspector,
'ip' instanceof \Concrete\Core\Permission\IPService,
'helper/validation/ip' instanceof \Concrete\Core\Permission\IPService,
'localization/countries' instanceof \Concrete\Core\Localization\Service\CountryList,
'helper/lists/countries' instanceof \Concrete\Core\Localization\Service\CountryList,
'helper/localization/countries' instanceof \Concrete\Core\Localization\Service\CountryList,
'lists/countries' instanceof \Concrete\Core\Localization\Service\CountryList,
'localization/languages' instanceof \Concrete\Core\Localization\Service\LanguageList,
'localization/states_provinces' instanceof \Concrete\Core\Localization\Service\StatesProvincesList,
'helper/lists/states_provinces' instanceof \Concrete\Core\Localization\Service\StatesProvincesList,
'helper/localization/states_provinces' instanceof \Concrete\Core\Localization\Service\StatesProvincesList,
'lists/states_provinces' instanceof \Concrete\Core\Localization\Service\StatesProvincesList,
'log' instanceof Concrete\Core\Logging\Logger,
'Concrete\Core\Logging\Logger' instanceof \Concrete\Core\Logging\Logger,
'Psr\Log\LoggerInterface' instanceof \Concrete\Core\Logging\Logger,
'mail' instanceof \Concrete\Core\Mail\Service,
'helper/mail' instanceof \Concrete\Core\Mail\Service,
'manager/area_layout_preset_provider' instanceof \Concrete\Core\Area\Layout\Preset\Provider\Manager,
'manager/grid_framework' instanceof \Concrete\Core\Page\Theme\GridFramework\Manager,
'manager/page_type/validator' instanceof \Concrete\Core\Page\Type\Validator\Manager,
'manager/view/pagination' instanceof \Concrete\Core\Search\Pagination\View\Manager,
'multilingual/detector' instanceof \Concrete\Core\Multilingual\Service\Detector,
'multilingual/extractor' instanceof \Concrete\Core\Multilingual\Service\Extractor,
'multilingual/interface/flag' instanceof \Concrete\Core\Multilingual\Service\UserInterface\Flag,
'oauth/factory/extractor' instanceof \OAuth\UserData\ExtractorFactory,
'oauth/factory/service' instanceof \OAuth\ServiceFactory,
'session' instanceof \Symfony\Component\HttpFoundation\Session\Session,
'Symfony\Component\HttpFoundation\Session\Session' instanceof \session,
'token' instanceof \Concrete\Core\Validation\CSRF\Token,
'helper/validation/token' instanceof \Concrete\Core\Validation\CSRF\Token,
'url/canonical' instanceof \Concrete\Core\Url\UrlImmutable,
'url/canonical/resolver' instanceof \Concrete\Core\Url\Resolver\CanonicalUrlResolver,
'Concrete\Core\Url\Resolver\CanonicalUrlResolver' instanceof \Concrete\Core\Url\Resolver\CanonicalUrlResolver,
'url/manager' instanceof \Concrete\Core\Url\Resolver\Manager\ResolverManager,
'Concrete\Core\Url\Resolver\Manager\ResolverManager' instanceof \Concrete\Core\Url\Resolver\Manager\ResolverManager,
'Concrete\Core\Url\Resolver\Manager\ResolverManagerInterface' instanceof \Concrete\Core\Url\Resolver\Manager\ResolverManager,
'url/resolver/page' instanceof \Concrete\Core\Url\Resolver\PageUrlResolver,
'Concrete\Core\Url\Resolver\PageUrlResolver' instanceof \Concrete\Core\Url\Resolver\PageUrlResolver,
'url/resolver/path' instanceof \Concrete\Core\Url\Resolver\PathUrlResolver,
'Concrete\Core\Url\Resolver\PathUrlResolver' instanceof \Concrete\Core\Url\Resolver\PathUrlResolver,
'url/resolver/route' instanceof \Concrete\Core\Url\Resolver\RouteUrlResolver,
'Concrete\Core\Url\Resolver\RouterUrlResolver' instanceof \Concrete\Core\Url\Resolver\RouterUrlResolver,
'user.avatar' instanceof \Concrete\Core\User\Avatar\AvatarService,
'Concrete\Core\User\Avatar\AvatarServiceInterface' instanceof \Concrete\Core\User\Avatar\AvatarService,
'user.registration' instanceof \Concrete\Core\User\RegistrationService,
'Concrete\Core\User\RegistrationServiceInterface' instanceof \Concrete\Core\User\RegistrationService,
'validator/password' instanceof \Concrete\Core\Validator\ValidatorManager,
'\Concrete\Core\Validator\ValidatorManagerInterface' instanceof \Concrete\Core\Validator\ValidatorManager,
```

## System Operations



### Database


#### Current database
```PHP
// database connection
$db = $app->make(\Concrete\Core\Database\Connection\Connection::class);

//prepare any query
$statement = $db->executeQuery('SELECT * FROM `myTable` WHERE `id`>?;', array(0)); 
    
//echo $statement->rowCount(); // number of SELECTed/UPDATEd/DELETEd rows
//echo $statement->getSqlQuery(); // prepared SQL //not working

//iterate through rows
$rows = $statement->fetchAll(); //print_r($rows);
foreach ($rows as $row) {
    print_r($row);
}
// OR:
while ($row = $statement->fetch()) {
    //print_r($row);
}	

// Prepares and executes an SQL query and returns the FIRST row of the result as an associative array.
$row = $db->fetchAssoc('SELECT * FROM `myTable` WHERE `id` = ?;', array(1)); //print_r($row);

// Prepares and executes an SQL query and returns the result as an associative array.
$rows = $db->fetchAll('SELECT `name` FROM `myTable`;'); //print_r($rows);

// Prepares and executes an SQL query and returns the value of a single column of the first row of the result.
$column = $db->fetchColumn('SELECT `name` FROM `myTable` WHERE id = ?;', array($id)); //echo $column;


// INSERT
$statement = $db->executeQuery('INSERT INTO `myTable` (`name`, `url`) VALUES (?, ?);', array('Name 1', 'URL 1')); 
//echo $db->lastInsertId(); // last inserted id
//echo $statement->rowCount(); // number of affected rows

//UPDATE
$statement = $db->executeQuery('UPDATE `myTable` SET name = ? WHERE `id` = ?;', array('new name', 1)); 
//echo $statement->rowCount(); // number of affected rows

//DELETE
$statement = $db->executeQuery('DELETE FROM `myTable` WHERE `id` = ?;', array(1)); 
//echo $statement->rowCount(); // number of affected rows
```
For more check [`here`](https://www.doctrine-project.org/api/dbal/2.5/Doctrine/DBAL/Connection.html)

#### Another database
```PHP
// new database connection info in /appilication/config/database.php
return array(
    'default-connection' => 'concrete',
    'connections' => array(
        'concrete' => array(
            'driver' => 'c5_pdo_mysql',
            'server' => 'localhost',
            'database' => 'database',
            'username' => 'username',
            'password' => 'password',
            'charset' => 'utf8',
        ),
        'pricing' => array(
            'driver' => 'c5_pdo_mysql',
            'server' => 'secure-pricing.wherever.com',
            'database' => 'pricing_db',
            'username' => 'username',
            'password' => 'password',
            'charset' => 'utf8',
        ),
    ),
);

$dbPricing = $app->make('database')->connection('pricing');
```

### Misc.

#### URL
```PHP
$url = URL::to('/path/to/somewhere'); //http://ursite/index.php/path/to/somewhere
```

#### Logging
```PHP
//use Log;
Log::addInfo('This is an informative message.');
Log::addWarning('Uh oh.');
Log::addAlert('Red alert!');
Log::addNotice('A notice error.');
// see logs at /dashboard/reports/logs
```

#### Get environment
```PHP
$environment = $app->environment(); //echo $environment;
```

#### Clear site cache
```PHP
$app->clearCaches();
```
