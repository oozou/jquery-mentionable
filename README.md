# jQuery Mentionable
**Enable the user to mention other people by typing @**

jQuey Mentionable is the plugin that enables the user to mention other poeple while
typing in text area.

## Requirements
You need to have a url that, when it is called, returns a list of user in json format.
When the user types a name after @, jquery.mentionable will make an ajax call to that
url, and parse a typed name as a query param 'mentioning'. For instance, if the url
is http://localhost/users.json, when the user types '@tai', jquery.mentionable will fire
a request to *http://localhost/users.json?mentioning=tai*.

jquery.mentionable has a built-in callback that will populate the
user list for you after ajax call is success. The only thing you
need to do is to ensure that the returned json is an array of user object
where each object has *name* and *image_url* fields. You can also
supply the callback function by yourself if there is more logic
you want to do.


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
The above code will use a default callback handle to populate the user list.

### Configuring
As stated above, you can also add your own handler function.
For instance, the following code will pop an alert box when the user list is loaded.
```javascript
$("#textarea").mentionable("user_list_url", function(){
  alert("hello world"); // do what you want here
});
```
There are also some options that you can parsed along which are
* id : an id of the user list container .
* minimumChar : a minimum number of characters required to trigger user fetching.
*parameterName : a name of parameter to be parsed to the user list url
* position : a position of user list: left, bottom, and right.

The following example creates a mentionable text area which will parse the name to 'user' parameter when 3 or more characters are typed.
```javascript
$("#textarea").mentionable(
  "http://your/user/list/url",
  {minimumChar: 3, parameterName: "user"}
);
```
