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


##RESTful APIs

###With PHP
Always use json_encode() when returning json data, even when it is a simple string value. Otherwise jQuery ajax calls activate the error callback on success. 
