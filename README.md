# jQuery Mentionable
**Enable the user to mention other people by typing @**

jQuey Mentionable is the plugin that enables the user to mention other poeple in text area.

## Usage
First, include jquery and jquery.mentionable to your HTML.
```html
<script src='jquery.js'></script>
<script src='jquery.mentionable.js'></script>
```
To make a textarea mentionable, call mentionable method with a url string as its parameter.
```javascript
$("#textarea").mentionable("user_list_url");
```