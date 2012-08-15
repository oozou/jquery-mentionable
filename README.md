# jQuery Mentionable
**Enable the user to mention other people by typing @**

jQuey Mentionable is the plugin that enables the user to mention other poeple after
typing '@' in the textarea. The example of jquery-mentionable can be found
[here](http://jquery-mentionable.ap01.aws.af.cm)

## Requirements
You need to have a url that, when it is called, returns a list of user in json format.
When the user types a name after @, jquery.mentionable will make an ajax call to that
url, and parse a typed name as a query param 'mentioning'. For instance, if the url
is http://localhost/users.json, when the user types '@tai', jquery.mentionable will fire
a request to *http://localhost/users.json?mentioning=tai*. The expected json should look
like this.
```json
[{"created_at":"2012-08-15T16:07:30Z","id":1,"image_url":"/assets/u1.png","name":"taiko","updated_at":"2012-08-15T16:26:35Z"},{"created_at":"2012-08-15T16:15:59Z","id":2,"image_url":"/assets/u2.png","name":"Kiera Harber","updated_at":"2012-08-15T16:15:59Z"}]
```

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
<link href='jquery.mentionable.css' media="all" rel="stylesheet" type="text/css">
```
Next, wrap a textarea with a div with relative positioning. If you did not wrap it
this way, the position of user list will be out of control.
```html
<div style="position:relative;">
  <textarea id="textarea"></textarea>
</div>
```
To make a textarea mentionable, in javascript, call mentionable method with a url string as its parameter.
```javascript
$("#textarea").mentionable("user_list_url");
```
The above code will use a default callback handle to populate the user list.

## Configuring
jquery.mentionable accepts three parameters which are usersURL, opts and onCompleteFunction respectively.
*usersURL* is, as stated above, a url for a user json collection. opts is an option object
and onCompleteFunction is a function that will be triggered when the ajax called is completed.

As stated above, you can also add your own handler function.
For instance, the following code will pop an alert box when the user list is loaded.
```javascript
$("#textarea").mentionable("user_list_url", null, function(){
  alert("hello world"); // do what you want here
});
```
There are also some options that you can parsed along
* *id* : an id of the user list container .
* *minimumChar* : a minimum number of characters required to trigger user fetching.
* *parameterName* : a name of parameter to be parsed to the user list url
* *position* : a position of user list: left, bottom, and right.

The following example creates a mentionable text area which will parse a string via 'filter' query parameter when 3 or more characters are typed.
```javascript
$("#textarea").mentionable(
  "http://your/user/list/url",
  {minimumChar: 3, parameterName: "filter"}
);
```
## Styling
If you decided to customize the user list id, the base style of jquery-mentionable will not be applied. Please take a look at jquery-mentionable.css to explore the base style.

## Known Issue
Sadly, jquery-mentionable is now not working on Firefox.

## Todo
* Make it works with Firefox.
* Rework on a base style, especially the hover and selection.
* Enable the user to use other property name other than 'name' and 'image_url'.

