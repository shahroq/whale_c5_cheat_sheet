# Whale Concrete5 V8+ Cheat Sheet

This is a collection Concrete5 cheat sheet, based on the C5 8+ source code. 

**Contributions are welcome via [issues](https://github.com/shahroq/whale_c5_cheat_sheet/issues) and [pull requests](https://github.com/shahroq/whale_c5_cheat_sheet/pulls).**

## Table of Contents
* [Collections/Pages](#pages)
* [Files](#files)
* [Users](#users)
* [Single Pages](#single-pages)
* [Blocks](#blocks)
* [Stacks](#stacks)
* [Language](#language)
* [Constants](#constants)
* [Configs](#configs)
* [Helpers](#helpers)

## Collections/Pages
### A page

#### Get Current page
```PHP
$page = \Page::getCurrentPage();
```
#### Get a page by something
```PHP
$page = \Page::getByID(1); //by ID
$page = \Page::getByPath('/path/to/page'); //by path
```
#### Get data of a page
```PHP
echo $page->getCollectionName();
echo $page->getCollectionDescription();
echo $page->getCollectionDateAdded();
echo $page->getCollectionDatePublic();
echo $page->getCollectionUserID();

$attr = $page->getAttribute('attribute_handle');
```



### List of pages



## Files

## Users

## Single Pages

## Blocks

## Stacks

## Language

## Constants

## Configs

## Helpers
