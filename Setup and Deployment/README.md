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

Create a new database in MySQL through phpMyAdmin (http://localhost/phpmyadmin), e.g.:

```javascript
magento21 (for Magento 2.1 version)
```

Choose for collation: utf8_unicode_ci

You don't create tables in the new database yet. This will be done through the setup of Magento itself.

#Magento Download and Install

Download the Magento Community Edition (CE) version 2.1.x from https://magento.com/tech-resources/downloads/magento/

For example, download Magento Community Edition 2.1.3 with Sample Data (which is a LUMA-based theme, populated with sample products, customer registration, and other common storefront data.).

See also '***Magento Community Edition - Getting Started***' at http://docs.magento.com/m2/ce/user_guide/getting-started.html

This most up-to-date documentation for the current release combines easy-to-follow tutorials with comprehensive reference material.

See also '***Magento Designer's Guide***' at http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/bk-frontend-dev-guide.html

A practical guide to the concepts and best practices of theme design for Magento stores. Leverage structural components, theme hierarchy, and fallback methods to create custom themes

See also '***Magento Reference Developer Documentation***' at http://devdocs.magento.com/

Reference articles to assist developers and integrators with installations, upgrades, patches, and customizations.

See also '***Test Automation Framework***' at http://devdocs.magento.com/guides/v2.0/mtf/mtf_introduction.html

Get instructions on installing and configuring the Magento Testing Framework (MTF).

See also the '***Magento User Forum***' at http://community.magento.com/

Once downloaded the zip file of Magento software, extract the zipped file inside the directory of C:\xampp\htdocs\magento21

This video shows the procedure to follow, 'How to Install Magento 2 Community Edition using XAMPP on Windows 10' at https://www.youtube.com/watch?v=Voq2XarSSBA&t=5s

#Start Apache and MySQL in XAMPP

Open the XAMPP Control Panel, click the 'Start' button for Apache and MySQL.

Then open a browser window and browse for:

```javascript
http://localhost/phpmyadmin
```

Verify that the previously created database 'magento21' exists (even though it has no tables yet).

#Magento Setup

Open a browser window and browse for:

```javascript
http://localhost:magento21
```

NOTE: If you named the directory where you installed Magento differently, use that directory name instead.

The browser will forward you to the setup page of your new Magento.

Click on the button ***Agree and Setup Magento***.

##Step 1: Readiness Check

Click on the button ***Start Readiness Check***.

It will check for:

- PHP Version Check: Checks if you have the required version of PHP.

- PHP Settings Check: If you need to make changes in php.ini, look at http://localhost/dashboard/phpinfo.php where php.ini is installed (e.g. Loaded Configuration File	C:\xampp\php\php.ini) and make the required changes. Restart Apache server for the changes in php.ini to take effect!

- PHP Extensions Check: If you need to enable extensions (by uncommenting the respective dll) in php.ini, look at http://localhost/dashboard/phpinfo.php where php.ini is installed (e.g. Loaded Configuration File	C:\xampp\php\php.ini) and make the required changes. Restart Apache server for the changes in php.ini to take effect!

- File Permission Check: Checks File Permissions.

When all checks are green ticked, you are ready to go to the next step.

##Step 2: Add a Database

Enter the following details in the form:

Database Server Host: localhost

Database Server Username: root

Database Server Password: <choose one (e.g. root), then make a note of it so as to not to forget>

Database Name: magento21 

NOTE: This should match the database name created in MySQL previously.

Table prefix: <leave empty>

WARNING! We need now to activate the password in both MySQL as well as myPHPAdmin (as the default password for 'root' is empty).

In a terminal window, type:

```javascript
cd C:\xampp\mysql\bin\mysql -u root
mysql> UPDATE mysql.user SET Password=PASSWORD('root') WHERE User='root';
mysql> commit;
mysql> quit
```

Find your config.inc.php file under the phpMyAdmin installation directory and update the line that looks like
this:

$cfg['Servers'][$i]['password'] = '';

... to this:

 $cfg['Servers'][$i]['password'] = 'root';

Now stop and start MySQL only (!) in the XAMPP Control Panel.

Choose Next to go to the next step.

##Step 3: Web Configuration

Enter the following details in the form:

Your Store Address: http://localhost/magento21/

Magento Admin Address: 
http://localhost/magento21/admin<unique number, e.g. _ho71mo>





