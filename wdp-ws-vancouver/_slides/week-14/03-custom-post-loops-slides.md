---
layout: slidedeck
title: Custom Post Loops Slides
---

{% highlight html %}
name: inverse
layout: true
class: center, middle, inverse

---

# Custom Post Loops

.title-logo[![Red logo](/public/img/red-logo-white.svg)]

---

layout: false

# Agenda

1. 4 Ways to Loop Posts
2. `WP_Query`

---

template: inverse

# Custom Post Loops

---

class: center, middle

.large[
**Why?**
]

---

# 4 Ways to Loop

1. The default loop (aka **main loop** or **main query**)
2. `query_posts()`
3. `WP_Query`
4. `get_posts()`

---

# Default Loop

* Uses the main query to loop through post content/meta (e.g. `the_title`, `the_content`)
* The main query is the one triggered automatically when WordPress has determined what to show based on the request URI (different depending on the template!)
* Look at the template files in `redstarter`...it's everywhere

---

# What It Looks Like

The default loop:

```php
<?php if ( have_posts() ) : ?>

   <?php while ( have_posts() ) : the_post(); ?>

      <h2><?php the_title(); ?></h2>
      <?php the_content(); ?>

   <?php endwhile; ?>

   <?php the_posts_navigation(); ?>

<?php else : ?>

   <h2>Nothing found!</h2>

<?php endif; ?>
```

---

# query_posts()

* `query_posts` allows us to alter our **default loop**
* It's inefficient and often produces unexpected results
* **NEVER USE THIS!**
* If you need to mess with the main loop use the `pre_get_posts` hook (and use sufficient conditionals)

---

# What It Looks Like

Using `query_posts()`:

```php
<?php
   global $query_string; // required
   query_posts( $query_string . '&posts_per_page=3&order=ASC' );
?>

   <?php /* DEFAULT LOOP STUFF GOES HERE */ ?>

<?php wp_reset_query(); ?>
```

---

class: center, middle

.large[
Now you know, <br />but again, don't use it!
]

---

# WP_Query

* For complete, fine-grained control over creating custom loops in WordPress
* Allows you to create **secondary loops** (aka **custom queries**)
* It's not a function, it's a **class** (which we use to create objects, and these objects can access the properties and methods of the class...more on that tomorrow!)
* It's powerful&mdash;you can create incredibly complex queries with it, and break your site at scale if you're not careful

---

# What It Looks Like

It looks a lot like the default WP loop, with some exceptions:

```php
<?php
   $args = array( 'post_type' => 'product', 'order' => 'ASC' );

   $products = new WP_Query( $args ); // instantiate our object
?>

<?php if ( $products->have_posts() ) : ?>

   <?php while ( $products->have_posts() ) : $products->the_post(); ?>

      <?php /* Content of the queried post results goes here */ ?>

   <?php endwhile; ?>
   <?php wp_reset_postdata(); ?>

<?php else : ?>

      <h2>Nothing found!</h2>

<?php endif; ?>
```

---

# get_posts()

* A wrapper for `WP_Query`
* However, it's a function (not an object instantiated from the `WP_Query` class) so none of the `WP_Query` methods will be available to you
* What it does is returns an array of `WP_Post` objects that you can loop over yourself

---

# What It Looks Like

We pass `$args` into `get_posts()` just like we do `WP_Query`, but we handle the output a bit differently:

```php
<?php
   $args = array( 'post_type' => 'product', 'order' => 'ASC' );

   $product_posts = get_posts( $args ); // returns an array of posts
?>

<?php foreach ( $product_posts as $post ) : setup_postdata( $post ); ?>

   <?php /* Content from your array of post results goes here */ ?>

<?php endforeach; wp_reset_postdata(); ?>
```

---

template: inverse

# WP_Query, in Detail

---

# Main vs. Secondary

* The **default loop** is based on the **URL request** and is processed before templates are loaded (remember when we looked at the query strings?)
* The **secondary loops** are **additional database queries** (using arguments passed into `new WP_Query()`) in theme template or plugin files

---

# All About the $args

The `$args` are where the magic happens in `WP_Query`:

```php
$args = array(
   'order' => 'ASC',
   'posts_per_page' => 8,
   'post_type' => 'product',
   'tax_query' => array(
      array(
         'taxonomy' => 'product-type',
         'field'    => 'slug',
         'terms'    => 'bread',
      ),
   ),
);

$products = new WP_Query( $args );
```

Explore all the **[available parameters in the Codex](https://codex.wordpress.org/Class_Reference/WP_Query#Parameters)** and have fun...but remember to **be responsible** about this!

---

# In Use

We can use all of our normal loop functions!

```php
<?php $products = new WP_Query( $args ); /* $args set above*/ ?>

<?php if ( $products->have_posts() ) : ?>

   <?php while ( $products->have_posts() ) : $products->the_post(); ?>

      <h1><?php the_title(); ?></h1>
      <?php the_content(); ?>

   <?php endwhile; ?>

   <?php the_posts_navigation(); ?>
   <?php wp_reset_postdata(); ?>

<?php else : ?>

      <h2>Nothing found!</h2>

<?php endif; ?>
```

---

# wp_reset_postdata()

According to the Codex, `wp_reset_postdata` will &#8220;restore the global `$post` variable of the **main query** loop after a **secondary query** loop using `new WP_Query`. It restores the `$post` variable to the current post in the main query.&#8221;

Whether using `WP_Query` directly or `get_posts()`, you will often be creating a secondary loop within _the default loop_.

For that reason, you need to **reset** the `WP_Post` object to the main query's post when your done with your secondary loop.

---

class: center, middle

.large[
Remember that `get_posts()` is a wrapper for `WP_Query`, so it does *almost* everything that `WP_Query` does, but what you get back from WP is very different.
]

---

# Subtle Differences

* `get_posts` should be faster than `WP_Query`
* `get_posts` returns the `$posts` property of `WP_Query` only, while `WP_Query` returns the complete object (which means you can access all of its properties and methods)
* `get_posts` doesn't use the loop, and requires a `foreach` loop to display posts.
* No template tags are available by default with `get_posts`, but you can use `setup_postdata( $post )` to make them available

---

# Which Do I Pick?

* Use `WP_Query` when you need to create a paginated query
* Use `get_posts()` to create static, additional loops (e.g. a list of a few recent posts on a homepage, etc.)

---

# Exercise 1

Let's try building a custom post loop for Project 4 by building the news feed on the homepage.

You'll need to decide whether to use `WP_Query` or `get_posts` first, then you need to create and pass in an array of the appropriate arguments, and finally figure out how to display the returned data on your homepage.

Don't worry about styling yet, just grab the data!

---

# What We've Learned

* How to loop all the things in WP
* The dos and do-not-dos of secondary loops with WP Query

---

template: inverse

# Questions?

{% endhighlight %}