###README.md

Based on 'Themes' at http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/themes/theme-general.html

#Themes

The Themes chapter provides all information, including theoretical concepts and practical references, a frontend developer might need to efficiently create a new theme for storefront or Admin in Magento application.

##Create a storefront theme

Based on 'Create a storefront theme' at http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/themes/theme-create.html

See also 'MAGENTO 2: HOW TO CREATE YOUR OWN THEME IN MAGENTO 2.0' at https://astrio.net/blog/magento-2-theme-creation/

###Step 1. Create a directory for the theme (e.g. my_theme_name):

```javascript
magento21/app/design/frontend/MyVendorName/my_theme_name/
```

Note: As you can see, the folder name of the vendor is capitalized. It is not a requirement, just a recommendation from Magento 2 developers.

###Step 2. Add a declaration file theme.xml and optionally create etc directory and create a file named view.xml to the theme directory.

```javascript
magento21/app/design/frontend/MyVendorName/my_theme_name/theme.xml
```

theme.xml
```javascript
<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Config/etc/theme.xsd">
     <title>My Theme Name</title> <!-- your theme's name -->
     <parent>Magento/blank</parent> <!-- the parent theme, in case your theme inherits from an existing theme -->
     <media>
         <preview_image>media/preview.jpg</preview_image> <!-- the path to your theme's preview image -->
     </media>
</theme>
```

```javascript
magento21/app/design/frontend/MyVendorName/my_theme_name/etc/view.xml
```

If you change the theme title or parent theme information in theme.xml after a theme was already registered, you need to open or reload any Magento Admin page for your changes to be saved in the database.

###Step 3. Make your theme a Composer package (optional)

To organize your theme as a package, add the composer.json file to the theme directory and register the package on the server.

```javascript
magento21/app/design/frontend/MyVendorName/my_theme_name/composer.json
```

Example of a theme composer.json:

```javascript
{
    "name": "myvendorname/my-theme-name",
    "description": "N/A",
    "require": {
        "php": "~5.5.0|~5.6.0|~7.0.0",
        "magento/theme-frontend-blank": "100.0.*",
        "magento/framework": "100.0.*"
    },
    "type": "magento2-theme",
    "version": "100.0.1",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "autoload": {
        "files": [
            "registration.php"
        ]
    }
}
```

You can find details about the Composer integration in the Magento system in Composer integration.

###Step 4. Add registration.php

In order to register the theme in the system, you must create the registration.php file in the theme folder, with the following content:

```javascript
<?php
/**
 * Copyright © 2016 Magento. All rights reserved.
 * See COPYING.txt for license details.
 */
\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::THEME,
    'frontend/MyVendorName/my_theme_name',
    __DIR__
);
```

###Step 5. Configure images

Product image sizes and other properties used on the storefront are configured in a view.xml configuration file. It is required for a theme, but is optional if exists in the parent theme.

If the product image sizes of your theme differ from those of the parent theme, or if your theme does not inherit from any theme, add view.xml using the following steps:

1. Log in to your Magento server as a user with permissions to create directories and files in the Magento installation directory. (Typically, this is the the Magento file system owner.)

2. Create the etc directory in your theme folder

3. Copy view.xml from the etc directory of an existing theme (for example, from the Blank theme) to your theme’s etc directory.

4. Configure all storefront product image sizes in view.xml. For example, you can make the category grid view product images square by specifying a size of 250 x 250 pixels, here is how the corresponding configuration would look like:

```javascript
...
    <image id="category_page_grid" type="small_image">
        <width>250</width>
        <height>250</height>
    </image>
...
```

For details about images configuration in view.xml, see the Configure images properties for a theme topic.

###Step 6. Internationalization and translation

In the Magento 1.9.x version, the CSV files with translations are stored in the theme directory. To be more specific the translate.csv file with translation entries, stored in the "locale" folder, inside language folder, e.g. "ru_RU" or "en_US" folders, this way: <theme folder>/locale/en_US/translate.csv

The Magento 2 approach is a bit different. Now, at the root of the theme directory, you should create a folder with the name "i18n". And create a file with translation in the "i18n" folder, e.g. "en_US.csv".

Note: The "i18n" term is numeronym (where 18 stands for the number of letters between the first "i" and the last "n" in the word "internationalization").

Example: <theme folder>/i18n/en_US.csv

###Step 7. Create directories for static files

In order to store the static theme files (e.g. CSS style files, images, fonts or JavaScript files), you should create the "web" folder in the theme root directory, with the following directories inside: "css/source", "fonts", "images" and "js".

```javascript
MyVendorName/
  my_theme_name/
    web/
      css/
        source/
      fonts/
      images/
      js/
```

Note: The "web" folder (located in the root of the theme directory) used to store theme static files. If you need to connect a file for some specific module, you should create a module directory in the theme folder and create there a "web" folder with the structure described above.

Example: /<theme>/<Namespace_Module>/web/

```javascript
MyVendorName/
..my_theme_name/
....web/
......css/
........source/
......fonts/
......images/
......js/
....my_module_name/
......web/
........css/
..........source/
........fonts/
........images/
........js/    
```

NOTE During theme development, when you change any files stored here, you need to clear pub/static and var/view_preprocessed directories, and then reload the pages. Otherwise the old versions of files are displayed on the storefront.

Magento 2 has a new organization structure, where there is a clear separation between module files and theme files.

###Step 8: Defining the theme logotype

