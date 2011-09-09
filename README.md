Flutie
======

[![Build Status](https://secure.travis-ci.org/thoughtbot/flutie.png?branch=master)](http://travis-ci.org/thoughtbot/flutie)

Basic, default styles for rails applications

Installation & Upgrading
------------------------

Flutie is a Rails engine. It works with versions of Rails greater than 3.0.

Flutie is recommended to be run as a gem and included in your Gemfile:

    gem "flutie"

After you've bundled, if you are using Rails < 3.1, run the installer:

    rake flutie:install

The installer will copy the Flutie stylesheets sass into public/stylesheets/sass/flutie, and a static flutie.css into public/stylesheets/ in your app.

Once Flutie is installed, with your application running (not in production environment) you can browse to /styleguides.  This will present you with many standard markup elements that are present in a Rails application, in your default application layout.

Click on the "Default styles" link to view the same markup with a barebones layout that only contains the Flutie stylesheets. Click on "Application styles" to view the markup in your application layout.

To upgrade, bump the gem version in your Gemfile, and then run 'rake flutie:install' again to get the latest changes moved into your application.

If you are using rails 3.1 or greater with asset pipelining enabled, you don't need to run the installer.  Simply add:

    *= require _flutie

in the application stylesheet manifest (app/assets/stylesheets/application.css), or:

    @import 'flutie';

as a sass import.

Usage
-----

Flutie registers a :flutie shortcut for stylesheets, so in your layout you can do...

    <%= stylesheet_link_tag :flutie, 'admin', :cache => true %>

...this will include all the flutie stylesheets, then the 'admin' stylesheet, and it will cache them all into one file.

### Sass

If you use Sass in your application, the flutie stylesheets are also available as scss files, installed in public/stylesheets/sass/flutie.  These files can be imported into your own sass files for use with the following:

    @import "flutie/flutie";

You'll want to import flutie before any of your own styles so that you can do things like extend your classes with flutie classes.

We also have a [Bourbon](https://github.com/thoughtbot/bourbon) gem available, which can be used to extend flutie with a set of vanilla sass mixins.

### Custom Styles

To add custom styles to the styleguide add partials to the app/views/styleguides directory. For example:

    app/views/styleguides/_todo_item.erb:

    <ol>
      <li class="todo">This is a todo item</li>
    </ol>

Plugin authors can also add to the styleguide by ensuring that their view path is in ActionController::Base.view_paths and by placing a partial under the styleguides directory. For example:

    ActionController::Base.append_view_path(File.join(File.dirname(__FILE__), 'views'))

    my_awesome_plugin/views/styleguides/_pagination.erb:

    <div class="pagination">
      <a href="#prev">Previous</a>
      <a href="#next">Next</a>
    </div>

Suggestions, Bugs, Refactoring?
-------------------------------

Fork away and create a [Github Issue](http://github.com/thoughtbot/flutie/issues). Please don't send pull requests.

Please see CONTRIBUTING.md for details.

Development
-----------

The actual stylesheet source files are sass, so edit the files in app/assets/stylesheets/.
To rebuild the static flutie.css file, you can run:

    sass --update app/assets/stylesheets/_flutie.scss:public/stylesheets/flutie.css

You can run a server which will allow you to view the flutie styleguide locally:

    ruby server.rb

Browsing to localhost at the port output by the above command will show you the styleguide.

Credits
-------

![thoughtbot](http://thoughtbot.com/images/tm/logo.png)

Flutie is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community)

Thank you to all [the contributors](https://github.com/thoughtbot/flutie/contributors)!

The names and logos for thoughtbot are trademarks of thoughtbot, inc.

License
-------

Flutie is Copyright © 2010-2011 thoughtbot. It is free software, and may be redistributed under the terms specified in the LICENSE file.
