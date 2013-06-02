jquery-collagePlus
==================

Create an image gallery like Google+ Albums


Example
-------
[![solarized dualmode](https://github.com/ed-lea/jquery-collagePlus/blob/master/support/images/0.2.0-preview.png)]


JSFiddle Example
----------------
http://jsfiddle.net/edlea/uZv3n/



Basic Usage
-----------


    $('.Collage').collagePlus();
    
    
    
Getting Started
---------------


    /* In your CSS */
    .Collage img{
    
        /* ensures padding at the bottom of the image is correct */
        vertical-align:bottom;
        
        /* hide the images until the plugin has run. the plugin will reveal the images*/
        opactiy:0;
        
        }
        

Ensure you have no whitespace between your image tags for a clean grid.

        
    <!-- In your HTML -->
    <div class="Collage">
    <img src="http://placehold.it/350x150"><img src="http://placehold.it/400x300"><img src="http://placehold.it/290x800">
    </div>
    
Alternatively, use the jquery.removeWhitespace.js plugin in the extras directory to do this for you e.g.

    $('.Collage').removeWhitespace().collagePlus();
    

You may want to run the plugin with an image loader like https://github.com/desandro/imagesloaded, alternatively you can try it with


    $(window).load(function () {
        $('.Collage').collagePlus();
    });


Browser Resize
--------------

By default this behaviour not included in the plugin but you can use a few lines of js to reload the images if the user resizes the browser window


    function collage() {
        $('.Collage').collagePlus(
            {
                'fadeSpeed' : 2000
            }
        );
    };
     
    var resizeTimer = null;
    $(window).bind('resize', function() {
        // hide all the images until we resize them
        // set the element you are scaling i.e. the first child nodes of ```.Collage``` to opacity 0
        $('.Collage .Image_Wrapper').css("opacity", 0);
        // set a timer to re-apply the plugin
        if (resizeTimer) clearTimeout(resizeTimer);
        resizeTimer = setTimeout(collage, 200);
    });

