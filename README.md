( This is a file in Markdown format: https://www.markdownguide.org/basic-syntax/ .
VSCode can display this as intended via "preview": https://code.visualstudio.com/docs/languages/markdown .)

## SVG by hand

The point of this exercise is to be exposed (once) to what is actually inside the textual representation of an SVG object, so that we can better appreciate being able to create and manipulate them with d3. GLK recommends that you skim the first few sections of [MDN's SVG Tutorial](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial) (up through "Paths") to get a sense of what an SVG is, these were also discussed [in class on April 5](http://people.cs.uchicago.edu/~glk/class/datavis/slides/04-05-WebTufte.pdf).

Your goal is to modify the given hw2.svg so that it looks like the given hw2.png image (which is different for everyone in the class). You finish this part of hw2 by svn commit'ing your hw2.svg. You will add **five** SVG elements after the line that says

    <!-- v.v.v.v.v.v.v.v.v.v.v.v.v.v.v  begin student code -->

and before the line that says

    <!-- ^'^'^'^'^'^'^'^'^'^'^'^'^'^'^  end student code -->

You create this SVG "by hand" (i.e., with an editor like VSCode which which you edit the textual contents of the file), rather than with a GUI-based program like Inkscape or Illustrator. In class we noted [a VSCode extension that supports SVG previewing](https://marketplace.visualstudio.com/items?itemName=jock.svg). The elements you will add are:

- Two line segments [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/line](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/line)
- One rectangle [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/rect](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/rect)
- One ellipse [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/ellipse](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/ellipse)
- One triangle, formed with a path [https://developer.mozilla.org/en-US/docs/Web/SVG/Element/path](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/path), with [path data](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d) of the form "M x y L x y L x y Z" (note that M, L, and Z are [path commands](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d#path_commands))

The order you write the elements in determines which elements appear on top of others. Every element uses the [stroke](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke) attribute (to set the color of the line segments or the color of outline of the other shapes) and the [stroke-width](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke-width) attribute to set the width of the lines and outlines. There are no [transform](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/transform) attributes in any element.

To learn what is where in your hw2.png, you can use a site like [https://www.ginifab.com/feeds/pms/color_picker_from_image.php](https://www.ginifab.com/feeds/pms/color_picker_from_image.php) that allows you to upload an image, and use the cursor to find the pixel coordinate locations for different things in the image, and color at that location.

To help compare hw2.svg and hw2.png, your index.html has been set up so that you can toggle between them, which is sort of like a [blink comparator that astronomers have used to discover faint objects moving in the night sky](https://en.wikipedia.org/wiki/Blink_comparator).

However, so that this is not a completely tedious exercise in fiddling coordinates and parameters in order to make the SVG match the PNG, there are strong constraints on the geometry and colors of things, so that you have a manageable set of discrete choices:

- all RGB colors are of the form "#HHH" where "H" is a hex character, but limited to the set: 1, 5, 9, D (for reference search [here](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) for "three-digit notation").
- all stroke widths are either 5, 10, or 20 (never 0)
- all X and Y spatial coordinates and all dimensions (widths, heights, radii) are some non-zero multiple of 50.

If the strokes were much thinner, you might more clearly see that the vertices for the rectangles and lines, and the boxes bounding the ellipses, are exactly aligned with coordinates for which X and Y are multiples of 50. Because the stroke is thick, the interior of the object may seem smaller. The stroke extends across the center of the path of the outline of the object, so for the rectangle and ellipse it eats away at the apparent size of the interior, and makes the total size a little larger. The stroke may also extend well past the actual location of triangle corners (with the default [line-join](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke-linejoin)).

If part of a shape (such as a line or rectangle) is hidden, there may be multiple SVGs that have the same appearance, and that's ok. Grading will rasterize your svg and compare it to the given PNG image. Note that even when you've find a correct hw2.svg, it will not look exactly like the pre-rasterized hw2.png. The specific tool used for doing that rasterizing, and the way that it [anti-aliases](https://en.wikipedia.org/wiki/Spatial_anti-aliasing) the geometry, will be different than what your browser does on your screen. The constraints on the SVG parameters in hw2.svg, however, allow you to not worry about these small differences.
