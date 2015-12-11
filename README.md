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

##RESTful APIs

###With PHP
Always use json_encode() when returning json data, even when it is a simple string value. Otherwise jQuery ajax calls activate the error callback on success. 
