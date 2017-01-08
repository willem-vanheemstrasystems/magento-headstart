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

