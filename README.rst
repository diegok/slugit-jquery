===================================================
slugIt - just another jQuery slugs generator plugin
===================================================

I've created this one because I wanted a jQuery slug plugin capable of convert 
european utf8 chars plus some symbols and easily extensible for custom extra mappings.
None of the ones listed on http://plugins.jquery.com/plugin-tags/slug does what I needed.

I got the idea of this plugin after using the excelent perl module Text::Unidecode 
(http://search.cpan.org/dist/Text-Unidecode/) for this same task server side. 

I've taken some chars tables from Django admin urlify.js 
(http://code.djangoproject.com/browser/django/trunk/django/contrib/admin/media/js/urlify.js) 
as this one was the most similar aproach to what I was looking to implement over jQuery.

Requirements
============

Requires JQuery ( I've only tested with 1.4, but should work with previous versions)::

  <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4/jquery.min.js"></script>

Usage
=====

Load this plugin like any other::

  <script type="text/javascript" src="jquery.slugit.js"></script>

Then, you select the source field to be converted::

    <form>
        <input type="text" id="slugme"/>
        <input type="text" id="slug"/>
    </form>

    <script>
        $(document).ready(function(){
            $('#slugme').slugIt();
        });
    </script>

Or, you can add some extra mappings::

    <script>
        $(document).ready(function(){
            $('#slugme').slugIt({ map: { '☂': 'umbrella' } });
        });
    </script>

...So, "I ♥ my ☂'" will be converted to "i-love-my-umbrella"
    
Options
-------

While the slugIt() method has some defaults that make the previous example to work, you'll be probably
inerested in customize for your convenience. These are the available options and their defaults::

    {
        events: 'keypress keyup', // Any sensible jquery event (http://api.jquery.com/category/events/)
        output: '#slug',          // A selector to place the converted result
        map   : false,            // A hash with extra replacemets. 
                                  // You can overwrite default replacements just passing the
                                  // ones you like to replace.
        space : '-',              // Character that replaces spaces
        modify: false             // Callback that will be fired before processing slug
                                  // It's useful when you need to change the input in some way,
                                  // for example add some prefix or suffix
    }

Examples
--------
Examples can be found at http://github.com/diegok/slugit-jquery/tree/master/examples/

Licensing
---------
BSD License can be found at http://www.opensource.org/licenses/bsd-license.php

