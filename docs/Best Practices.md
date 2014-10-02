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

##4. Pay notice when using functions inside loops
**Don't**
```php
for ($i  = 0, $i <= count($array);  $i++) {
//statements
}
```

**Do**
```php
$count = count($array);
for ($i = 0; $i < $count;  $i++) {
//statements
}
```
If you store the value returned by the function in a separate variable before the loop, then you would be **saving enough execution time** as in the first case the function will be called and executed every time the loop runs which can increase the time complexity of the program for large loops.

##5. Avoid *"hard code"*
**Don't**
```php
class Person
{
    protected $_type;
     
    public function __construct($type)
    {
        $this->_type = $type;
    }
}
...
$person = new Person(1);
```

**Do**
```php
class Person
{
    const GOOD_TYPE = 1;
    const BAD_TYPE  = 2;
    
    protected $_type;
    
    public function __construct($type)
    {
        $this->_type = $type;
    }
}
...
$person = new Person(Person::GOOD_TYPE);
```

##6. Consider alternative syntax for control structures
When using PHP control structures *(if, while, for, foreach, switch)* inside your HTML template, those curlly brackets can really be hard to follow. Take a look at this HTML template extract:
```php
<div id="fooes">
<?php if ($haveFoo) { ?>
	<h2>Here are my fooes</h2>
	<?php foreach ( $fooes as $myfoo ) { ?>
		<h3><?php echo $myfoo->title; ?></h3>
		<p class="foo-date">This foo was posted on <?php echo $myfoo->date; ?> by <?php echo $myfoo->author; ?></p>
		<?php if ( $myfoo->is_special ) { ?>
			<div class="special">
				<?php echo $myfoo->content; ?>
			</div>
		<?php } else { ?>
			<div class="not-so-special">
				<?php echo $myfoo->content; ?>
			</div>
		<?php } ?>
	<?php } ?>
<?php } else { ?>
	<h2>Sorry, no fooes available!</h2>
<?php } ?>
</div>
```

Even in a simple template, like our example here, it’s easy to get confused with those closing brackets. So let’s try to rewrite this using alternative syntax for control structures:
```php
<div id="fooes">
<?php if ($haveFoo) : ?>
	<h2>Here are my fooes</h2>
	<?php foreach ( $fooes as $myfoo ) : ?>
		<h3><?php echo $myfoo->title; ?></h3>
		<p class="foo-date">This foo was posted on <?php echo $myfoo->date; ?> by <?php echo $myfoo->author; ?></p>
		<?php if ( $myfoo->is_special ) : ?>
			<div class="special">
				<?php echo $myfoo->content; ?>
			</div>
		<?php else : ?>
			<div class="not-so-special">
				<?php echo $myfoo->content; ?>
			</div>
		<?php endif; ?>
	<?php endforeach; ?>
<?php else : ?>
	<h2>Sorry, no fooes available!</h2>
<?php endif; ?>
</div>
```
And even better, try using some **template engines** such as [Smarty](http://www.smarty.net/), [Twig](http://twig.sensiolabs.org/), ...


***
####*References:*
1. https://www.corephp.com/blog/php-best-practices-that-you-must-follow/
2. http://www.kmoser.com/articles/Good_Programming_Practices.php
3. http://www.smarty.net/
4. http://twig.sensiolabs.org/
