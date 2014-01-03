---
layout: post
title:  Declutter
---

We now have a working homepage AND a menu - that's pretty sweet! Next thing to do, though, it to remove the stuff that comes with the framework project that we're not going to use. It's all good stuff, I recommend you have a good look at it before you delete it. To be honest, it won't matter if you don't but for my sample code I have removed it.

## Removing Pages

Pages demonstrates simple blog functionality. Remove:

* app/controllers/PagesController.php
* app/views/pages
* app/views/hello_world (deleted its controller in the last chapter)

## Updating our home screen

Notice that now there is no "Pages" controller to handle the default route

TODO screenshot

So, let's make our HomeController the default! Open up app/config/routes.php and remove this code:

{% highlight php %}
<?php
// ...

/**
 * Here, we are connecting `'/'` (the base path) to controller called `'Pages'`,
 * its action called `view()`, and we pass a param to select the view file
 * to use (in this case, `/views/pages/home.html.php`; see `app\controllers\PagesController`
 * for details).
 *
 * @see app\controllers\PagesController
 */
Router::connect('/', 'Pages::view');

/**
 * Connect the rest of `PagesController`'s URLs. This will route URLs like `/pages/about` to
 * `PagesController`, rendering `/views/pages/about.html.php` as a static page.
 */
Router::connect('/pages/{:args}', 'Pages::view');
// ...
{% endhighlight %}

Now we're going to replace that section with:

{% highlight php %}
<?php
// ...
Router::connect('/', 'Home::index');
// ...
{% endhighlight %}

Now, when you hit [http://staff-rolodex.localhost/](http://staff-rolodex.localhost/), you should see your "This is a HOME PAGE!" screen. Result!

TODO screenshot

## About "empty"

You'll notice a bunch of files just named "empty" - that's to make sure that they stay in the Git repo. You can delete them, but I recommend leave them alone - at least until you've put something else in each empty directory - so you can easily figure out where things need to go.