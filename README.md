# JavaScript_Sierpinski_Triangle

# HTML Previews

## No Game Loop + Normal "In Set" Render
* https://htmlpreview.github.io/?https://github.com/JDoucette/JavaScript_Sierpinski_Triangle/blob/master/sierpinski_triangle_v1_no_gameloop.html

## Game Loop + Normal "In Set" Render
* https://htmlpreview.github.io/?https://github.com/JDoucette/JavaScript_Sierpinski_Triangle/blob/master/sierpinski_triangle_v2_game_loop.html

## Game Loop + Density Population
* https://htmlpreview.github.io/?https://github.com/JDoucette/JavaScript_Sierpinski_Triangle/blob/master/sierpinski_triangle_v3_population.html

# TODO

## From Michael Pohoreski:

Since the anonymous lambda function works you might be able to remove it entirely and just directly call main_function()
https://github.com/JDoucette/JavaScript_Sierpinski_Triangle/blob/master/sierpinski_triangle_v2.html#L93
//	(function () {
				main_function();
//	})();


Now that I'm awake another solution is:

1. Remove the canvas tag from body and manually dynamically insert it in main_function().

                // Dynamically insert canvas into body
                hCanvas        = document.createElement( 'canvas' ); // document.getElementById("MyCanvas");
                hCanvas.width  = 1536;
                hCanvas.height = 1536;
                document.body.appendChild( hCanvas );

Unfortunately the anonymous lambda creates a problem for us:  We are trying to access.document body before the body has finished loading.  We can solve this by placing a guard in main so that this doesn't execute in the remote case.

                // Unify local and remote (HTMLPreview)
                if( !document.body || hCanvas )
                    return;

2. We also need to fix onload so that it runs in the local case only and is ignored in the remote case.

    <body onload="if( typeof window['main'] === 'function' ) main()">
	
	
## Perhaps for other JavaScript effects, and not this one:

Scale canvas up as nearest neighbour for low resolution, full screen effects:

https://stackoverflow.com/questions/7615009/disable-interpolation-when-scaling-a-canvas

