###README.md

Based on 'Magento DevDocs - Setup and Deployment' at http://devdocs.magento.com/

#Setup and Deployment

##System Requirements

See http://devdocs.magento.com/magento-system-requirements.html

Basically:

- PHP
- MySQL/MariaDB

Prerequisites

See http://devdocs.magento.com/guides/v2.1/install-gde/prereq/prereq-overview.html

##For Windows

First install XAMPP

http://www.wikihow.com/Install-XAMPP-for-Windows

XAMPP is an easy to install Apache distribution containing MariaDB, PHP, and Perl.

Download XAMPP from https://www.apachefriends.org/index.html

Follow the instructions of the installer.

Use the default installation directory at C:\xampp

When the XAMPP Control Panel opens after installation, start the Apache and MySQL components. 

NOTE: Should ports be already in use, stop the processes that used them thorugh Windows Services panel.

You can also start the other components, if you plan to use them.

Verify the Apache install, by clicking on the Apache administrative link in the Control Panel.

Verify the MySQL installation, by clicking on the MySQL administrative link in the XAMPP Control Panel.

If the verification steps are successful, XAMPP should be successfully installed on your PC. Open a browser and enter "localhost" on your address bar. You will be redirected to a page telling you that you've successfully installed xampp on your system

View php info at:

```javascript
http://localhost/dashboard/phpinfo.php
```

View phpMyAdmin at:

```javascript
http://localhost/phpmyadmin/
```

#Magento Database

Create a new database in MySQL through phpMyAdmin, e.g.:

```javascript
magento21 (for Magento 2.1 version)
```

You don't create tables in the new database yet. This will be done through the setup of Magento itself.

#Magento Download and Install

Download the Magento Community Edition (CE) version 2.1.x from https://magento.com/tech-resources/downloads/magento/

See also '***Magento Community Edition - Getting Started***' at http://docs.magento.com/m2/ce/user_guide/getting-started.html

This most up-to-date documentation for the current release combines easy-to-follow tutorials with comprehensive reference material.

See also '***Magento Designer's Guide***' at http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/bk-frontend-dev-guide.html

A practical guide to the concepts and best practices of theme design for Magento stores. Leverage structural components, theme hierarchy, and fallback methods to create custom themes

See also '***Magento Reference Developer Documentation***' at http://devdocs.magento.com/

Reference articles to assist developers and integrators with installations, upgrades, patches, and customizations.

See also '***Test Automation Framework***' at http://devdocs.magento.com/guides/v2.0/mtf/mtf_introduction.html

Get instructions on installing and configuring the Magento Testing Framework (MTF).

See also the '***Magento User Forum***' at http://community.magento.com/

Once downloaded the zip file of Magento software, extract the zipped file to the directory of C:\xampp\htdocs\magento21

