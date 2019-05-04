# Whale [Concrete5](https://www.concrete5.org) Cheat Sheet V8+

This is a collection of Concrete5 cheat sheets, based on the C5 V8+ source code. 

**Contributions are welcome via [issues](https://github.com/shahroq/whale_c5_cheat_sheet/issues) and [pull requests](https://github.com/shahroq/whale_c5_cheat_sheet/pulls).**

## Table of Contents <!-- omit in toc -->
- [Pages (Collections)](#pages-collections)
  - [A page](#a-page)
    - [Get Current page](#get-current-page)
    - [Get a page by a unique identifier](#get-a-page-by-a-unique-identifier)
    - [Get a page data](#get-a-page-data)
    - [Get a page type/template](#get-a-page-typetemplate)
    - [Get a page attribute](#get-a-page-attribute)
    - [Get list of attributes of a page](#get-list-of-attributes-of-a-page)
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
- [Attributes](#attributes)
  - [Attribute operations](#attribute-operations)
    - [Add an attribute](#add-an-attribute)
    - [Delete an attribute](#delete-an-attribute)
    - [List of attribute set categories (collection/user/file/site/event)](#list-of-attribute-set-categories-collectionuserfilesiteevent)
    - [List of sets in a category](#list-of-sets-in-a-category)
    - [Get a Collection/Page attribute](#get-a-collectionpage-attribute)
    - [Get options of an 'Option List' attribute](#get-options-of-an-option-list-attribute)
  - [Attrubute Set](#attrubute-set)
    - [A set](#a-set)
    - [Attributes in a set](#attributes-in-a-set)
    - [Add a Collection/Page set](#add-a-collectionpage-set)
    - [Add a File set](#add-a-file-set)
    - [List of sets](#list-of-sets)
- [Single Pages](#single-pages)
- [Blocks](#blocks)
- [Stacks](#stacks)
- [Packages](#packages)
- [Express Entries](#express-entries)
- [Language](#language)
- [Constants](#constants)
- [Configs](#configs)
- [Helpers](#helpers)
    - [Number helper](#number-helper)
    - [Text helper](#text-helper)
    - [URL helper](#url-helper)
    - [Image helper](#image-helper)
- [System Operations](#system-operations)
  - [Database](#database)
    - [Current database](#current-database)
    - [Another database](#another-database)
  - [Misc.](#misc)
    - [Get environment](#get-environment)
    - [Clear Cache](#clear-cache)
- [Contributors](#contributors)



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
echo $page->getCollectionParentID();
echo $page->isSystemPage();
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
For custom markup check [`here`](https://documentation.concrete5.org/tutorials/styling-the-pagination-5-7)

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

$pageList->filterBySelectAttribute($akHandle, $value); //select attribute

$pageList->filterByUserID($uID); //by user ID
$pageList->filterByIsApproved($cvIsApproved); //by is approved
$pageList->filterByIsAlias($ia); //by alias

$pageList->filterByDateAdded($date, $comparison = '='); //by date added
$pageList->filterByPublicDate($date, $comparison = '='); //by public date
$pageList->filterByDateLastModified($date, $comparison = '='); //by last modified date
$pageList->filterByNumberOfChildren($num, $comparison = '>'); //by number of children
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

$pageList->sortBy('ak_attribute_handle', 'desc'); //by an attribute: 'ak_' + attrbute_handle
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
));
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
$page->addAdditionalPagePath('/blog-path-for-others');
```

#### Set/Update an attribute of a page
```PHP
$page = \Page::getByID(1); //by ID
$page->setAttribute('attribute_handle', 'value');
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
$pagination->setMaxPerPage(10);
$pagination->setCurrentPage(1);
$files = $pagination->getCurrentPageResults();

//Pagination functions
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of files
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3. 

//echo count($files);
foreach ((array)$files as $file) {
    echo $file->getFileID();
}
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

## Users



### A User

#### Get/Check current user
```PHP
$u = new User();

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
$pagination->setMaxPerPage(10);
$pagination->setCurrentPage(1);
$users = $pagination->getCurrentPageResults();

//Pagination functions
echo $pagination->getTotalResults(); //total number of results
echo $pagination->getTotalPages(); //total number of pages
echo $pagination->hasNextPage(); //To determine whether paging is necessary
echo $pagination->hasPreviousPage(); //"
echo $pagination->renderDefaultView(); //Outputs HTML for Bootstrap 3.

//echo count($users);
foreach ((array)$users as $user) {
    echo $user->getUserID();
}
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

$userList->filterByGroup('Administrators'); //by group
//OR send the group object
$group = \Group::getByName('Administrators');
$userList->filterByGroup($group);

$group = \Group::getByName('Administrators');
$userList->filterByGroup($group, false); //return all non-admins

$userList->filterByProfilePrivateMessagesEnabled(true); //by attribute

$userList->filterByInAnyGroup($groups, $inGroups = true) //multiple group
```

#### Sort a user list
```PHP
$userList->sortByDateAdded();
$userList->sortByUserName();

$userList->sortBy('ak_attribute_handle', 'desc'); //by an attribute: 'ak_' + attrbute_handle
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

## Attributes



### Attribute operations


#### Add an attribute
```PHP
//use CollectionAttributeKey;
//use Concrete\Core\Attribute\Type as AttributeType;

$key = CollectionAttributeKey::getByHandle('attr_handle');
if (!is_object($key)) {
    $attr_type = AttributeType::getByHandle('text'); 
    //$attr_type = AttributeType::getByHandle('number'); 
    //$attr_type = AttributeType::getByHandle('boolean'); //checkbox 
    //$attr_type = AttributeType::getByHandle('textarea'); 
    //$attr_type = AttributeType::getByHandle('image_file');
    //$attr_type = AttributeType::getByHandle('date_time'); 
    //$attr_type = AttributeType::getByHandle('url'); 

    $desc = array ( 
        'akHandle' => 'attr_handle',
        'akName'=> t('Attribute Name'),
        //'asID' => $attrSetID, //attribute set ID: check 'Get a set/Create a set' on how to get $attrSetID
        //'akIsSearchableIndexed' => TRUE, //Content included in search index
        //'akIsSearchable' => TRUE, //Field available in advanced search
        
        //textarea attribute
        //'akTextareaDisplayMode' => 'rich_text', //ONLY FOR 'textarea': Input Format/ values: text,rich_text

        //date_time attribute
        //'akUseNowIfEmpty' => TRUE, //ONLY FOR 'date_time': Suggest the current date/time if empty/ values: TRUE, FALSE
        //'akDateDisplayMode' => 'date_time', //ONLY FOR 'date_time': Ask User For/ values: date_time, date, date_text, text
        //'akTextCustomFormat' => 'Y-m-d H:i:s', //ONLY FOR 'date_time': Custom format/ values: PHP date function values
        //'akTimeResolution' => 60, //ONLY FOR 'date_time': Time Resolution/ values: 1, 5, 10, 15, 30, 60, 300, 600, 900, 1800, 3600, 10800, 14400, 21600, 43200
    );
    $key = CollectionAttributeKey::add( $attr_type, $desc, $pkg = null);

    //option list attrbute
    //$keyOption = SelectAttributeTypeOption::add($key, 'Option 1'); //add options
    //$keyOption = SelectAttributeTypeOption::add($key, 'Option 2'); //"
}
```

#### Delete an attribute
```PHP

```

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

#### Add a Collection/Page set
```PHP
//use Concrete\Core\Attribute\Key\Category as AttributeKeyCategory;

$akc = AttributeKeyCategory::getByHandle('collection');
$akc->setAllowAttributeSets(AttributeKeyCategory::ASET_ALLOW_SINGLE);
$attrSet = $akc->addSet('my_set', t('My Set'), $pkg = null, $locked = null); 
    
$attrSetID = $attrSet->getAttributeSetID(); //echo $attrSetID;
$attrSetHandle = $attrSet->getAttributeSetHandle(); //echo $attrSetHandle;
$attrSetName = $attrSet->getAttributeSetName(); //echo $attrSetName;
```

#### Add a File set
```PHP
```



#### List of sets
```PHP
```

## Single Pages



## Blocks



## Stacks



## Packages



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

## System Operations



### Database


#### Current database
```PHP
//database connection
$db = Database::connection();

//prepare any query
$statement = $db->executeQuery('SELECT * FROM `myTable` WHERE `id`>?;', array(0)); 
	
//echo $statement->rowCount(); //number of rows
//echo $statement->getSqlQuery(); //prepared SQL //not working


$rows = $statement->fetchAll(); //print_r($rows);
foreach ($rows as $row) {
    print_r($row);
}
//OR:
while ($row = $statement->fetch()) {
    //print_r($row);
}	

//get associated rows
$row = $db->fetchAssoc('SELECT * FROM `myTable` WHERE `id`=?;', array(1)); //print_r($row);

//get rows diretly
$rows = $db->fetchAll('SELECT `name` FROM `myTable`;'); //print_r($rows);

//get a column
$column = $db->fetchColumn('SELECT `name` FROM `myTable` WHERE id = ?;', array($id)); //echo $column;

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

$dbPricing = Database::connection('pricing');
```

### Misc.

#### Get environment
```PHP
$environment = Core::make('app')->environment(); //echo $environment;
```

#### Clear Cache
```PHP
Core::make('app')->clearCaches();
//$this->app->clearCaches();
```


## Contributors


