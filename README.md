jQuery Language detection plugin
================================

jQuery plugin for browser language detection with automatic redirection.

## Installation

Include the production file after jquery.

```html
<script src="path/jquery-latest-version.js"></script>
<script src="path/jquery.language.detection.min.js"></script>
```

## Usage

### HTML

Set the `lang` attribute for your `html` elements in the whole website.

```html
<html lang="en">
```

Assign to each `a` element in your language menu the `.language` class and the `data-language` attribute set to the right ISO Language Code. 

```html
<a class="language" href="path/to/english-version" data-language="en">English</a>
<a class="language" href="path/to/italian-version" data-language="it">Italian</a>
<a class="language" href="path/to/french-version" data-language="fr">French</a>
<a class="language" href="path/to/spanish-version" data-language="es">Spanish</a>
```

### jQuery

Initialize the plugin in your main scripts file (the one included in all of your pages).

```javascript
$(document).ready(function() {
	$(document).languageDetection({
		languages   :   [
			{
				code : 'en',
				path : '',
				defaultLanguage : true
			},
			{
				code : 'it',
				path : 'it'
			},
			{
				code : 'fr',
				path : 'fr'
			},
			{
				code : 'es',
				path : 'es'
			}
		]	
	});
});
```

## Options

### domain

The root of your website (use this option if it is inside a subfolder). If not set explicitly, this will be set to the protocol and hostname of the URL within the browser URL bar.

### useFullPaths

Set this option to `true` if you want to use absolute paths for languages folders (you have to use it if each language is in a different subdomain).
Default:false

### languages

An array of objects, one for each language.
Each object has 3 properties:

#### code

The ISO Language Code.

#### path

The relative path to the folder which contains the files for the language.
You have to specify the absolute path if you set the `useFullPaths` option to `true`.

#### defaultLanguage

This must be `true` for the default language of the website.
Users will be redirected to this language if their browser language is not in the `languages` array.

Default:
```javascript
[
	{
		code   :   'en',
		path   :   '',
		defaultLanguage   :   true
	}
]
```

### expires

The expiration date of the cookie used to store the user's language preference.
It is expressed in days.
Default: null

### Example with custom options

```javascript
$(document).ready(function() {
	$(document).languageDetection({
		domain        :  'http://www.mydomain.xx/subfolder/',
		languages     :  [
			{
				code : 'it',
				path : ''
			},
			{
				code : 'en',
				path : 'en',
				defaultLanguage : true
			},
			{
				code : 'fr',
				path : 'fr'
			},
			{
				code : 'es',
				path : 'es'
			}
		],
		expires       :  10	
	});
});
```
