Coding standards and Conventions


Using reStructuredText markup (do not use markdown syntax).


When contributing to any Zikula Project, you must follow the these standards.  These standards are recommended module development to maintain consistency across all code.




Text Editor/IDE Settings
------------------------


  - Tabs should be inserted as 4 spaces. 
  - No white space at end of lines (set to auto-remove trailing white space at end of line).
  - Text files should be in UTF-8 format.
  - Existing tab characters should be converted to spaces when found.
  - Use single line feeds (Unix line endings) for text files.
    - ref: https://help.github.com/articles/dealing-with-line-endings/


.. note::


   When using git in a Windows environment, git might be translating line endings to Windows line endings on fetch/pull and back to Unix line endings on push. See instructions on properly configuring git in a Windows environment for more information. If git is configured this way, then Windows line endings (CR followed by a LF) can be ignored while working with the file. 




Naming in General
-----------------


This overview of naming standards is expanded below.  


  - Variables, methods, and function names should only consist of numbers, letters and underscore. They must not start with a number. 
  - Class names, depending on PEAR or PHP 5.3+ namespacing, may use either underscore or the backslash.
  - Use camel casing to support improved readability.  
  - Everything except class names, should start with a lowercase letter, i.e. methods, functions and variable names. 
  - Class names must start with a capital letter.
  - Acronyms should not be all caps but follow the camel casing rules above as if they were normal words.  If they start in a variable name, method or function then start with lowercase `sqlArray`, if they appear anywhere else, they start with a capital letter, `filteredSqlStatement`.
  - Array keys should be all lowercase.
  - Constants should be in upper case letters only and may also contain numbers and underscores, but must start with a letter.




PHP Files
---------


PHP files must start with `<?php` alone on an empty line. Short-tags are not allowed (to ensure that the code works independently of whether short tags are allowed in the environment).


Immediately after the PHP opening tag, on a new line, there should be a file-level docblock.  Below is the template (year can be adjusted as apropriate.


    /**
     * Copyright 2009-2011 Zikula Foundation
     *
     * This work is contributed to the Zikula Foundation under one or more
     * Contributor Agreements and licensed to You under the following license:
     *
     * @license GNU/LGPLv3 (or at your option, any later version).
     * @package Zikula
     * @subpackage EventManager
     *
     * Please see the NOTICE file distributed with this source code for further
     * information regarding copyright and licensing.
     */


There should not be a PHP closing `?>` tag at the end of the file.




Javascript Files
----------------


Non vendor javascript files may use a shortened header:


    // Copyright 2010 Zikula Foundation, licensed LGPLv3 or any later version.




Constants
---------


Constants should be in full capital letters and may include underscores and numbers.


    define('SOMETHING', 123);
    define('SOMETHING_ELSE', 1234);
    define('SOMETHING_ELSE2', 12345);


    class Foo
    {
        const SOMETHING = 123;
        const SOMETHING_ELSE = 1234;
        const SOMETHING_ELSE2 = 12345;
    }




Variable Naming
---------------


Variable names should be in camel case with the first letter lower cases.  Variables may contain only letters, numbers and underscore (but must start with a letter or underscore).  Acronyms should not be capitalised differently to any other words.


    $foo = 1;
    $onSuccess = true;
    $generatedSql = '';
    $sqlArray = array();




Arrays
------


Array keys should always be in lower case and may use an underscore if readability is a concern.


    array('mykey' => 1);
    array('something_very_long' => 12345);




Class and Interface Naming
--------------------------


Class names should start with a capital letter and be and camel cased for each word.  Class names may not start with a number.  Use a capital letter after an underscore. Acronyms should not be capitalised differently to any other words.  Class names must consist of at least package name and class name, i.e. there must be at least one separator (with underscore or backslash) in the class name.


PEAR Naming


    MyClass_Event
    MyClass_Generator_Sql


PHP 5.3 namespaced naming


    MyClass\Event
    MyClass\Generator\Sql


Interfaces must end with the word Interface
 
    MyClass_EventInterface
    MyClass\EventInterface


Abstract classes must contain the word “Abstract” prefixing the last element in the class name.


    MyClass_AbstractController
    MyClass\AbstractController


Functions and class method names should begin with a lower case letter and be capitalised. Acronyms should not be capitalised differently to any other words.


Functions, class methods, variable, and class properties should start with a lower case letter and be camel cased. Constants should be fully upper case. Do not prefix private or protected methods with an underscore.


    function myFoo() 
    {
    }


    function sqlFoo() 
    {
    }


    function mySqlFoo() 
    {
    }


    Class Foo_Bar
    {
        const ALL = '1';
        private $number;
        protected $sqlObject;
        
        public function getSqlObject()
        {
            return $this->sqlObject();
        }


        private function setup()
        {
            // do something
        }
    }




Namespace Usage
---------------


The `namespace` directive must appear directly after the file level docblock followed by any `use` directives.


    namespace Zikula\Common\EventManager;
    
    use Zikula\Common\EventManager\EventManager as EventManager;
    use Zikula\Common\EventManager\Event as Event;




File Names and Location
-----------------------


Classes and interfaces should be named and located according to their name.  The `\` or `_` translate to directory paths.


    Foo_Bar => Foo/Bar.php
    Goo\Bar\Map\Link => Goo/Bar/Map/Link.php




Method Signatures
-----------------


Method signatures should follow the following guidelines.


  - Use type hinting where possible.


        public function registerFoo(Foo $foo, array $collection)
        {
        }


  - Optional arguments should be grouped on the right side for better readability.


    Example offending code:


        function foo($optional = null, $required)
        {
        }


    Recommended code:


        function foo($required, $optional = null)
        {
        } 




Class and interface Conventions
-------------------------------


  - One class or interface per file.
  - The entire class declaration together with `extends` or `implements` declarations should all be on the same line.
  - All properties and methods must explicitly declare public, protected or private.
  - Declare constants first.
  - Declare static variables after constants.
  - Declare properties before methods (public, protected then private).
  - The constructor (if there is one) should be the first method.
  - Declare protected methods after public methods.
  - Declare private methods after protected methods.
  - All properties and methods require a docblock.




Spacing and parenthesis
-----------------------


A single space should follow PHP statements followed by parenthesis and no padding on the inside of the parenthesis. There should be single spaces between operators.


    $foo = 1 + 2;


    if ($foo == 1) {
        // code
    }


    foreach ($beans as $key => $value) {
        // code
    }




Single/Double Quotes
--------------------


Please note there is no performance gain from using single quotes over double quotes.


Reasons for double quotes are to evaluate variables or properties, or to avoid ugly escaping of single quotes:


    $message = 'John wants you to call him today";
    $message = "Today's news is good for a change";


When concatenating strings, use double quotes where possible.  Here are some examples of this.


    $fullName = "$firstName $lastName";
    $include = "$this->basePath/$filename.php";


    // In this example, single quotes to avoid evaluating 
    // $firstName as a variable.
    $errorMsg = '$firstName should not contain numbers';


    // {} required for method calls
    $include = "{$this->getPath()}/$filename.php";


    // {} required because of underscore
    $path = "$fullPath/class_{$name}.php";


    // Concatenation using periods because PHP does not
    // evaluate constants inside quotation.  Using single
    // quotes as there is nothing to evaluate.
    $filePath = __DIR__ . '/myfile.php';


    // As above with double quotes because there are variables 
    // to evaluate.
    $filePath = __DIR__ . "/data_dir/$filename.php";




Control Structures
------------------


Braces are required around all control structures without exception.


Classes, interfaces, abstracts, functions and methods should start the brace on a new line and all the remaining constructs should have a space followed by the opening brace.


    class Foo
    {
        public function test()
        {
            foreach ($array as $key => value) {
                // do something
            }


            if ($condition) {
                // do something
            } else if ($condition) {
                // something else
            } else {
                // more
            }


            switch ($variable) {
                case 1:
                    // code
                    break;
                case 2:
                    // code
                    break;
                default:
                    // code
                    break;
            }
        }
    }


Typed constants
---------------


Types constants should be in lower case:


    true, false, null, array, int, float, string


When typecast, there should be no space between the typecast and the variable being typecast.


    $value = (int)$value;




Operators
---------
Boolean operators should be in lower case, `true`, and `false`.


Logical operators, do not use the words `and` or `or`.  Instead use `&&` and `||` and `xor`.




Negative conditional statements
-------------------------------
If using 'not' logic, the explanation mark should immediately precede the condition.


    if (!$foo) {
        // code
    }


    if (!($a == $b)) {
        // code
    }
  
    return !$this->flag; // invert a value




Ternary Expressions
-------------------


Shortcut conditional assignment should have a parenthesis around the condition.


    $flag = ($condition) ? true : false;
    


Method Naming Conventions
-------------------------


Class methods should have standards naming that is linguistically meaningful and consistent.


    getFoo()  - getter for foo.
    getFoos() - get all foo collection.
    setFoo()  - setter for foo.
    setFoos() - set foo collection.
    hasFoo()  - has a Foo (in the collection).
    isBar()  - is a Bar?
    isEmpty() - Is whatever empty.
    clearFoo() - Flush/clear.
    flushFoo() - Flush/clear.
    registerFoo() - Set specific key in collection.
    unregisterFoo() - Unset specific key in collection.
    addFoo() - Add to a stack.
    countFoo() - How many in collection.
    
    
Docblocks
---------


All PHP files should have a documentation block with the standard header [ref].


All classes must have a class level docblock.


    /**
     * ServiceManager class.
     */
    class Zikula\ServiceManager implements \ArrayAccess
    {
    }


All properties must have a docblock which includes the @var annotation.


    /**
     * Argument storage.
     *
     * @var array
     */
    private $arguments = array();




All functions (except lambda functions) and class methods must have a docblock that includes the @params (where appropriate) and @return in all cases.


    /**
     * Single line summary here.
     *
     * Extra details can go here in a paragraph or paragraphs as
     * necessary.
     *
     * @param string  $id     Id.
     * @param Foo\Bar $bar    Bar instance
     * @param boolean $shared Shared type.
     *
     * @throws InvalidArgumentException If ID is invalid.
     *
     * @return Foo\Bar Returns Bar instance
     */




Author Annotations
------------------


@author annotations are not permitted. There are specific reason for this which is worth mentioning for the record.  The nature of open source means that contributors will come and go.  As such @author tags can create a false sense of ownership over portions of the code-base.  @author annotations can prevent others from contributing to certain files because they may feel it's "someone domain".


Next comes the "when should I add my own @author My Name?" - When should you be entitled to add your name?  If you merely touch the file, or if you fix a typo, or a bug - how extensive do the changes have to be?  It starts getting rather complicated. 


Open source is about contribution, not about name recognition, so for these reasons, the @author annotations are forbidden.




API Annotations
---------------


@api - This annotation is used in function and method docblocks to declare it stable, public facing and intended for use by developers.  


The reason for this annotation is that there is no way to know definitively from the visibility declarations the intention of an API or whether the API is considered stable because even if a method is declared public, it may be intended to be internal to the framework.  


The @api annotation removes any ambiguity by expressly declaring what is meant to be public and stable so developers can rely on the interface.  Conversely, this also implies that everything without this annotation should be considered internal or unstable.  


This annotation must be used frugally and with careful consideration.
