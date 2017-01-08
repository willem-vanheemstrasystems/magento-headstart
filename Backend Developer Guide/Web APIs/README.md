###README.md

Based on 'Getting Started with Magento Web APIs' at http://devdocs.magento.com/guides/v2.1/get-started/bk-get-started-api.html

See also 'Magento Meetup New Delhi - Magento Web Services/API' at https://www.youtube.com/watch?v=daC2GvdFrfo

See also 'Tutorial Magento API REST integration workflow' at https://www.youtube.com/watch?v=Mj1icy_6Cro

#Web APIs

##What are the Magento web APIs?

The Magento web API framework provides integrators and developers the means to use web services that communicate with the Magento system. Key features include:

Support for both REST (Representational State Transfer) and SOAP (Simple Object Access Protocol). In Magento 2, the web API coverage is the same for both REST and SOAP.

Three types of authentication:

- Third-party applications authenticate with OAuth 1.0a.
- Mobile applications authenticate using tokens.
- Administrators and customers are authenticated with login credentials.

All accounts and integrations are assigned resources that they have access to. The API framework checks that any call has authorization to perform the request.

Any Magento or third-party service can be configured as a web API with a few lines of xml.

To configure a web API, you define XML elements and attributes in a webapi.xml configuration file. If a service is not defined in a configuration file, it will not be exposed at all.

The framework is based on the CRUD (create, read, update, delete) & search model. The system does not currently support web hooks.

The framework supports field filtering of web api responses to conserve mobile bandwidth.

Integration style web API’s enable a single web API call to run multiple services at once for a more efficient integration. An example of this behavior can be see in the Catalog where one web API call can create a product; if your payload includes the inventory object and media object then the framework will also create the product’s inventory & media in that one API call.

##What can I do with the Magento web APIs?

The APIs can used to perform a wide array of tasks. For example:

- Create a shopping app. This can be a traditional app that a user downloads on a mobile device. You could also create an app that an employee uses on a showroom floor to help customers make purchases.

- Integrate with CRM (Customer Relationship Management) or ERP (Enterprise Resource Planning) back-end systems, such as Salesforce or Xero.

- Integrate with a CMS (Content Management System). At present, content tagging is not supported.

- Create JavaScript widgets in the Magento storefront or on the Admin panel. The widget makes AJAX calls to access services.

##How do I get started?

You must register a web service on Magento Admin. Use the following general steps to set up Magento to enable web services.

1. If you are using token-based authentication, create a web services user on Magento Admin by selecting System > All Users > Add New User. (If you are using session-based or OAuth authentication, you do not need to create the new user in the Admin.)
2. Create a new integration on Magento Admin. To create an integration, click System > Integration > Add New Integration. Be sure to restrict which resources the integration can access.
3. Use a REST or SOAP client to configure authentication.

See the User Guide for more information.