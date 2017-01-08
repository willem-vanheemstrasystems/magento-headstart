###README.md

Based on 'Templates' at http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/templates/template-overview.html

#Templates

Introduction to customizing a theme using templates

In Magento application templates are the part of the view layer. Templates define exactly how the content of layout blocks is presented on a page: order, CSS classes, elements grouping, and so on. In most cases, templates do not contain any logic about whether they will or will not be rendered, this is typically handled by the layout files. Once a template is called in a layout, it will be displayed.

Default Magento templates are PHTML files. Also HTML templates are used for Knockout JS scripts.

This chapter describes how to customize templates in your design theme, and provides both the practice reference and the theoretical background of how templates are applied in a Magento store.

We strongly recommend that you do not change the default templates, because if you do edit them, your changes can be overwritten by the new version of the default files during upgrades. The best practice is creating a new design theme and adding your modified templates there.

This chapter contains the following topics:

- Template customization walkthrough
- Templates basic concepts
- Illustration of customizing templates
- Customizing email templates