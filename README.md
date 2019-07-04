# [concrete5](https://www.concrete5.org) Cheat Sheet V8+

This is a collection of concrete5 cheat sheets, based on the C5 V8+ source code. 

**Contributions are welcome via [issues](https://github.com/shahroq/whale_c5_cheat_sheet/issues) and [pull requests](https://github.com/shahroq/whale_c5_cheat_sheet/pulls).**

## Table of Contents <!-- omit in toc -->
- [Application (`$app`)](#Application-app)
  - [`$app` in a controller](#app-in-a-controller)
  - [`$app` in a custom class](#app-in-a-custom-class)
  - [`$app` in other places](#app-in-other-places)
- [Superglobals](#Superglobals)
  - [`$request` in a controller](#request-in-a-controller)
  - [`$request` in a custom class](#request-in-a-custom-class)
  - [`$request` in other places](#request-in-other-places)
- [Pages (Collections)](#Pages-Collections)
  - [A page](#A-page)
    - [Get Current page](#Get-Current-page)
    - [Get a page by a unique identifier](#Get-a-page-by-a-unique-identifier)
    - [Get a page data](#Get-a-page-data)
    - [Get a page type/template](#Get-a-page-typetemplate)
    - [Get a page attribute](#Get-a-page-attribute)
    - [Get list of attributes of a page](#Get-list-of-attributes-of-a-page)
  - [List of pages](#List-of-pages)
    - [Get list of pages](#Get-list-of-pages)
    - [Get list of pages with pagination](#Get-list-of-pages-with-pagination)
    - [Filter a page list](#Filter-a-page-list)
    - [Sort a page list](#Sort-a-page-list)
  - [Page operations](#Page-operations)
    - [Add a page](#Add-a-page)
    - [Update a page](#Update-a-page)
    - [Delete a page](#Delete-a-page)
    - [Move a page](#Move-a-page)
    - [Copy a Page](#Copy-a-Page)
    - [Add an extra location URL](#Add-an-extra-location-URL)
    - [Set/Update an attribute of a page](#SetUpdate-an-attribute-of-a-page)
    - [Clear an attribute of a page](#Clear-an-attribute-of-a-page)
    - [Refresh page cache](#Refresh-page-cache)
  - [Attributes](#Attributes)
    - [Get an attribute](#Get-an-attribute)
    - [Add an attribute](#Add-an-attribute)
    - [Delete an attribute](#Delete-an-attribute)
    - [Add an attribute set](#Add-an-attribute-set)
- [Files](#Files)
  - [A Files](#A-Files)
    - [Get a file by a unique identifier](#Get-a-file-by-a-unique-identifier)
    - [Get a file data](#Get-a-file-data)
    - [Get a file attribute](#Get-a-file-attribute)
    - [Get list of attributes of a file](#Get-list-of-attributes-of-a-file)
  - [List of files](#List-of-files)
    - [Get list of files](#Get-list-of-files)
    - [Get list of files with pagination](#Get-list-of-files-with-pagination)
    - [Filter a file list](#Filter-a-file-list)
    - [Get files inside a folder](#Get-files-inside-a-folder)
    - [Sort a file list](#Sort-a-file-list)
    - [Get a file set](#Get-a-file-set)
    - [Get a file folder](#Get-a-file-folder)
  - [File Operation](#File-Operation)
    - [Importing a file](#Importing-a-file)
    - [Delete a file](#Delete-a-file)
    - [Set/Update an attribute to a file](#SetUpdate-an-attribute-to-a-file)
    - [Clear an attribute of a file](#Clear-an-attribute-of-a-file)
    - [Create a file set](#Create-a-file-set)
    - [Add a file to a set](#Add-a-file-to-a-set)
    - [Create a file folder](#Create-a-file-folder)
    - [Add a file to a folder](#Add-a-file-to-a-folder)
  - [Attributes](#Attributes-1)
    - [Get an attribute](#Get-an-attribute-1)
    - [Add an attribute](#Add-an-attribute-1)
    - [Add an attribute set](#Add-an-attribute-set-1)
- [Users](#Users)
  - [A User](#A-User)
    - [Get/Check current user](#GetCheck-current-user)
    - [Get a user by a unique identifier](#Get-a-user-by-a-unique-identifier)
    - [Get a user data](#Get-a-user-data)
    - [Get user info object](#Get-user-info-object)
    - [Get user info data](#Get-user-info-data)
    - [Get a user (info) attributes](#Get-a-user-info-attributes)
  - [List of users](#List-of-users)
    - [Get list of users](#Get-list-of-users)
    - [Get list of users with pagination](#Get-list-of-users-with-pagination)
    - [Filter a user list](#Filter-a-user-list)
    - [Sort a user list](#Sort-a-user-list)
  - [User operation](#User-operation)
    - [Add a user](#Add-a-user)
    - [Update a user](#Update-a-user)
    - [Activate/Deactivate a user](#ActivateDeactivate-a-user)
    - [Delete a user](#Delete-a-user)
    - [Set/Update an attribute to a user](#SetUpdate-an-attribute-to-a-user)
    - [Clear an attribute of a user](#Clear-an-attribute-of-a-user)
  - [Attributes](#Attributes-2)
    - [Get an attribute](#Get-an-attribute-2)
    - [Add an attribute](#Add-an-attribute-2)
    - [Add an attribute set](#Add-an-attribute-set-2)
- [Topics](#Topics)
    - [Schema](#Schema)
    - [Get a Topic Tree](#Get-a-Topic-Tree)
    - [List of Topic Trees](#List-of-Topic-Trees)
    - [Get children (Categories, Nodes) of a Topic Tree](#Get-children-Categories-Nodes-of-a-Topic-Tree)
    - [Topic Tree operations](#Topic-Tree-operations)
    - [Get a Category/Node](#Get-a-CategoryNode)
    - [Add a Category/Node](#Add-a-CategoryNode)
- [Attributes](#Attributes-3)
    - [List of attribute set categories (collection/user/file/site/event)](#List-of-attribute-set-categories-collectionuserfilesiteevent)
    - [List of sets in a category](#List-of-sets-in-a-category)
  - [Attrubute Set](#Attrubute-Set)
    - [A set](#A-set)
    - [Attributes in a set](#Attributes-in-a-set)
    - [List of sets](#List-of-sets)
- [Themes](#Themes)
  - [Page types](#Page-types)
    - [Adding areas in a Page Template](#Adding-areas-in-a-Page-Template)
    - [Embedding Blocks in a Page Template](#Embedding-Blocks-in-a-Page-Template)
- [Single Pages](#Single-Pages)
- [Blocks](#Blocks)
- [Stacks](#Stacks)
- [Packages](#Packages)
- [Express Entries](#Express-Entries)
  - [Express Entity](#Express-Entity)
    - [Create the entity](#Create-the-entity)
    - [Adding Associations to the Object](#Adding-Associations-to-the-Object)
    - [Create the Form](#Create-the-Form)
    - [Add attributes](#Add-attributes)
  - [Express Entry](#Express-Entry)
- [Language](#Language)
- [Constants](#Constants)
- [Configs](#Configs)
  - [Basics](#Basics)
    - [Key](#Key)
    - [Value](#Value)
  - [Different places for storing data](#Different-places-for-storing-data)
    - [Database](#Database)
    - [FileSystem](#FileSystem)
  - [Different ways to read and write config values](#Different-ways-to-read-and-write-config-values)
    - [1: Using a Package object](#1-Using-a-Package-object)
    - [2: Using a service provider](#2-Using-a-service-provider)
    - [3: Using Config](#3-Using-Config)
- [Helpers](#Helpers)
    - [General](#General)
    - [Number helper](#Number-helper)
    - [Text helper](#Text-helper)
    - [URL helper](#URL-helper)
    - [Array helper](#Array-helper)
    - [Arrays validation helper](#Arrays-validation-helper)
    - [Numbers validation helper](#Numbers-validation-helper)
    - [Strings validation helper](#Strings-validation-helper)
    - [JSON helper](#JSON-helper)
    - [Ajax helper](#Ajax-helper)
    - [HTML helper](#HTML-helper)
    - [Navigation helper](#Navigation-helper)
    - [Date helper](#Date-helper)
    - [Form helper](#Form-helper)
    - [Form (color picker) helper](#Form-color-picker-helper)
    - [Form (date/time) helper](#Form-datetime-helper)
    - [Form (page selector) helper](#Form-page-selector-helper)
    - [Form (user selector) helper](#Form-user-selector-helper)
    - [Form (rating) helper](#Form-rating-helper)
    - [Form (attribute) helper](#Form-attribute-helper)
    - [Form (typography) helper](#Form-typography-helper)
    - [Concrete URL helper](#Concrete-URL-helper)
    - [Asset library (file manager) helper](#Asset-library-file-manager-helper)
    - [Validation error helper](#Validation-error-helper)
    - [User Interface helper](#User-Interface-helper)
    - [Image helper](#Image-helper)
    - [List of all helper](#List-of-all-helper)
- [System Operations](#System-Operations)
  - [Database](#Database-1)
    - [Current database](#Current-database)
    - [Another database](#Another-database)
  - [Misc.](#Misc)
    - [URL](#URL)
    - [Logging](#Logging)
    - [Get environment](#Get-environment)
    - [Clear site cache](#Clear-site-cache)


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

## Superglobals

Direct access to PHP superglobals (that is, `$_REQUEST`, `$_POST`, `$_GET`, `$_SERVER`, `$_FILES`) should be avoided: concrete5 have a nicer way to work with them with the `$request` instance.

- instead of `$_GET['key']`: use `$request->query->get('key')`
- instead of `$_POST['key']`: use `$request->request->get('key')`
- instead of `$_REQUEST['key']`: use `$request->get('key')`
- instead of `$_SERVER['key']`: use `$request->server->get('key')`
- instead of `$_FILES['key']`: use `$request->files->get('key')`

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
$page = \Page::getByID(1); //by ID
$page = \Page::getByPath('/path/to/page'); //by path
```

#### Get a page data
```PHP
echo $page->getCollectionID();
echo $page->getCollectionName();
echo $page->getCollectionDescription();
echo $page->getCollectionDateAdded();
echo $page->getCollectionDatePublic();
echo $page->getCollectionUserID();

echo $page->getCollectionPath();
echo $page->getCollectionLink();
echo $page->getCollectionHandle()

echo $page->getCollectionParentID();

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

//get all page paths (locations)
foreach ($page->getPagePaths() as $path) {
    echo $path->getPagePath();
    echo $path->getPagePathID();
    echo $path->isPagePathCanonical();
}

//\concrete\src\Page\Page.php
```

#### Get a page type/template
```PHP
//Page Template
$pt = $page->getPageTemplateObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTemplateID(); //echo $ptID;
    $ptName = $pt->getPageTemplateName(); //echo $ptName;
    $ptHandle = $pt->getPageTemplateHandle(); //echo $ptHandle;
}        

//Page Type
$pt = $page->getPageTypeObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTypeID(); //echo $ptID;
    $ptName = $pt->getPageTypeName(); //echo $ptName;
    $ptHandle = $pt->getPageTypeHandle(); //echo $ptHandle;
}        
```

#### Get a page attribute
```PHP
//attribute
$attr = $page->getAttribute('attribute_handle');

//Option List: get options
foreach ((object)$attr as $option) {
    $optionID = $option->getSelectAttributeOptionID(); //echo $optionID;
    $optionValue = $option->getSelectAttributeOptionValue(); //echo $optionValue;
}

//Image/File
$attr = $page->getAttribute('thumbnail');
if ($attr) {
    $attrURL = $attr->getURL(); //echo $attrURL);
    $attrDownloadURL = $attr->getDownloadURL(); //echo $attrDownloadURL;
    $attrForceDownloadURL = $attr->getForceDownloadURL(); //echo $attrForceDownloadURL;
    $attrSize = $attr->getSize(); //echo $attrSize;
    $attrExtension = $attr->getExtension(); //echo $attrExtension;

    //image thumbnail
    $ih = $app->make('helper/image');
    $thumbSrc = $ih->getThumbnail($attr, 100, 100)->src; //echo $thumbSrc;
}
```

#### Get list of attributes of a page
```PHP
// get a list of attribute keys for which the page has values
$attrKeys = $page->getSetCollectionAttributes();
if (count($attrKeys)) {
    foreach ($attrKeys as $key) {
    	// each $key is an instance of \Concrete\Core\Entity\Attribute\Key\Key
        echo $attrHandle = $key->getAttributeKeyHandle();
        echo $attrName = $key->getAttributeKeyName();
    }
}
```

### List of pages


#### Get list of pages
```PHP
$pageList = new PageList();

$pages = $pageList->getResults();

//echo count($pages);
foreach ((array)$pages as $page) {
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
foreach ((array)$pages as $page) {
    echo $page->getCollectionID().'-'.$page->getCollectionName().'<br/>';
}

//pagination buttons
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3. 

//pagination functions
$pagination->setCurrentPage(1);
//$pagination->setCurrentPage($_GET['ccm_paging_p'] ?? 1); //in case the result is not generated correctly based on current page number
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of pages
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
```
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a page list
```PHP
$pageList->filterByParentID($cParentID); //by parent ID

$pageList->filterByKeywords('foobar'); //by keyword
$pageList->filterByFulltextKeywords('foobar'); //more advanced search by keyword

$pageList->filterByPageTypeID($ctID); //by a page type ID
$pageList->filterByPageTypeHandle('blog_entry'); //by a page type handle

$pageList->filterByPageTypeHandle(['blog_entry', 'press_release']); //by page typeS

$pageList->filterByUserID($uID); //by user ID
$pageList->filterByIsApproved($cvIsApproved); //by is approved
$pageList->filterByIsAlias($ia); //by alias

$pageList->filterByDateAdded($date, $comparison = '='); //by date added
$pageList->filterByPublicDate($date, $comparison = '='); //by public date
$pageList->filterByDateLastModified($date, $comparison = '='); //by last modified date
$pageList->filterByNumberOfChildren($num, $comparison = '>'); //by number of children


//by attribute:
$pageList->filterByAttribute($column, $value, $comparison = '=');
//OR
$pageList->filterByAttributeHandle($value, $comparison = '='); //for 'attribute_handle' => filterByAttributeHandle/ 'is_featured' => filterByIsFeatured(TRUE);

// by attribute: checkbox(boolean)
$pageList->filterByAttribute('attribute_handle', TRUE);
$pageList->filterByAttribute('attribute_handle', FALSE);

//by attribute: string (text/text area/email/URL, Phone NUmber, etc)
$pageList->filterByAttribute('attribute_handle', 'cat'); //equal to 'cat'
$pageList->filterByAttribute('attribute_handle', '%'.'cat'.'%', 'LIKE'); //has 'cat' anywhere in the string

//by attribute: number
$pageList->filterByAttribute('attribute_handle', 5); //equal to 5
$pageList->filterByAttribute('attribute_handle', 5, '>='); //greater than or equal to 5

//by attribute: date/time
$pageList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start)); //equal to $stat
$pageList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start), '>='); //greater than or equal to $start

// by attribute: option list
//$pageList->filterBySelectAttribute($akHandle, $value); //legacy. not working

//for filter based on a single option:
$pageList->filterByAttribute('attribute_handle', $value1);

//for filter based on multiple options: It seems not working properly for array with multiple options. use manual method instead.
$pageList->filterByAttribute('attribute_handle', array($value1, $value2)); 

//have either $value1 OR $value2 value
$pageList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$pageList->getQueryObject()->orWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

//have both $value1 AND $value2 values
$pageList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$pageList->getQueryObject()->andWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

//by attribute: topics
//first get nodes:
//use \Concrete\Core\Tree\Node\Node as TreeNode;
$topicNode1 = TreeNode::getByID(1);
$topicNode2 = TreeNode::getByID(2);

$pageList->filterByAttribute('attribute_handle', array($topicNode1, $topicNode2));
//or send the nodeIDs directly
$pageList->filterByAttribute('attribute_handle', array(1,2));

//OR: Category
$topicCategory1 = TreeNode::getByID(1);
$pageList->filterByAttribute('attribute_handle', array($topicCategory1));
//or send the nodeIDs directly
$pageList->filterByAttribute('attribute_handle', array(1));
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

$pageList->sortBy('ak_attribute_handle', 'desc'); //by an attribute: 'ak_' + attribute_handle
```

### Page operations


#### Add a page
```PHP
//$parentPage = \Page::getByID(1);
$parentPage = \Page::getByPath('/blog');
$pageType = \PageType::getByHandle('blog_entry'); //dashboard/pages/types 
$pageTemplate = \PageTemplate::getByHandle('blog_entry');//dashboard/pages/templates
$page = $parentPage->add(
    $pageType, 
    array(
        'cName' => 'Hello All!',
        'cDescription' => 'Just a quick blog post.',
    	'cHandle ' => 'hello-all',
    	//'cDatePublic' => '2019-01-02 20:21:22',
    	//'cDateCreated' => date('Y-m-d H:i:s'),
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
        //'cCacheFullPageContent' => FALSE,
        //'cCacheFullPageContentOverrideLifetime' => FALSE,
        //'cCacheFullPageContentLifetimeCustom' => FALSE,
    )    
);
```

#### Delete a page
```PHP
$page->delete(); //delete it immediately
$page->moveToTrash(); //move to trash
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
$page = \Page::getByID(1); //by ID
$page->setAttribute('attribute_handle', 'value');

//multiple values (option list)
$page->setAttribute('attribute_handle', array('value1', 'value2'));
```

#### Clear an attribute of a page
```PHP
$page = \Page::getByID(1); //by ID
$page->clearAttribute('attribute_handle');
```

#### Refresh page cache
```PHP
$page = \Page::getByID(1); //by ID
$page->refreshCache();
```

### Attributes


#### Get an attribute
```PHP
$attr = CollectionAttributeKey::getByID(1); //by ID
$attr = CollectionAttributeKey::getByHandle('attribute_handle'); //by handle

$attrID = $attr->getAttributeKeyID(); //echo $attrID;
$attrHandle = $attr->getAttributeKeyHandle(); //echo $attrHandle;
$attrName = $attr->getAttributeKeyName(); //echo $attrName;

//options of an 'Option List' attribute
$controller = $attr->getController();
$attrOptions = $controller->getOptions();
foreach ((object)$attrOptions as $attrOption) {
    $attrOptionID = $attrOption->getSelectAttributeOptionID(); //echo $attrOptionID;
    $attrOptionValue = $attrOption->getSelectAttributeOptionValue(); //echo $attrOptionValue;
}
```

#### Add an attribute
```PHP
//use Concrete\Core\Attribute\Type as AttributeType;
//use Concrete\Attribute\Select\Option as SelectAttributeTypeOption;

$attr = CollectionAttributeKey::getByHandle('attr_handle');
if (!is_object($attr)) {
    $attr_type = AttributeType::getByHandle('text'); 
    //$attr_type = AttributeType::getByHandle('textarea');
    //$attr_type = AttributeType::getByHandle('boolean'); //Checkbox 
    //$attr_type = AttributeType::getByHandle('date_time'); 
    //$attr_type = AttributeType::getByHandle('image_file');
    //$attr_type = AttributeType::getByHandle('number'); 
    //$attr_type = AttributeType::getByHandle('select'); //Option List
    //$attr_type = AttributeType::getByHandle('telephone'); //Phone Number
    //$attr_type = AttributeType::getByHandle('url'); 
    //$attr_type = AttributeType::getByHandle('email'); 
    //$attr_type = AttributeType::getByHandle('rating'); 
    //$attr_type = AttributeType::getByHandle('topics'); 
    //$attr_type = AttributeType::getByHandle('express'); //Express Entity
    //$attr_type = AttributeType::getByHandle('calendar'); 
    //$attr_type = AttributeType::getByHandle('calendar_event'); 
    //$attr_type = AttributeType::getByHandle('page_selector'); 
    //$attr_type = AttributeType::getByHandle('address'); //NOT available for collections
    //$attr_type = AttributeType::getByHandle('social_links'); //NOT available for collections

    $desc = array ( 
        'akHandle' => 'attr_handle',
        'akName'=> t('Attribute Name'),
        //'asID' => $attrSetID, //attribute set ID: check 'Get a set/Create a set' on how to get $attrSetID
        //'akIsSearchableIndexed' => TRUE, //Content included in search index. Default: FALSE
        //'akIsSearchable' => FALSE, //Field available in advanced search. Default: TRUE

        //////ATRIBUTE TYPES WITH SETTINGS://////

        ////text attribute (table: `atTextSettings`)
        //'akTextPlaceholder' => 'placeholder', //Placeholder Text

        ////textarea attribute (table: `atTextareaSettings`)
        //'akTextareaDisplayMode' => 'rich_text', //Input Format: 'text', 'rich_text'

        ////boolean attribute (table: `atBooleanSettings`)
        //'akCheckedByDefault' => TRUE, //Default Value: TRUE, FALSE
        //'akCheckboxLabel'=> t('Attribute Label'), //Label

        ////date_time attribute (table: `atDateTimeSettings`)
        //'akUseNowIfEmpty' => TRUE, //Suggest the current date/time if empty: TRUE, FALSE
        //'akDateDisplayMode' => 'date_time', //Ask User For: 'date_time', 'date', 'date_text', 'text'
        //'akTextCustomFormat' => 'Y-m-d H:i:s', //Custom format: PHP date function values (https://www.php.net/manual/en/function.date.php)
        //'akTimeResolution' => 60, //Time Resolution: 1, 5, 10, 15, 30, 60, 300, 600, 900, 1800, 3600, 10800, 14400, 21600, 43200

        ////image_file attribute (table: `atFileSettings`)
        //'akFileManagerMode' => 0, //Input Format: 0 (File Manager Selector), 5 (HTML Input)

        ////select attribute (table: `atSelectSettings`)
        //'akSelectAllowMultipleValues' => FALSE, //Multiple Values: TRUE, FALSE
        //'akDisplayMultipleValuesOnSelect' => FALSE, //Single Value: TRUE, FALSE
        //'akHideNoneOption' => FALSE, //Hide None Option: TRUE, FALSE
        //'akSelectAllowOtherValues' => FALSE, //User Submissions: TRUE, FALSE
        //'akSelectOptionDisplayOrder' => 'display_asc', //Option Order: 'display_asc', 'alpha_asc', 'popularity_desc'
        ////Adding Options: check below this code block

        ////topic attribute (table: `atTopicSettings`)
        //'topicTreeID' => $topicTreeID, //Topic Tree: find id here: /index.php/dashboard/system/attributes/topics OR in the table: `TopicTrees`
        //'akTopicParentNodeID' => $topicParentNodeID, //Topic Default Parent Node: find id in the table: `TreeNodes`
        //'akTopicAllowMultipleValues' => TRUE, //Allow multiple nodes to be chosen: TRUE, FALSE

        ////express entity attribute (table: `atExpressSettings`)
        //'exEntityID' => $entityID, //Entity: find id in the table: `ExpressEntities`

        ////address attribute (table: `atAddressSettings`)
        //'akDefaultCountry ' => '', //Available Countries
        //'akHasCustomCountries ' => '', //Default Country
        //'customCountries ' => '', 
        //'akGeolocateCountry ' => '', //Suggest the Country from the user IP address: TRUE, FALSE
    );
    $attr = CollectionAttributeKey::add( $attr_type, $desc, $pkg = null);

    //add option to an 'option list' attribute
    //$attrOption = SelectAttributeTypeOption::add($attr, 'Option 1'); //add options
    //$attrOption = SelectAttributeTypeOption::add($attr, 'Option 2'); //"
}
```

#### Delete an attribute
```PHP
...

//delete options of an 'option list' attribute
...
```

#### Add an attribute set
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;

$akc = AttributeKeyCategory::getByHandle('collection');
$akc->setAllowAttributeSets(AttributeKeyCategory::ASET_ALLOW_SINGLE);
$attrSet = $akc->addSet('my_set', t('My Set'), $pkg = null, $locked = null); 
    
$attrSetID = $attrSet->getAttributeSetID(); //echo $attrSetID;
$attrSetHandle = $attrSet->getAttributeSetHandle(); //echo $attrSetHandle;
$attrSetName = $attrSet->getAttributeSetName(); //echo $attrSetName;
```



## Files



### A Files


#### Get a file by a unique identifier
```PHP
$file = \File::getByID(1); //by ID
```

#### Get a file data
```PHP
echo $file->getFileID(); //file ID
echo $file->getFileName(); //file name

echo $file->getURL(); //direct url
echo $file->getDownloadURL(); //tracked url
echo $file->getRelativePath();echo "<br><br>";
echo $_SERVER['DOCUMENT_ROOT'].$file->getRelativePath();echo "<br><br>";

echo $file->getTitle();
echo $file->getDescription();
echo $file->getTags(); //string
print_r($file->getTagsList()); //array

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

//file version
$fileVersion = $file->getApprovedVersion();
```

#### Get a file attribute
```PHP
echo $file->getAttribute('width');
```

#### Get list of attributes of a file
```PHP
//first get the approved version of the file
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
foreach ((array)$files as $file) {
    echo $file->getFileID();
}
```

#### Get list of files with pagination
```PHP
$fileList = new FileList();

$pagination = $fileList->getPagination();
$pagination->setMaxPerPage(5);
$files = $pagination->getCurrentPageResults();

//echo count($files);
foreach ((array)$files as $file) {
    echo $file->getFileID().'-'.$file->getFileName().'<br/>';
}

//pagination buttons
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3. 

//pagination functions
$pagination->setCurrentPage(1);
//$pagination->setCurrentPage($_GET['ccm_paging_p'] ?? 1); //in case the result is not generated correctly based on current page number
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of files
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
```
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

#### Filter a file list
```PHP
$FileList->filterByType(\Concrete\Core\File\Type\Type::T_IMAGE); //by type (T_IMAGE, T_TEXT, T_AUDIO, T_DOCUMENT, T_APPLICATION, T_UNKNOWN)
$FileList->filterByExtension('png'); //by extension
$FileList->filterByKeywords('foobar'); //by keywords
$FileList->filterBySize(1024, 2048); //Only includes files that are between 1MB and 2MB in Size
$FileList->filterByAttribute('width', 200, '>='); //Only include files where "width" is 200 or greater.
$FileList->filterByDateAdded($date, $comparison = '='); //by date added
$FileList->filterByTags($tags); //by tags

//SET
if ($fileSet) $FileList->filterBySet($fileSet); //by set (check 'Get a file set' for how to get a set)
$FileList->filterByNoSet(); //files in No Sets
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
foreach ((array)$files as $file) {
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
$fileSet = FileSet::getByID(1); //by ID
$fileSet = FileSet::getByName('File Set Name'); //name
```

#### Get a file folder
```PHP
$folder = Node::getByID($folderID); //by ID
$folder = Node::getNodeByName('My Folder'); //by name, not working
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
$fileSet = Set::createAndGetSet('My File Set', Set::TYPE_PUBLIC);
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
    print 'Yes, they are!';
}

print $u->getUserID();

$groups = $u->getUserGroups();
foreach($groups as $groupID) {
    $group = \Concrete\Core\User\Group\Group::getByID($groupID);
    print $group->getGroupName();
}
```

#### Get a user by a unique identifier
```PHP
$user = User::getByUserID(1); //by ID
//User::getByUserID(3, true); // Now user 3 is logged in.
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
$ui = UserInfo::getByID(1); //by ID
$ui = UserInfo::getByUserName('admin'); //by username
$ui = UserInfo::getByEmail('jane@concrete5.org'); //by email
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
foreach ((array)$users as $user) {
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
foreach ((array)$users as $user) {
    echo $user->getUserID().'-'.$user->getUserName().'<br/>';
}

//pagination buttons
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3.

//pagination functions
$pagination->setCurrentPage(1);
//$pagination->setCurrentPage($_GET['ccm_paging_p'] ?? 1); //in case the result is not generated correctly based on current page number
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of pages
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
```

#### Filter a user list
```PHP
$userList->filterByKeywords('andrew'); //by keywords (simple)
$userList->filterByFulltextKeywords('foobar'); //by keywords (advanced)
$userList->filterByUsername('foobar'); //by username
$userList->filterByFuzzyUsername('foobar'); //by username(fuzzy)
$userList->filterByDateAdded($date, $comparison = '='); //by date added
$userList->includeInactiveUsers();
$userList->includeUnvalidatedUsers();
$userList->filterByIsActive($isActive);
$userList->filterByIsValidated($isValidated);

//by group
$userList->filterByGroup('Administrators'); 
//OR send the group object
$group = \Group::getByName('Administrators');
$userList->filterByGroup($group);

$group = \Group::getByName('Administrators');
$userList->filterByGroup($group, false); //return all non-admins

$userList->filterByInAnyGroup($groups, $inGroups = true) //multiple group


//by attribute:
$userList->filterByAttribute($column, $value, $comparison = '=');
//OR
$userList->filterByAttributeHandle($value, $comparison = '='); //for 'attribute_handle' => filterByAttributeHandle/ 'is_featured' => filterByIsFeatured(TRUE);

// by attribute: checkbox(boolean)
$userList->filterByAttribute('attribute_handle', TRUE);
$userList->filterByAttribute('attribute_handle', FALSE);

//by attribute: string (text/text area/email/URL, Phone NUmber, etc)
$userList->filterByAttribute('attribute_handle', 'cat'); //equal to 'cat'
$userList->filterByAttribute('attribute_handle', '%'.'cat'.'%', 'LIKE'); //has 'cat' anywhere in the string

//by attribute: number
$userList->filterByAttribute('attribute_handle', 5); //equal to 5
$userList->filterByAttribute('attribute_handle', 5, '>='); //greater than or equal to 5

//by attribute: date/time
$userList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start)); //equal to $stat
$userList->filterByAttribute('attribute_handle', date('Y-m-d H:i:s', $start), '>='); //greater than or equal to $start

// by attribute: option list
//$userList->filterBySelectAttribute($akHandle, $value); //legacy. not working

//for filtering based on a single option:
$userList->filterByAttribute('attribute_handle', $value1);

//for filtering based on multiple options: It seems not working properly for array with multiple options. use manual method instead.
$userList->filterByAttribute('attribute_handle', array($value1, $value2)); 

//have either $value1 OR $value2 value
$userList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$userList->getQueryObject()->orWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

//have both $value1 AND $value2 values
$userList->getQueryObject()->where("ak_attribute_handle LIKE '%\n".$value1."\n%'");
$userList->getQueryObject()->andWhere("ak_attribute_handle LIKE '%\n".$value2."\n%'");

//by attribute: topics
//first get nodes:
//use \Concrete\Core\Tree\Node\Node as TreeNode;
$topicNode1 = TreeNode::getByID(1);
$topicNode2 = TreeNode::getByID(2);

$userList->filterByAttribute('attribute_handle', array($topicNode1, $topicNode2));

//OR: Category
$topicCategory1 = TreeNode::getByID(1);
$userList->filterByAttribute('attribute_handle', array($topicCategory1));

```

#### Sort a user list
```PHP
$userList->sortByUserID(); //by ID asc
$userList->sortByUserName(); //by username asc
$userList->sortByDateAdded(); //by date added desc

$userList->sortBy('u.uID', 'desc'); //by ID desc
$userList->sortBy('u.uName', 'asc'); //by username desc
$userList->sortBy('u.uDateAdded', 'asc'); //by date added asc

$userList->sortBy('ak_attribute_handle', 'desc'); //by an attribute: 'ak_' + attribute_handle
```

### User operation


#### Add a user
```PHP
$ui = \UserInfo::add(array(
    'uName' => 'andrew',
    'uEmail' => 'andrew@concrete5.org', 
    'uPassword' => 'kittens',
    //'uDefaultLanguage' => '', //an ISO language code for the user's default language
    //'uIsValidated' => '', //whether the user is validated. 1 for validated, 0 for definitely unvalidated, and -1 for unknown (which is the default on sites that don't employ user validation
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

//change password
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
$ui = UserInfo::getByID(1); //by ID
if ($ui) {
    $ui->setAttribute('attribute_handle', 'value');
}    
```

#### Clear an attribute of a user
```PHP
$ui = UserInfo::getByID(1); //by ID
if ($ui) {
    $ui->clearAttribute('attribute_handle');
}    
```

### Attributes


#### Get an attribute
Same as [`Collections`](#get-an-attribute). Just replace 'Collection' with 'File'.

#### Add an attribute
Same as [`Collections`](#add-an-attribute). Just replace 'Collection' with 'File'.

#### Add an attribute set
Same as [`Collections`](#add-an-attribute-set). Just replace 'Collection' with 'File'.

## Topics



#### Schema
- Topic Tree
	- Category
		- Topic (Node)

#### Get a Topic Tree 
```PHP
//use \Concrete\Core\Tree\Type\Topic as TopicTree;

$topicTree = TopicTree::getByID(1); //by ID
$topicTree = TopicTree::getByName('Blog Entries'); //by name

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

//Category
$topicCategory = TreeNode::getByID($catID);
$topicCategory = TreeNode::getNodeByName($catName); //not working (error)

//Topic (Node)
$topicNode = TreeNode::getByID($nodeID);
$topicNode = TreeNode::getNodeByName($nodeName); //not working (error)
```

#### Add a Category/Node
```PHP
//use Concrete\Core\Tree\Type\Topic as TopicTree;
//use Concrete\Core\Tree\Node\Node as TreeNode;
//use Concrete\Core\Tree\Node\Type\Topic as TopicTreeNode;
//use Concrete\Core\Attribute\Key\Category;

//get root Category
$topicCategory = TreeNode::getByID($topicTree->getRootTreeNodeObject()->treeNodeID);
//OR: Get anotehr category by its handle
//from https://documentation.concrete5.org/developers/topics/working-topics -> not working (error)
$topicCategory = new Category();
$topicCategory->getByHandle('Another Category');
//OR:
$topicCategory = TreeNode::getByID($catID);
$topicCategory = TreeNode::getNodeByName($catName); //not working (error)

//add a new topic (node)
$topicNode = TopicTreeNode::add('New Node', $topicCategory);

//add a new category
$topicCategory->add('New Category below seected $topicCategory', $topicCategory);
```

## Attributes



#### List of attribute set categories (collection/user/file/site/event)
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;
$categories = AttributeKeyCategory::getList();		
foreach ((array)$categories as $category) {
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
    foreach ((object)$sets as $set) {
        $setID = $set->getAttributeSetID(); //echo $setID);
        $setHandle = $set->getAttributeSetHandle(); //echo $setHandle;
        $setName = $set->getAttributeSetDisplayName(); //echo $setName;
	}
}	
```

### Attrubute Set


#### A set
```PHP
$attrSet = AttributeSet::getByID('attribute_set_id'); //by ID
$attrSet = AttributeSet::getByHandle('attribute_set_handle'); //by handle
```

#### Attributes in a set
```PHP
$attrs = $attrSet->getAttributeKeys();
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
//regular area
$a = new Area("Main");
//$a->enableGridContainer(); //enable grid container in area
//$a->setAreaGridMaximumColumns(12);
//if ($c->isEditMode()); //do something
//if ($a->getTotalBlocksInArea($c) > 0); //do something
$a->display($c);

//global area
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


## Single Pages



## Blocks



## Stacks



## Packages



## Express Entries



### Express Entity


#### Create the entity
```PHP
$eObj = Express::getObjectByHandle('marina');
if (!is_object($eObj)) {
    
    $eObj = Express::buildObject('marina', 'marinas', 'Marina', $pkg = null);

    ////general checkboxes (HELP WANTED)
    //use Concrete\Core\Entity\Attribute\Key\Key;
    //'Content included in search index' checkbox 
    //akIsSearchableIndexed --> setIsAttributeKeyContentIndexed()
    //'Field available in advanced search' checkbox 
    //akIsSearchable--> setIsAttributeKeySearchable()

    ////settings
    //text
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TextSettings();
    $settings->setPlaceholder('Enter Marina Name Here');
    $eObj->addAttribute('text', 'Name', 'marina_name', $settings);

    //textarea
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TextareaSettings();
    $settings->setMode('text'); //values: 'text', 'rich_text'
    $eObj->addAttribute('textarea', 'Description', 'marina_description', $settings);

    //checkbox
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\BooleanSettings();
    $settings->setIsCheckedByDefault(FALSE);
    $settings->setCheckboxLabel('Checkbox Label');
    $eObj->addAttribute('boolean', 'Active', 'marina_active', $settings);

    //date_time
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\DateTimeSettings();
    $settings->setUseNowIfEmpty(FALSE);
    $settings->setMode('date_time');
    $settings->setTextCustomFormat('Y-m-d H:i:s');
    $settings->setTimeResolution(60);
    $eObj->addAttribute('date_time', 'Establishment', 'marina_establishment', $settings);
    
    //image_file
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\ImageFileSettings();
    $settings->setModeToFileManager(); //OR $settings->setModeToHtmlInput();
    $eObj->addAttribute('image_file', 'Image', 'marina_image', $settings);

    //number
    $eObj->addAttribute('number', 'Size', 'marina_size');
    
    //select
    $eObj->addAttribute('select', 'Facilities', 'marina_facilities', $settings);
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\SelectSettings();
    $settings->setAllowMultipleValues(FALSE);
    $settings->setDisplayMultipleValuesOnSelect(FALSE);
    $settings->setHideNoneOption(FALSE);
    $settings->setAllowOtherValues(FALSE);
    $settings->setDisplayOrder('display_asc');
    
    //address
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\AddressSettings();
    $settings->setCustomCountries(array('US','UK'));
    $settings->setHasCustomCountries(true);
    $settings->setDefaultCountry('UK');
    $eObj->addAttribute('address', 'Address', 'marina_address', $settings);
    
    //telephone
    $eObj->addAttribute('telephone', 'Telephone', 'marina_telephone');
    
    //url
    $eObj->addAttribute('url', 'Website', 'marina_website');
    
    //email
    $eObj->addAttribute('email', 'Email', 'marina_email');
    
    //rating
    $eObj->addAttribute('rating', 'Rating', 'marina_rating');
    
    //topics
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\TopicsSettings();
    $settings->setTopicTreeID($topicTreeID);
    $settings->setParentNodeID($topicParentNodeID);
    $settings->setAllowMultipleValues(TRUE);
    $eObj->addAttribute('topics', 'District', 'marina_district', $settings);
    
    //social_links
    $eObj->addAttribute('social_links', 'twitter', 'marina_twitter');
    
    //express
    $settings = new \Concrete\Core\Entity\Attribute\Key\Settings\ExpressSettings();
    $settings->setEntity($entityID);
    $eObj->addAttribute('express', 'Personnels', 'marina_personnels');
    
    //calendar
    $eObj->addAttribute('calendar', 'Calendar', 'marina_calendar');
    
    //calendar_event
    $eObj->addAttribute('calendar_event', 'Event', 'marina_event');
    
    //page_selector
    $eObj->addAttribute('page_selector', 'Info Page', 'marina_info_page');

    $eObj->save();

    //creating an Express Object Form
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


## Language



## Constants



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

configNamespace | configGroup | configItem | configValue
--------------- | ----------- | ---------- | -----------
my_package | front_end | show_header | 1

#### FileSystem
File: *`application\config\generated_overrides\configNamespace\configGroup.php`*
```PHP
return array(
    'configItem' => TRUE,
    'configItem2' => 2,
    'configItem3' => 'Hey!',
);
```

### Different ways to read and write config values


#### 1: Using a Package object
```PHP
$packageObject = \Package::getByHandle('my_package');

//Database

//save config value
$packageObject->getConfig()->save('front_end.show_header', true);
//get config value
$showHeader = $packageObject->getConfig()->get('front_end.show_header');
//has config value
$hasShowHeader = $packageObject->getConfig()->has('front_end.show_header');
//set config value
//$packageObject->getConfig()->set('front_end.show_header'); //not working
//clear config value
//$packageObject->getConfig()->clear('front_end.show_header'); //not working


//FileSystem:

//save config value
$packageObject->getFileConfig()->save('front_end.show_header', true);
//get config value
$showHeader = $packageObject->getFileConfig()->get('front_end.show_header');
//has config value
$hasShowHeader = $packageObject->getFileConfig()->has('front_end.show_header');
//set config value
//$packageObject->getConfig()->set('front_end.show_header'); //not working
//clear config value
//$packageObject->getConfig()->clear('front_end.show_header'); //not working
```

#### 2: Using a service provider
```PHP
$key = 'configNamespace::configGroup.configItem';
$value = '5';
$default = -1;

//Database
$configDatabase = \Core::make('config/database');
$configDatabase->save($key, $value);
$configDatabase->get($key, $default);
$configDatabase->has($key);
//$configDatabase->set($key, $value); //not working
//$configDatabase->clear($key); //not working

//FileSystem:
$configFile = \Core::make('config');
$configFile->save($key, $value);
$configFile->get($key, $default);
$configFile->has($key);
//$configFile->set($key, $value); //not working
//$configFile->clear($key); //not working
```

#### 3: Using Config

```PHP
$key = 'configNamespace::configGroup.configItem';
$value = '5';
$default = -1;

//FileSystem:
\Config::save($key, $value);
\Config::get($key, $default);
\Config::has($key);
//\Config::set($key, $value); //not working
//\Config::clear($key); //not working
```

## Helpers



#### General
```PHP
//\concrete\bootstrap\helpers.php

//Translate text (simple form).
t($text);

//Translate text (plural form).
t2($singular, $plural, $number);

//Translate text (simple form) with a context.
tc($context, $text);

//Security helper.
h($input);

//Returns $string in CamelCase.
camelcase($string, $leaveSlashes = false);

//Returns CamelCase string as camel_case.
uncamelcase($string);

//Fills an object properties from an array.
array_to_object($o, $array);

//Dumps information about a variable in a way that can be used with Doctrine recursive objects.).
var_dump_safe($o, $echo = true, $maxDepth = true);

//Generate the PHPDoc for a set of defined variables.
output_vars(array $get_defined_vars, $valueOfThis = null, $return = false);
```

#### Number helper
```PHP
$nh = $app->make('helper/number');

$nh->flexround($value); //Rounds the value only out to its most significant digit.
$nh->trim($value); //Remove superfluous zeroes from a string containing a number.
$nh->isNumber($string); //Checks if a given string is valid representation of a number in the current locale.
$nh->isInteger($string); //Checks if a given string is valid representation of an integer in the current locale.
$nh->format($number, $precision = null); //Format a number with grouped thousands and localized decimal point/thousands separator.
$nh->unformat($string, $trim = true, $precision = null); //Parses a localized number representation and returns the number (or null if $string is not a valid number representation).
$nh->formatSize($size, $forceUnit = ''); //Formats a size (measured in bytes, KB, MB, ...).
$nh->getBytes($val); //Nice and elegant function for converting memory. Thanks to @lightness races in orbit on Stackoverflow.

//\concrete\src\Utility\Service\Number.php
```

#### Text helper
```PHP
$th = $app->make('helper/text');

$th->encodePath($path); //URL-encodes collection path.
$th->match($pattern, $value); //Determine if a given string matches a given pattern.
$th->lugSafeString($handle, $maxlength = 128); //Remove unsafe characters for URL slug.
$th->sanitize($string, $max_length = 0, $allowed = ''); //Strips tags and optionally reduces string to specified length.
$th->email($email); //Leaves only characters that are valid in email addresses (RFC).
$th->alphanum($string); //Leaves only characters that are alpha-numeric.
$th->entities($v); //always use in place of htmlentites(), so it works with different languages.
$th->decodeEntities($v); //Decodes html-encoded entities (for instance: from '&gt;' to '>').
$th->specialchars($v); //A concrete5 specific version of htmlspecialchars(). Double encoding is OFF, and the character set is set to your site's.
$th->shorten($textStr, $numChars = 255, $tail = '…'); //An alias for shorten().
$th->shortText($textStr, $numChars = 255, $tail = '…'); //Like sanitize, but requiring a certain number characters, and assuming a tail.
$th->camelcase($string); //Takes a string and turns it into the CamelCase or StudlyCaps version.
$th->twitterAutolink($input, $newWindow = 0, $withSearch = 0); //automatically add hyperlinks to any twitter style @usernames in a string.
$th->makenice($input); //Runs a number of text functions, including autolink, nl2br, strip_tags. Assumes that you want simple text comments but with a few niceties.
$th->prettyStripTags($input, $allowedTags = null); //Runs strip_tags but ensures that spaces are kept between the stripped tags.
$th->autolink($input, $newWindow = false, $defaultProtocol = 'http://'); //Scans passed text and automatically hyperlinks any URL inside it.
$th->fnmatch($pattern, $string); //A wrapper for PHP's fnmatch() function, which some installations don't have.
$th->uncamelcase($string); //Takes a CamelCase string and turns it into camel_case.
$th->unhandle($string); //Takes a handle-based string like "blah_blah" or "blah-blah" or "blah/blah" and turns it into "Blah Blah".
$th->handle($handle, $leaveSlashes = false); //Takes a string and turns it into a handle.
$th->sanitizeFileSystem($handle); //Determines whether a string matches a particular pattern.
$th->urlify($handle, $max_length = null, $locale = '', $removeExcludedWords = true); //Takes text and returns it in the "lowercase-and-dashed-with-no-punctuation" format.
$th->asciify($text, $locale = ''); //Takes text and converts it to an ASCII-only string (characters with code between 32 and 127, plus \t, \n and \r).
$th->wordSafeShortText($textStr, $numChars = 255, $tail = '…'); //alias of shortenTextWord().
$th->shortenTextWord($textStr, $numChars = 255, $tail = '…'); //Shortens and sanitizes a string but only cuts at word boundaries.
$th->filterNonAlphaNum($val); //Strips out non-alpha-numeric characters.
$th->highlightSearch($value, $searchString); //Highlights a string within a string with the class ccm-highlight-search.
$th->formatXML($xml); //Formats a passed XML string nicely.
$th->appendXML(\SimpleXMLElement $root, \SimpleXMLElement $new); //Appends a SimpleXMLElement to a SimpleXMLElement.

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
$form = $app->make('helper/form'); //no need to initiate

$form->setRequest(Request $request); //Set the request instance.
$form->getRequest(); //
echo $form->action($action, $task = null); //Returns an action suitable for including in a form action property.
echo $form->submit($key, $value, $miscFields = [], $additionalClasses = ''); //Creates a submit button.
echo $form->button($key, $value, $miscFields = [], $additionalClasses = ''); //Creates a button.
echo $form->label($forFieldID, $innerHTML, $miscFields = []); //Creates a label tag.
echo $form->file($key, $miscFields = []); //Creates a file input element.
echo $form->hidden($key, $value = null, $miscFields = []); //Creates a hidden form field.
echo $form->checkbox($key, $value, $isChecked = false, $miscFields = []); //Generates a checkbox.
echo $form->textarea($key, $valueOrMiscFields = '', $miscFields = []); //Creates a textarea field.
echo $form->radio($key, $value, $checkedValueOrMiscFields = '', $miscFields = []); //Generates a radio button.
echo $form->getRequestValue($key); //Checks the request (first POST then GET) based on the key passed.
echo $form->text($key, $valueOrMiscFields = '', $miscFields = []); //Renders a text input field.
echo $form->number($key, $valueOrMiscFields = '', $miscFields = []); //Renders a number input field.
echo $form->email($key, $valueOrMiscFields = '', $miscFields = []); //Renders an email input field.
echo $form->telephone($key, $valueOrMiscFields = '', $miscFields = []); //Renders a telephone input field.
echo $form->url($key, $valueOrMiscFields = '', $miscFields = []); //Renders a URL input field.
echo $form->search($key, $valueOrMiscFields = '', $miscFields = []); //Renders a search input field.
echo $form->select($key, $optionValues, $valueOrMiscFields = '', $miscFields = []); //Renders a select field.
echo $form->selectCountry($key, $selectedCountryCode = '', array $configuration = [], array $miscFields = []); //Renders a select menu to choose a Country.
echo $form->selectMultiple($key, $optionValues, $defaultValues = false, $miscFields = []); //Renders a multiple select box.
echo $form->password($key, $valueOrMiscFields = '', $miscFields = []); //Renders a password input field.
echo $form->getAutocompletionDisabler(); //Generates HTML code that can be added at the beginning of a form to disable username/password autocompletion.
echo $form->processRequestValue($key, $type = 'post'); //Checks the request based on the key passed.
echo $form->inputType($key, $type, $valueOrMiscFields, $miscFields); //Internal function that creates an <input> element of type $type. Handles the messiness of evaluating $valueOrMiscFields. Assigns a default class of ccm-input-$type.
echo $form->parseMiscFields($defaultClass, $attributes); //Create an HTML fragment of attribute values, merging any CSS class names as necessary.

//\concrete\src\Form\Service\Form.php
```

#### Form (color picker) helper
```PHP
$cpfh = $app->make('helper/form/color');

echo $cpfh->output($inputName, $value = null, $options = array()); //Creates form fields and JavaScript includes to add a color picker widget.
//echo $cpfh->output('background-color', '#f00');

//\concrete\src\Form\Service\Widget\Color.php
```

#### Form (date/time) helper
```PHP
$dtfh = $app->make('helper/form/date_time');

$dtfh->translate($field, $arr = null, $asDateTime = false); //Takes a "field" and grabs all the corresponding disparate fields from $_POST and translates into a timestamp.
echo $dtfh->datetime($field, $value = null, $includeActivation = false, $calendarAutoStart = true, $classes = null, $timeResolution = 60, array $datePickerOptions = array()); //Creates form fields and JavaScript calendar includes for a particular item (date/time string representations will be converted from the user system-zone to the time-zone).
echo $dtfh->date($field, $value = null, $calendarAutoStart = true, array $datePickerOptions = array()); //Creates form fields and JavaScript calendar includes for a particular item but includes only calendar controls (no time, so no time-zone conversions will be applied).
echo $dtfh->selectNearestValue(array $values, $wantedValue); //hoose an array value nearest to a specified value. Useful when we work with time resolutions.

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

#### Form (rating) helper
```PHP
$rfh = $app->make('helper/form/rating');

echo $rfh->rating($prefix, $value = null, $includeJS = true); //

//\concrete\src\Form\Service\Widget\Rating.php
```

#### Form (attribute) helper
```PHP
$afh = $app->make('helper/form/attribute');

$afh->setAttributeObject($obj); //
$afh->display($key, $required = false, $includeLabel = true, $template = 'composer'); //


//usage for page(collection) attributes
$afh = $app->make('helper/form/attribute');
$key = CollectionAttributeKey::getByHandle('page_attribute_handle'); //get attribute object
echo $afh->display($key);

//usage for file attributes
$afh = $app->make('helper/form/attribute');
$key = FileAttributeKey::getByHandle('file_attribute_handle'); //get attribute object
echo $afh->display($key);

//usage for userinfo attributes
$afh = $app->make('helper/form/attribute');
$key = UserAttributeKey::getByHandle('user_attribute_handle'); //get attribute object
echo $afh->display($key);

//\concrete\src\Form\Service\Widget\Attribute.php
```

#### Form (typography) helper
```PHP
$tfh = $app->make('helper/form/typography');
//OR
$tfh = $app->make('helper/form/font');

echo $tfh->output($inputName, $value = array(), $options = array()); //Creates form fields and JavaScript includes to add a font picker widget.

//\concrete\src\Form\Service\Widget\Typography.php
```

#### Concrete URL helper
```PHP
$cuh = $app->make('helper/concrete/urls');

$cuh->getPackageIconURL($pkg); //Gets a full URL to an icon for a particular application.
$cuh->getPackageURL($pkg); //Get the package's URL.
$cuh->getToolsURL($tool, $pkgHandle = null); //Gets a URL to reference a script in the tools directory
$cuh->getBlockTypeIconURL($bt); //Gets a full URL to an icon for a particular block type.
$cuh->getBlockTypeAssetsURL($bt, $file = false); //Gets a full URL to the directory containing all of a block's items, including JavaScript, tools, icons, etc...
$cuh->getBlockTypeJavaScriptURL($bt); //Gets a full URL to a block's JavaScript file (if one exists).
$cuh->getBlockTypeToolsURL($bt); //@deprecated: Gets a full URL to a block's tools directory

//\concrete\src\Application\Service\Urls.php
```

#### Asset library (file manager) helper
```PHP
$alh = $app->make('helper/concrete/asset_library');
//OR
$alh = $app->make('helper/concrete/file_manager');

$alh->file($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a file.
$alh->image($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick an image file.
$alh->video($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a video file.
$alh->text($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a text file.
$alh->audio($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick an audio file.
$alh->doc($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a document file.
$alh->app($inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a application file.
$alh->fileOfType($type, $inputID, $inputName, $chooseText, $preselectedFile = null, $args = []); //Sets up a form field to let users pick a file of a specific type.

//\concrete\src\Application\Service\FileManager.php
```

#### Validation error helper
```PHP
$errors = $app->make('error');
//OR
$errors = $app->make('helper/validation/error');

$errors->add($e, $fieldName = null, $fieldDisplayName = null); //Add an error message/object or exception to the internal error array (error messages are in plain text if not otherwise specified).
$errors->addHtml($e, $fieldName = null, $fieldDisplayName = null); //Add an error message/object or exception to the internal error array (error messages are in HTML if not otherwise specified).
$errors->getList(); //Get the list of errors contained in this error list.
$errors->has(); //Returns whether or not this error list has more than one error registered within it.
$errors->toText(); //Render this error list as a plain text.
$errors->containsField($field); //Does this list contain error associated to a field?
$errors->getMessage($field); //Get the error message (if any) associated to a field.
$errors->createResponse($errorCode = JsonResponse::HTTP_BAD_REQUEST); //Create a JSON response describing the errors in this list.

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
//database connection
$db = $app->make(\Concrete\Core\Database\Connection\Connection::class);

//prepare any query
$statement = $db->executeQuery('SELECT * FROM `myTable` WHERE `id`>?;', array(0)); 
	
//echo $statement->rowCount(); //number of SELECTed/UPDATEd/DELETEd rows
//echo $statement->getSqlQuery(); //prepared SQL //not working

//iterate through rows
$rows = $statement->fetchAll(); //print_r($rows);
foreach ($rows as $row) {
    print_r($row);
}
//OR:
while ($row = $statement->fetch()) {
    //print_r($row);
}	

//Prepares and executes an SQL query and returns the FIRST row of the result as an associative array.
$row = $db->fetchAssoc('SELECT * FROM `myTable` WHERE `id` = ?;', array(1)); //print_r($row);

//Prepares and executes an SQL query and returns the result as an associative array.
$rows = $db->fetchAll('SELECT `name` FROM `myTable`;'); //print_r($rows);

//Prepares and executes an SQL query and returns the value of a single column of the first row of the result.
$column = $db->fetchColumn('SELECT `name` FROM `myTable` WHERE id = ?;', array($id)); //echo $column;


//INSERT
$statement = $db->executeQuery('INSERT INTO `myTable` (`name`, `url`) VALUES (?, ?);', array('Name 1', 'URL 1')); 
//echo $db->lastInsertId(); //last inserted id
//echo $statement->rowCount(); //number of affected rows

//UPDATE
$statement = $db->executeQuery('UPDATE `myTable` SET name = ? WHERE `id` = ?;', array('new name', 1)); 
//echo $statement->rowCount(); //number of affected rows

//DELETE
$statement = $db->executeQuery('DELETE FROM `myTable` WHERE `id` = ?;', array(1)); 
//echo $statement->rowCount(); //number of affected rows
```
For more check [`here`](https://www.doctrine-project.org/api/dbal/2.5/Doctrine/DBAL/Connection.html)

#### Another database
```PHP
//new database connection info in /appilication/config/database.php
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
//see logs at /dashboard/reports/logs
```

#### Get environment
```PHP
$environment = $app->environment(); //echo $environment;
```

#### Clear site cache
```PHP
$app->clearCaches();
```
