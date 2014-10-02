Best Practices
==============
##1. Never Use Short Tags
Why would you use short tags instead of writing the full and official **“<?php”** tag?    
Using **“<?”** or **“<%”** is never a good practice and it doesn’t make your code look more professional than others.    
This simple malpractice can cause conflicts with XML parsers and can also make your code incompatible with future versions of PHP.

##2. Format your code
**Don't**
```php
    public function myFunction() {
  //Some statements
        //Some more statements
}
```
**Do**
```php
public function myFunction() {
    //Some statements
    //Some more statements
}
```

##3. Use meaningful variable and function names in your code
It can surely become a painful experience for other programmers to understand your code if you **don’t stick with a proper naming standard and use generic and un-meaningful names everywhere**. It’s not a good practice at all, and you must not follow it in any way.    

Always try to use meaningful and grammatically sensible names for your variables and functions and try to make the good habit of separating every word with underscores. **And also try to be consistent with the standard you are following** so that other people can get to understand your convention quickly and easily.

**Don't**
```php
protected $_var_a = 'Mr PHP';
protected $varB = '25';

public function c() {
    return 'Name: ' . $this->_var_a . '. Age: ' . $this->varB;
}
```

**Do**
```php
protected $_name = 'Mr PHP';
protected $_age  = '25';

public function getInfo() {
    return 'Name: ' . $this->_name . '. Age: ' . $this->_age;
}
```
