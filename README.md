# jQuery Mentionable
**Enable the user to mention other people by typing @**

jQuey Mentionable is the plugin that enables the user to mention other poeple in text area.

## Requirements
You need to have a url that, when it is called, returns a list of user in json format.
When the user types a name after @, jquery.mentionable will make an ajax call to that
url, and parse a typed name as a query param 'mentioning'. For instance, if the url
is http://localhost/users.json, when the user types '@tai', jquery.mentionable will fire
a request to http://localhost/users.json?mentioning=tai.

Two fields are expected in returned json: name and image_url. If these fields
are found, jquery.mentionable can handle data population for you. However,
you can also parse your own handling function if you wanted to handle
the data yourself.

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

