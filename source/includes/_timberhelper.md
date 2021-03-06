
# Timber\Helper
As the name suggests these are helpers for Timber (and you!) when developing. You can find additional (mainly internally-focused helpers) in TimberURLHelper



Name | Type | Description
---- | ---- | -----------
[ob_function](#ob_function) | string | 
[start_timer](#start_timer) | \Timber\float | 
[transient](#transient) | mixed | 

## array_to_object
`array_to_object( mixed $array )`

**returns:** `\stdClass` 

Name | Type | Description
---- | ---- | -----------
$array | mixed | 



## array_truncate
`array_truncate( mixed $array, mixed $len )`

**returns:** `array` 

Name | Type | Description
---- | ---- | -----------
$array | mixed | 
$len | mixed | 



## <strike>close_tags</strike>
**DEPRECATED** since 1.2.0

`close_tags( mixed $html )`

**returns:** `string` 

Name | Type | Description
---- | ---- | -----------
$html | mixed | 



## error_log
`error_log( mixed $error )`

**returns:** `void` 

Name | Type | Description
---- | ---- | -----------
$error | mixed | 



## <strike>function_wrapper</strike>
**DEPRECATED** since 1.3.0

`function_wrapper( mixed $function_name, array $defaults=array(), bool $return_output_buffer=false )`

**returns:** `\Timber\FunctionWrapper/mixed` 

Name | Type | Description
---- | ---- | -----------
$function_name | mixed |        String or array( $class( string|object ), $function_name ).
$defaults | array |             Optional.
$return_output_buffer | bool | 



## <strike>get_comment_form</strike>
**DEPRECATED** 0.21.8 use `{{ function('comment_form') }}` instead

`get_comment_form( mixed $post_id=null, array $args=array() )`

**returns:** `string` 

Gets the comment form for use on a single article page

Name | Type | Description
---- | ---- | -----------
$post_id | mixed | 
$args | array | 



## get_current_url
`get_current_url( )`

**returns:** `string` 



## get_object_by_property
`get_object_by_property( mixed $array, mixed $key, mixed $value )`

**returns:** `array/null` 

Name | Type | Description
---- | ---- | -----------
$array | mixed | 
$key | mixed | 
$value | mixed | 



## get_object_index_by_property
`get_object_index_by_property( mixed $array, mixed $key, mixed $value )`

**returns:** `bool/int` 

Name | Type | Description
---- | ---- | -----------
$array | mixed | 
$key | mixed | 
$value | mixed | 



## get_wp_title
`get_wp_title( string $separator=" ", string $seplocation="left" )`

**returns:** `string` 

Name | Type | Description
---- | ---- | -----------
$separator | string | 
$seplocation | string | 



## is_array_assoc
`is_array_assoc( mixed $arr )`

**returns:** `bool` 

Name | Type | Description
---- | ---- | -----------
$arr | mixed | 



## is_true
`is_true( mixed $value )`

**returns:** `bool` 

Name | Type | Description
---- | ---- | -----------
$value | mixed | 



## iseven
`iseven( mixed $i )`

**returns:** `bool` 

Name | Type | Description
---- | ---- | -----------
$i | mixed | 



## isodd
`isodd( mixed $i )`

**returns:** `bool` 

Name | Type | Description
---- | ---- | -----------
$i | mixed | 



## ob_function
`ob_function( \Timber\callback $function, array $args=array() )`

**returns:** `string` 

Calls a function with an output buffer. This is useful if you have a function that outputs text that you want to capture and use within a twig template.

Name | Type | Description
---- | ---- | -----------
$function | \Timber\callback | 
$args | array | 

###### PHP
```php
<?php
	function the_form() {
	    echo '<form action="form.php"><input type="text" /><input type="submit /></form>';
	}
		$context = Timber::get_context();
	$context['post'] = new TimberPost();
	$context['my_form'] = TimberHelper::ob_function('the_form');
	Timber::render('single-form.twig', $context);
```
###### Twig
```twig
	<h1>{{ post.title }}</h1>
	{{ my_form }}
```
###### HTML
```html
	<h1>Apply to my contest!</h1>
	<form action="form.php"><input type="text" /><input type="submit /></form>
```

## osort
`osort( mixed $array, mixed $prop )`

**returns:** `void` 

Name | Type | Description
---- | ---- | -----------
$array | mixed | 
$prop | mixed | 



## <strike>paginate_links</strike>
**DEPRECATED** since 1.1.2

`paginate_links( array $args=array() )`

**returns:** `array` 

Name | Type | Description
---- | ---- | -----------
$args | array | 



## pluck
`pluck( array $array, string $key )`

**returns:** `void` 

Plucks the values of a certain key from an array of objects

Name | Type | Description
---- | ---- | -----------
$array | array | 
$key | string | 



## start_timer
`start_timer( )`

**returns:** `\Timber\float` 

For measuring time, this will start a timer



## stop_timer
`stop_timer( mixed $start )`

**returns:** `string` 

For stopping time and getting the data

Name | Type | Description
---- | ---- | -----------
$start | mixed | 

###### PHP
```php
<?php
	$start = TimberHelper::start_timer();
	// do some stuff that takes awhile
	echo TimberHelper::stop_timer( $start );
```

## transient
`transient( mixed $slug, mixed $callback, mixed $transient_time, mixed $lock_timeout=5, bool $force=false )`

**returns:** `mixed` 

A utility for a one-stop shop for Transients

Name | Type | Description
---- | ---- | -----------
$slug | mixed | 
$callback | mixed | 
$transient_time | mixed | 
$lock_timeout | mixed | 
$force | bool | 

###### PHP
```php
<?php
	$context = Timber::get_context();
	$context['favorites'] = Timber\Helper::transient('user-' .$uid. '-favorites', function() use ($uid) {
	 	//some expensive query here that's doing something you want to store to a transient
	 	return $favorites;
	}, 600);
	Timber::render('single.twig', $context);
```

## <strike>trim_words</strike>
**DEPRECATED** since 1.2.0

`trim_words( mixed $text, mixed $num_words=55, mixed $more=null, string $allowed_tags="p a span b i br blockquote" )`

**returns:** `string` 

Name | Type | Description
---- | ---- | -----------
$text | mixed | 
$num_words | mixed | 
$more | mixed | 
$allowed_tags | string | 



## warn
`warn( string $message )`

**returns:** `boolean` 

Name | Type | Description
---- | ---- | -----------
$message | string | that you want to output



## handle_transient_locking
`handle_transient_locking( mixed $slug, mixed $callback, mixed $transient_time, mixed $lock_timeout, mixed $force, mixed $enable_transients )`

**returns:** `void` 

Does the dirty work of locking the transient, running the callback and unlocking

Name | Type | Description
---- | ---- | -----------
$slug | mixed | 
$callback | mixed | 
$transient_time | mixed | 
$lock_timeout | mixed | 
$force | mixed | 
$enable_transients | mixed | 






