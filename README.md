# tympanustextinput
http://tympanus.net/Development/TextInputEffects/index.html
<br>
Taken from http://tympanus.net/Development/TextInputEffects/index.html Set 1 and Set 2. All files included here for easy integration into your own HTML code. None of this work is my own, just putting this here as an easy way to use for rapid prototyping of delightful experiences. 
<br>
<br>
Instructions:<br>
1) Download zip or clone into desktop from command line using <br>
```
$ git clone https://github.com/shuyag/tympanustextinput.git
```
<br>
2) Rename entire folder "inputfields"
<br>
3) Paste the following into your header: 
```
    <link rel="stylesheet" type="text/css" href="inputfields/css/normalize.css" />
    <link rel="stylesheet" type="text/css" href="inputfields/fonts/font-awesome-4.2.0/css/font-awesome.min.css" />
    <link rel="stylesheet" type="text/css" href="inputfields/css/demo.css" />
    <link rel="stylesheet" type="text/css" href="inputfields/css/set2.css" />

	<script type="text/javascript">
	var _gaq = _gaq || [];
	_gaq.push(['_setAccount', 'UA-7243260-2']);
	_gaq.push(['_trackPageview']);
	(function() {
	var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
	ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
	var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
	})();
	</script>
```
Note: if you are using a text input field set from Set 2, change line 13 from 
```
<link rel="stylesheet" type="text/css" href="inputfields/css/set1.css" />
```
to
```
<link rel="stylesheet" type="text/css" href="inputfields/css/set2.css" />
```

4) Paste the following into your footer: 

```
    <script src="js/classie.js"></script>
		<script>
			(function() {
				// trim polyfill : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Trim
				if (!String.prototype.trim) {
					(function() {
						// Make sure we trim BOM and NBSP
						var rtrim = /^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g;
						String.prototype.trim = function() {
							return this.replace(rtrim, '');
						};
					})();
				}

			[].slice.call( document.querySelectorAll( 'input.input__field' ) ).forEach( function( inputEl ) {
					// in case the input is already filled..
					if( inputEl.value.trim() !== '' ) {
						classie.add( inputEl.parentNode, 'input--filled' );
					}

					// events:
					inputEl.addEventListener( 'focus', onInputFocus );
					inputEl.addEventListener( 'blur', onInputBlur );
				} );

				function onInputFocus( ev ) {
					classie.add( ev.target.parentNode, 'input--filled' );
				}

				function onInputBlur( ev ) {
					if( ev.target.value.trim() === '' ) {
						classie.remove( ev.target.parentNode, 'input--filled' );
					}
				}
			})();
		</script>

```

5) Paste any section into your HTML where you want the input field to show up. Delete the line containing the name to get just the fields. 
Ex: 
```

<section class="content bgcolor-1">
				<!--Delete this line below to get just input fields.-->
				<h2 class="nomargin-bottom">Haruki</h2> 
				<span class="input input--haruki">
					<input class="input__field input__field--haruki" type="text" id="input-1" />
					<label class="input__label input__label--haruki" for="input-1">
					<span class="input__label-content input__label-content--haruki">First Name</span>
					</label>
				</span>
				<span class="input input--haruki">
					<input class="input__field input__field--haruki" type="text" id="input-2" />
					<label class="input__label input__label--haruki" for="input-2">
					<span class="input__label-content input__label-content--haruki">Last Name</span>
					</label>
				</span>
				<span class="input input--haruki">
					<input class="input__field input__field--haruki" type="text" id="input-3" />
					<label class="input__label input__label--haruki" for="input-3">
						<span class="input__label-content input__label-content--haruki">Email</span>
					</label>
				</span>
			</section>
```			
<br>


6) Customise any classes to fit in with the rest of your page.
