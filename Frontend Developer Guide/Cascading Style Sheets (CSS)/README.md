###README.md

Based on 'Cascading Style Sheets (CSS)' at http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/css-topics/css-overview.html

#Cascading Style Sheets (CSS)

##Overview

Magento 2 incorporates ***LESS***, a CSS pre-processor that simplifies the management of complex CSS files. To define styles of a Magento store, you can use both - CSS and LESS stylesheets.

Magento application provides a built-in LESS UI library, which you can optionally extend.

To customize storefront styles, you need to create a custom design theme. Then you can use one of the following approaches:

- If your theme inherits from the Magento out-of-the-box Blank or Luma theme, you can override the default LESS files; for example to change the values of the variables used in the default files.
- Create your own LESS files using the built-in LESS preprocessor.
- Create your own CSS files, optionally having compiled them using third-party CSS preprocessor.