Elucidate™
=========

A jQuery plugin to help you explain your HTML mockups. Facilitate design and front-end hand-offs to your development teams.


WHAT IS IT?
-----------

Elucidate™ is a jQuery plugin designed to help you document and explain your HTML mockups. The goal is to use simple and standard HTML markup while ensuring the documentation is *never* confused with the mockup itself. The purpose is to facilitate design and front-end hand-offs to your development teams. This is especially important when your design and development teams are remotely distributed. Ensure that you design interactions are clearly documented and understood.


BASIC USAGE
-----------

Add Elucidate™ to your site by including the following css and scripts to the head of your document.

    <link rel="stylesheet" href="elucidate/css/elucidate.css" type="text/css" media="screen, projection">
    <script type="text/javascript" charset="utf-8" src="js/jquery.js"></script>
    <script type="text/javascript" charset="utf-8" src="elucidate/js/cookie.jquery.js"></script>
    <script type="text/javascript" charset="utf-8" src="elucidate/js/elucidate.jquery.js"></script>

You invoke Elucidate™ by calling the function on whichever element you would like the controls added.

    <script type="text/javascript" charset="utf-8">
      $(document).ready(function() {
        $("body").elucidate();
      });
    </script>

This appends the annotation controls to the body element. If you pass in a collection, the controls will simply be added to the first item only.

To create the annotations, simply add a title attribute with the text you want to any HTML elements. For example:

    <p title="Neither is there anyone who loves grief itself since it is grief and thus wants to obtain it">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. </p>

This will add a callout on the paragraph which reveals the annotation on rollover.


ADVANCED USAGE
--------------

There are quite a few options you can pass in to Elucidate™ to customize its display. These are the options, along with the default values:

    metadata_ignore: ["viewport","keywords"]

This is an array of meta tags that are ignored when creating the page summary box. By default we're ignoring keywords and the viewport directive. Any others will be displayed.
  
    annotation_selector: "[title]"

This is a jQuery selector to target which items are used for the callouts. The default finds all items that have a title attribute. You could for example, restrict this to a particular class ".annotate[title]". I do recommend only calling it on a collection that has title tags though.

    label_instructions: "Show",
    label_annotations: "Notes",
    label_hotspots: "What's clickable?",
    label_notshown: "(Not shown in the current page state)",

These four options customize the user interface labels and have no effect on the functionality. 'label_notshown' only appears on the print version for items that happen to be hidden. This is especially useful if you are using the PolyPage plugin to hide elements and want to avoid "orphaned" annotations (more on PolyPage later).
    
    ignore_hotspots_selector: "#pp_options a"

If there are links that you don't want highlighted for the "What's Clickable?" feature, include a jQuery for what to *ignore*. The default value ignores links that PolyPage uses, but you can add to that set.
  
Here's an example of calling Elucidate™ with several custom options:  

    <script type="text/javascript" charset="utf-8">
      $(document).ready(function() {
        $("body").elucidate(
            {label_instructions: "Mockup Annotations", label_annotations: "Callouts", metadata_ignore: [ "viewport" ] }
          );
    	});
    </script>


TIPS & TRICKS
----------

* Few people seem to take advantage of it, but the meta tag can take any arbitrary key/value pairs. For example, you could use source control revision, last modified date, revision, a project status of some sort, etc. 

* Title attributes *seem* to allow arbitrary HTML. I wouldn't go crazy, but it seems that you can use bold, italic, br, etc., to style the annotation text.


KNOWN ISSUES
----------

* Given that we're inserting elements into your HTML it is extremely difficult to avoid CSS collision. All of Elucidate™ styles are namespaced so that it is unlikely to affect your mockup, however, the reverse is not necessarily true. While, I've attempted to reset styles on each Elucidate™ element, any global styles you write on html elements tables, divs, spans, links, lists, etc. might collide. The best way to avoid any issues is to namespace your css by using classes/ids, or simply edit elucidate css file to override.

* Adding annotations to images is not supported at the moment, the annotation will silently disappear.

* Adding an annotation to a link tag doesn't work exactly right because the callout/annotation picks up the link behaviour/styling, meaning it'll likely be underlined and if you click it and it'll go where the link goes.

ACKNOWLEDGEMENTS
------------

Elucidate originally started out as a simple fork of the now dormant [Annotatr](https://github.com/philoye/annotatr) plugin by Phil Oye. The goal was to update the styling and extend it for my own purposes. It has since morphed into a whole scale re-write with tons more functionality added. But, the original vision and code credit goes to Phil. Many Thanks. 


LICENSE
------------

This software is licensed under the MIT license.