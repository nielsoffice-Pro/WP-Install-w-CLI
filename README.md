# WP-Install-with-CLI

``` Run in terminal inside the project folder : ``` 

``` 

// Live
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

// localhost
curl --ssl-no-revoke -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

```

``` Create file and save in project directory with file name  [ wp.bat ] ```
```

@ECHO OFF
php "C:\wp-cli\wp-cli.phar" %* 

/* update in your project directory */
C:\xampp\projectname\wp-cli.phar

```

```

Open System Properties:

Press Win + R, type sysdm.cpl, and press Enter.

#Open Environment Variables:

 * In the System Properties window, go to the Advanced tab.
 * Click on Environment Variables....

#Edit the PATH Variable:

 * In the Environment Variables window, under System variables, find the Path variable and select it.
 * Click Edit....

#Add the New PATH:

 * In the Edit Environment Variable window, click New.
 * Add the path to the directory where wp.bat is located (e.g., C:\xampp\project-file\).
 * Click OK to close all windows.

#Test the Installation
  wp --info

```

Basic Commands

```
// Installing WordPress
wp core download

// DB Create
wp config create --dbname=your_db_name --dbuser=your_db_user --dbpass=your_db_password
wp db create

// WP Config
wp config create --dbname=your_db_name --dbuser=your_db_user --dbpass=your_db_password --dbhost=localhost

// WP Install
wp core install --url="your_site_url" --title="Your Site Title" --admin_user="your_admin_user" --admin_password="your_admin_password" --admin_email="your_email@example.com"
wp core install --url="http://localhost/your_site" --title="My WordPress Site" --admin_user="admin" --admin_password="password" --admin_email="admin@example.com"


// WP Update by any chance: 
>> cd C:\path\to\your\wordpress\directory
wp option update home "http://localhost/my_new_site"
wp option update siteurl "http://localhost/my_new_site"
wp search-replace 'http://localhost/your_old_site' 'http://localhost/my_new_site'
wp rewrite flush

// Core and DB Update
wp core update
wp core update-db

```

Plugin command
```

>> wp plugin install plugin-slug

>> wp plugin activate plugin-slug

>> wp plugin deactivate plugin-slug

>> wp plugin update --all

```

Theme command
```

>> wp theme install theme-slug

>> wp theme activate theme-slug

>> wp theme update --all

```

Scaffold
```

wp scaffold _s <theme-name> --theme_name="<Theme Name>" --author="<Author Name>" --author_uri="<Author URI>" --activate

// Demo Data
wp scaffold _s my-theme --theme_name="My Theme" --author="John Doe" --author_uri="https://example.com" --activate

```

User lists
```

>> wp user list

// Create new user
wp user create username email@example.com --role=author --user_pass=your_password

```

Database Commands:
```
>> wp db export
>> wp db import filename.sql
>> wp db optimize

```

Post Commands:
```
>> wp post create --post_type=post --post_title='Your Post Title' --post_status=publish

>> wp post list

```

Custom Command
```PHP

<?php
if ( defined( 'WP_CLI' ) && WP_CLI ) {
    class My_Custom_Command {
        public function my_command() {
            WP_CLI::success( "Hello, WP-CLI!" );
        }
    }
    WP_CLI::add_command( 'my_command', 'My_Custom_Command' );
}
''
require_once get_template_directory() . '/path/to/my-command.php';

// Run command:
wp my_command

```

Dependecies:
- Composer
- GitBash
- CMD

Resouces:
<br><a href="https://make.wordpress.org/cli/handbook/">WP-CLI Handbook</a>
<br><a href="https://developer.wordpress.org/cli/commands/">WP-CLI Commands</a>
<br><a href="https://make.wordpress.org/cli/handbook/quick-start/">Quick Start</a>

