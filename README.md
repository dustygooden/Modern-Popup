# Modern Popup: Beautiful popups for HTML5

* Adds customizable HTML5 popups with ease.
* All in a single JavaScript file.
* No additional CSS files or additions to your CSS necessary.
* Requires jQuery.

## Usage

Load it after jQuery

```html
<script src="http://code.jquery.com/jquery-x.x.x.min.js"></script>
<script src="popuphandler.js"></script>
```

Setup your HTML:

```html
<section>
	<div class="popup">
		<div>
			<h1>Title</h1>
			<p></p>
		</div>
	</div>
</section>
```

The popup must have at least one parent, although the `<body>` can technically be the parent. In this example I used a `<section>` tag, but the script can run on virtually any HTML5 tag.

The `<div>` with `class="popup"` is where the overlay will be styled. Since Modern Popup only uses JavaScript to create the styles, no CSS is necessary. (If you would like to style the overlay view the Config section below).

The child of the `class="popup`" is where the actual popup box will be styled. There is no identifier needed to create this, however, this child cannot have a sibling. (Again, if you would like to style this please view the Config section below).

The `<h1>` and `<p>` tags are not required, you may use any applicable HTML5 tag you wish (These may be styled with CSS). If for any reason you do not wish to have text, you can leave these out, it will not affect the rest of the popup.

Optionally you can use an `<img>` tag if you would like to display an image within the popup.

## Calling the Popup:

```html
<section>
	<div class="popup">
		<div>
			<h1>Title</h1>
			<p></p>
		</div>
	</div>
	<a href="javascript:void(0)" onclick="popupHandler(this)" data-location="sibling">Show Popup</a>
</section>
```

The only required action is to call the function `popupHandler()` with an identifying parameter and a `data-location` attribute. You can achieve this easily with `onclick="popupHandler(this)"`.
The function must be called with a parameter that identifies the calling object. In this case, clicking the `<a>` tag calls the function. Making the `<a>` tag the calling object.

If you were to call this from within a JavaScript file, you could add an `id="#"` attribute to any parent of the `class="popup"`. Then using the `id="#"` as the parameter sent to the method.

If the popup is a sibling of the calling object, then use `data-location="sibling"`. If the popup is a child of the calling object, then use `data-location="child"`. These are the only two accepted `data-location` attributes at this time . It is not required that the popup be a direct child of the calling object.


Below is an example of using a parent to call the popup:

```html
<section onclick="popupHandler(this)" data-location="child">
	<div class="popup">
		<div>
			<h1>Title</h1>
			<p></p>
		</div>
	</div>
</section>
```

## Closing the Popups

There are three possible ways of closing the popups: 
* By clicking the popup or overlay. 
* By waiting the specified timeout period (default is 15 seconds). 
* By calling the `popupClose()` function.

The latter is not quite as self explanatory. If you wish to use the `popupClose()` function you have to include a parameter that identifies the specific element with the `class="popup"` you wish to close. It was created this way to avoid issues with having multiple popups on a single page.
This can be called by either a JavaScript function or with either the HTML `onclick` or Form `action` attributes.


Below is an example of using the `popupClose()` method:

```html
<section>
	<div class="popup" id="popupOne">
		<div>
			<h1>Title</h1>
			<p></p>
		</div>
	</div>
</section>
<div onclick="popupClose('#popupOne')">Close Popup</div>
```

Again, you could use JavaScript by itself to close the popup, but for simplicity's sake I did it with HTML `onclick`.

## Data Attributes

You can apply the `data-null` attribute to the object that calls the `popupHandler()` method.

You may use the following attributes to change how the popup is closed:

* `data-null="click"` Will not allow clicking the popup to close the popup. However, the function and timer will still work.
* `data-null="timer"` Will not allow the popup timer to close the popup. However, the function and clicking will still work.
* `data-null="both"` Will not allow clicking the popup or the timer to close the popup. However, the function will still work.

If you do not want the popup to close, simply set `data-null="both"` and do not call `popupClose()`.

If you do not specify a `data-null` attribute it will default to allowing the use of any of the three available methods.


An example of using the `data-null` attribute is shown below:
```html
<section>
	<div class="popup">
		<div>
			<h1>Title</h1>
			<p></p>
		</div>
	</div>
	<a href="javascript:void(0)" onclick="popupHandler(this)" data-location="sibling" data-null="both">Show Popup</a>
</section>
```

This will not allow the timer or clicking the popup to close it.

## Config:

```js
//User-Defined Settings

var config = {
    'Overlay Background-Color' : 'rgba(0, 0, 0, .65)',
    'Overlay Z-Index' : '99',
    'Content Color' : '#777',
    'Content Width' : '300', //In Pixels Only.
	'Content Height' : '200', //In Pixels Only.
	'Content Padding' : '1em',
	'Content Background-Color' : 'rgba(255, 255, 255, 0.85)',
	'Content Z-Index' : '100',
	'Popup Timeout' : '15000' //In Milliseconds
};
```

The names of the configuration are fairly self explanatory. You may change these as you see fit.

The `'Content Width'` and `'Content Height'` configurations will only work as pixel values, because of math related problems that would occur when centring the popup. 

## Further Information

If you would like to see the Modern Popup in action, please view the working example included in the repository.

Feel free to contact me with any questions you may have.

## License

Modern Popup is released under the MIT license.

Copyright © 2014 Dusty Gooden

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.