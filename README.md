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
$my_query = new WP_Query( $args );

// 3. on lance la boucle !


$val = 0;
$img = array();
if ( $my_query->have_posts() ) : while ( $my_query->have_posts() ) : $my_query->the_post() ?>

	<?php

	if ( ! empty( get_the_post_thumbnail_url() ) ) {
		$img[] = b64ize_image( get_the_post_thumbnail_url() );
	}



	$val ++;
endwhile;
endif;

// AFFICHER IMAGE
echo '<pre>';
var_dump( $img );
echo '</pre>';

// 4. On réinitialise à la requête principale (important)
wp_reset_postdata();
?>
```




