# Useful Notes
A list of tips and notes to keep you better prepared against the dangers of the wild.

##Regex

### Email validation
A fairly decent regex for email-validation can be found [HERE](http://www.regular-expressions.info/email.html). The sample code is: 
```
[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?
```


##CSS

###Failed clicks
When an element has :active styling that changes its position, if the user targets with a click a zone, that is empty in :active state, the click is not fired as javascript event. To fix that, use a modified version of the following code:
```
element-selector:active:before {
  content: '';
  position: absolute;
  top: -Xpx; /* border plus shift amount */
  right: 0;
  bottom: 0;
  left: -Xpx; /* border plus shift amount */
}
```

###Center block/inline-block element
To position such element, give it's parent postion: relative; Then make sure the element has position: absolute; margin: auto; top/right/bottom/left: 0; and defined width and height. It is expremely good browser support that compensate for the need to define height.

###Horizontaly align elements with 50% width
When you give two divs width: 50%, they will most probably end on different lines. The cause for this is a blank space character that is generated between them. To counter it, either go to your source code and make sure the ending tag of the first div and the opening tag of the second are at the same line without any sapce between them, or set their parent's font-size: 0. Take in mind that font-size is inherited, so you need to specifically assign font-size value to the children elements, if you want to have some text inside them.

###Change dynamically the content value of a pseudo element
A pseudo element is unable to be selected with javascript thus it makes the dynamic change of its content attribute a hard task. This, however is easily solved if you use attr() as value for the content of that element. attr() takes one argument - a name of an attribute of the main element. Let's say we have a div and a :before pseudo element. In the stylesheet, we can set:
```
div::before {
  content = attr('data-text');
}
```
and in our html, we can set:
```
<div data-text="Text"></div>
```
This will make the initial value of our :before to equal 'Text'. And we can easily select the div and change the data-text attribute with javascript.


##RESTful APIs

###With PHP
Always use json_encode() when returning json data, even when it is a simple string value. Otherwise jQuery ajax calls activate the error callback on success. 
