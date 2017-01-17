# Wordpress

## Images from article to base64 encoded string : 
```php
function b64ize_image($url_img){
	$image = file_get_contents($url_img);
	$type = pathinfo($url_img, PATHINFO_EXTENSION);
	$base64 = 'data:image/' . $type . ';base64,' . base64_encode($image);
	return $base64;
}
```


To put inside a loop : 

```php
$img = array();
   
if(get_the_post_thumbnail_url() != ''){
	$img[] =  b64ize_image(get_the_post_thumbnail_url());
}
```




