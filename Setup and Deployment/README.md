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

Advanced Options:

- HTTPS Options: 

  - [Unchecked] Use HTTPS for Magento Storefront
  - [Unchecked] Use HTTPS for Magento Admin

- Apache Rewrites: [Checked] Use Apache Web Server Rewrites

- Encryption Key:

  - [Checked] I want to use a Magento generated key

  - [Unchecked] I want to use my own encryption key

- Session Save: Files

Choose Next to go to the next step.

##Step 4: Customize Your Store

Store Default Time Zone: GMT (UTC)

Store Default Currency: US Dollar (USD)

Store Default Language: English (United States)

Advanced Modules Configurations:

- [Checked] Select all

122 out of 122 selected

Choose Next to go to the next step.

##Step 5: Create Admin Account

Create a new Admin account to manage your store.

New Username: magento21

New Email: wvanheemstra@icloud.com

New Password: <e.g. magento21>

Confirm Password: <e.g. magento21>

Choose Next to go to the next step.

##Step 6: Install

You're ready!

Click the button 'Install Now'.

A progress bar will show the progress of the installation.

Wait till it has reached 100%.

##Success

Success

Please keep this information for your records:

Magento Admin Info:

Username: magento21

Email: wvanheemstra@icloud.com

Password: ******

Your Store Address: http://localhost/magento21/

Magento Admin Address: http://localhost/magento21/admin_ho71mo/

Be sure to bookmark your unique URL and record it offline.

Encryption Key: c419879920ccc787378159a5b41fdb53

Database Info:

Database Name: magento21

Username: root

Password: ******

For security, remove write permissions from these directories: 'C:/xampp/htdocs/magento21/app/etc'

NOTE: Change the permissions in Windows by changing the properties of the directory 'etc', removing the permission to write.

Click the button 'Launch Magento Admin'.

#Signing in to Magento Admin Panel

Follow the URL to get to the Magento Admin Panel (e.g. http://localhost/magento21/admin_ho71mo/).

When prompted for a username and password, type:

```javascript
Username: magento21
Password: magento21
```

Click the button 'Sign in'.

#Dashboard of Magento Admin Panel

After successfully signing in to Magento, the Dashboard will be shown.

NOTE: Icons and images may be missing on this Dashboard. To get the images to show we have to do the following:

Run the following command from a Terminal, to install the static demo files:

```javascript
cd C:\xampp\htdocs\magento21
C:\xampp\php\php bin/magento setup:static-content:deploy
```

Now when you refresh the Dashboard (http://localhost/magento21/admin_ho71mo/admin/dashboard) all images should show.

NOTE: Should there be a number of System Messages, click on the number to view what is being warned.

E.g.: "One or more indexers are invalid. Make sure your Magento cron job is running."

In the above case, following the link to the indexer (http://localhost/magento21/admin_ho71mo/indexer/indexer/) will list all records and their status. 

Run the following command from a Terminal, to re-index files:

```javascript
cd C:\xampp\htdocs\magento21
C:\xampp\php\php bin/magento indexer:reindex
```

NOTE: if you want to reindex only one indexer then write following command:

```javascript
cd C:\xampp\htdocs\magento21
C:\xampp\php\php bin\magento indexer:reindex <indexer_name>
```

where indexer_name can be found by typing following command :

```javascript
cd C:\xampp\htdocs\magento21
C:\xampp\php\php bin\magento indexer:info
```

E.g.: "One or more of the Cache Types are invalidated: Page Cache. Please go to Cache Management and refresh cache types."

In the above case, following the link to the cache management (http://localhost/magento21/admin_ho71mo/admin/cache/index/)

Check the specified cache type, choose 'Refresh' from the actions drop down list and click Submit. The status for the specific Cache Type will have changed to Enabled.

#Home Page of Magento Store

After having installed the static files of the Magento Store, browse to the Home Page at:

```javascript
http://localhost/meganto21/
```

It will show the demo Home Page of the Luma theme.
