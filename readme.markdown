#Readme


##Overview

Ext JS OrgChart is a plugin that allows you to render structures with nested elements in a easy-to-read tree structure. To build the tree all you need is to make a single line call to the plugin and supply the root element of tree structure prepared in Javascript Objects. This plugin has been adopted from [jOrgChart plugin](https://github.com/wesnolte/jOrgChart) prepared by [@wesnolte](http://twitter.com/wesnolte)

Features include:

* Very easy to use javascript object tree structure.
* Objects can be filled up based on required logic, plugin will take care of rendering tree structure.
* Object structure allows to fill in data from any external source. E.g. json objects
* Nodes can contain any amount of HTML.
* Easy to style.
* HTML rendered in the nodes can have qtip markup so that easy QuickTip can be provided

Works with:

* Works with IE8+, Chrome 30+ and FF 25+
* Tested with Ext JS 3.4.0


![Ext JS OrgChart](http://i.imgur.com/iKKjWs9.png "Ext JS OrgChart")

----

##Expected Markup & Example Usage

To get up and running you'll need very few things. 

-----

###The JavaScript Libraries & CSS

You need to include the Ext JS as well as the Ext JS OrgChart libraries. For example:

	<script type='text/javascript' src='http://cdn.sencha.io/ext-3.4.0/adapter/ext/ext-base.js'></script>
	script type="text/javascript" src="http://cdn.sencha.io/ext-3.4.0/ext-all-debug.js"></script>
	<script type="text/javascript" src="ExtJSOrgChart.js"></script>

As part of Ext JS library you will require to include style sheets also. 

	<link href="http://extjs-public.googlecode.com/svn/tags/extjs-3.4.0/release/resources/css/ext-all.css" rel="stylesheet" type="text/css" />

In example I have used gray theme of Ext JS which is optional to include.

	<link href="http://extjs-public.googlecode.com/svn/tags/extjs-3.4.0/release/resources/css/xtheme-gray.css" rel="stylesheet" type="text/css" />
  
The core CSS is necessary to perform some of the basic styling i.e.

    <link rel="stylesheet" href="css/ExtJSOrgChart.css"/>
    <link rel="stylesheet" href="css/custom.css"/>

----

###The HTML

You'll need to construct a nested object structure that represents your node nesting. For example below hard coded content is used to prepare tree node structure: 

	//prepare root node
	var rootNode = new ExtJSOrgChart.createNode(1,"<a ext:qtip=\"<strong>This is a quick tip from markup!<br/>Add tooltip content as ext:qtip attribute in markup itself.<br/>It will load up as quick tip here.</strong>\" href='https://github.com/shaikhmshariq/ExtJSOrgChart'>Food</a>");
	
	//add child nodes under root node
	rootNode.addChild(new ExtJSOrgChart.createNode(2,"Beer"));
	rootNode.addChild(new ExtJSOrgChart.createNode(3,"Vegetables").addChild(new ExtJSOrgChart.createNode(3.1,"Pumpkin")).addChild(new ExtJSOrgChart.createNode(3.2,"<a href='https://github.com/shaikhmshariq/ExtJSOrgChart'>Aubergine</a><span><p>A link and a paragraph is all we need.</p></span>")).addChild(new ExtJSOrgChart.createNode(3.3,"Cucumber")));
	rootNode.addChild(new ExtJSOrgChart.createNode(4,"Fruit").addChild(new ExtJSOrgChart.createNode(4.1,"Apple").addChild(new ExtJSOrgChart.createNode(4.10,"Granny Smith"))).addChild(new ExtJSOrgChart.createNode(4.2,"Berries").addChild(new ExtJSOrgChart.createNode(4.21,'<img src="images/raspberry.jpg" alt="Raspberry"/>'))));

This plugin works by generating the tree as a series of nested tables. Each node in the tree is represented with `<div class="node">`. You can include any amount of HTML markup. Your markup will be used within the node's `<div>` element. Any classes you attach to the `<li>` elements will be copied to the associated node, allowing you to highlight particular parts of the tree.


-----

###The Ext JS Call

And the cherry on the top is the usual call, often but not always on document load. You'll need to specify the Id of element in which you want to render the chart along with root object prepared from any external source. For example:

	ExtJSOrgChart.prepareTree({
		chartElement: 'chart',
		rootObject: rootNode,
		depth: -1
	});	
	
This call will append the markup for the OrgChart to the `chart` element by default.


------

##Sourcecode

Source code with an example is available [here](https://github.com/shaikhmshariq/ExtJSOrgChart/archive/master.zip "Example & Source").

-----

##Configuration

There are only 3 configuration options.

1. **chartElement** - used to specify which HTML element you'd like to append the OrgChart markup to.
2. **depth** - tells the code what depth to parse to. The default value of "-1" instructs it to parse like it's 1999. *[default=-1]*
4. **rootNode** - this should be root node prepared from external source through custom logic as per the requirement.
