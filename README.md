# Whale Concrete5 Cheat Sheet V8+

This is a collection of Concrete5 cheat sheets, based on the C5 V8+ source code. 

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
* [Contributors](#contributors)

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

//Page Type (not working)
$pt = $page->getPageTypeObject();
if (is_object($pt)) {
    $ptID = $pt->getPageTypeID(); //echo $ptID;
    $ptName = $pt->getPageTypeName(); //echo $ptName;
    $ptHandle = $pt->getPageTypeHandle(); //echo $ptHandle;
}        
```

#### Get page attributes
```PHP
//attribute
$attr = $page->getAttribute('attribute_handle');

//Option List: get options
foreach ((object)$attr as $option) {
    $optionID = $option->getSelectAttributeOptionID(); //echo $optionID;
    $optionValue = $option->getSelectAttributeOptionValue(); //echo $optionValue;
}

//Image/File
if ($attr) {
    $attrURL = $attr->getURL(); //echo $attrURL);
    $attrDownloadURL = $attr->getDownloadURL(); //echo $attrDownloadURL;
    $attrForceDownloadURL = $attr->getForceDownloadURL(); //echo $attrForceDownloadURL;
    $attrSize = $attr->getSize(); //echo $attrSize;
    $attrExtension = $attr->getExtension(); //echo $attrExtension;

    //image thumbnail
    $im = Core::make('helper/image');
    $thumbSrc = $im->getThumbnail($attr, 100, 100)->src; //echo $thumbSrc;
}
```

#### Get list of attributes of a page
```PHP

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
$pagination->setMaxPerPage(10);
$pagination->setCurrentPage(1);
$pages = $pagination->getCurrentPageResults();

//Pagination functions
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of pages
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3. 

//echo count($pages);
foreach ((array)$pages as $page) {
    echo $page->getCollectionID();
}
```
For custom markup check <a href='https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7' target="_blank">`here`</a>

#### Filter a page list
```PHP
$pageList->filterByParentID($cParentID); //by parent ID

$pageList->filterByKeywords('foobar'); //by keyword
$pageList->filterByFulltextKeywords('foobar'); //more advanced search by keyword

$pageList->filterByPageTypeID($ctID); //by a page type ID
$pageList->filterByPageTypeHandle('blog_entry'); //by a page type handle

$pageList->filterByPageTypeHandle(['blog_entry', 'press_release']); //by page typeS
$pageList->filterByExcludeNav(true); //by an attribute

$topicNode = \Concrete\Core\Tree\Node::getByID(24); 
$pageList->filterByBlogEntryTopic($topicNode); //by a topic

$pageList->filterBySelectAttribute($akHandle, $value); // select attribute

$pageList->filterByUserID($uID); //by user ID
$pageList->filterByIsApproved($cvIsApproved); //by is approved
$pageList->filterByIsAlias($ia); // by alias

$pageList->filterByDateAdded($date, $comparison = '='); //by date added
$pageList->filterByPublicDate($date, $comparison = '='); // by public date
$pageList->filterByDateLastModified($date, $comparison = '='); //by last modified date
$pageList->filterByNumberOfChildren($num, $comparison = '>'); // by number of children
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

$pageList->sortBy('ak_attribute_handle', 'desc'); // by an attribute: 'ak_' + attrbute_handle
```


## Files
### A Files
#### Get a file by a unique identifier
```PHP
$file = \File::getByID(1); // by ID
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
#### Get a file attributes
```PHP
echo $file->getAttribute('width');
```
#### Get list of attributes of a file
```PHP

```

#### Get list of files
```PHP
$FileList = new FileList();
$files = $FileList->getResults();

//echo count($files);
foreach ((array)$files as $file) {
    echo $file->getFileID();
}
```


## Users

#### Get a user by a unique identifier
```PHP
$user = \File::getByID(1); // by ID
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

#### Get a Collection/Page attribute
```PHP
$attr = CollectionAttributeKey::getByID(1); //by ID
$attr = CollectionAttributeKey::getByHandle('attribute_handle'); //by handle

$attrID = $attr->getAttributeKeyID(); //echo $attrID;
$attrHandle = $attr->getAttributeKeyHandle(); //echo $attrHandle;
$attrName = $attr->getAttributeKeyName(); //echo $attrName;
```
#### Get options of an 'Option List' attribute
```PHP
$attr = CollectionAttributeKey::getByHandle('attribute_handle'); //by handle
$controller = $attr->getController();
$attrOptions = $controller->getOptions();
foreach ((object)$attrOptions as $attrOption) {
    $attrOptionID = $attrOption->getSelectAttributeOptionID(); //echo $attrOptionID;
    $attrOptionValue = $attrOption->getSelectAttributeOptionValue(); //echo $attrOptionValue;
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


## Single Pages


## Blocks


## Stacks

## Express Entries


## Language


## Constants


## Configs


## Helpers

#### Number helper
```PHP
$im = Core::make('helper/number');
```

#### Text helper
```PHP
$im = Core::make('helper/text');
```

#### URL helper
```PHP
$im = Core::make('helper/url');
```

#### Image helper
```PHP
$im = Core::make('helper/image');
```


## Contributors
