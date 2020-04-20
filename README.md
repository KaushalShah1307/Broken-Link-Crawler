# Broken-Link-Crawler
A Python project that captures all the links, recursively, from any websites sitemap.xml file and checks whether the links are ok or are broken. It also send an email notification upon completion of the checks.

# linkChecker
A simple website URL and link checker. It crawls through a given sitemap for every accessible URL, checks that the response is 200 (OK). It then procedes to check every link in the html of that page. 

This program does not create a sitemap.xml for you, so for that you can a website such as https://www.xml-sitemaps.com/.

## Setup 

Note: Make sure to have Python pre-installed on your system before moving forward.

There are few packages and libraries that you'll be required to install. These packages, for your benifit, have been added as lineitems within the requirements.txt file.

To install the required packages use `pip`:
`pip install -r requirements.txt`

## Usage
### Command Line & Server side
Copy the contents of the `conf/conf.ini.example` file into `conf/conf.ini` in the same directory. 

Modify your config file with the details for your site:

#### GENERAL CONFIG

|Config option|Description|
|-------------|-----------|
SiteName|The name of your site, this is for display only and gets used in the output for easier identification
UseLocalFile|yes (default) / no
LocalSitemapFile | File path + name relative to this directory
DownloadSitemap | yes / no (default)
RemoteSitemapUrl | The url of the sitemap hosted on your website
OutputToFile | yes (default) / no
OutputFileName | Name of the file that the results will store. Can be placed elsewhere using relative path
LogfileDirectory| The directory where logs will be saved, ensure you have the correct permissions for the directory. The script will a directories per site, ie: `<LogFileDirectory>/Broken-Link-Crawler/<SiteName>/<date-of-scan>`


#### EMAIL CONFIG

|Config option|Description|
|-------------|-----------|
EmailOutput|yes (default) / no
SMTPDomain|The domain that will be used to send these emails from (eg. smtp.gmail.com or smtp.mailtrap.io)
AdminEmailAddress|The address of that emails will be sent from
AdminEmailPassword|The password of the Admins email account -> **PLAIN TEXT!**
RecipientEmailAddresses|The recipient(s) email where the output gets sent to. Separate multiple emails with ','

#### AUTH CONFIG

For sites that are protected behind a username and password, you can authenticate by providing the username and password in the config. 

**WARNING** These are stored in plain text, so the right priviledges should be granted to keep them as secure as possible. 

|Config option|Description|
|-------------|-----------|
SiteUsername| The username for the protected site
SitePassword| The password for the protected site -> **Plain Text**


To run the script, ensure you have python (min <2.7) installed and run:
`python3 linkChecker.py`

#### MULTI CONFIGS
You can pass the config file name as a Command line argument, this is useful for multiple sites with a config for each site. ie: 

`python3 linkchecker.py mysite.ini`

`python3 linkchecker.py mysecondsite.ini`

### Graphical interface
Enter the Broker-Link-Crawler directory, and run:
`python3 main.py`

From here you can enter or browse for the filename of the XML sitemap, and click enter. 

#### HTTP Auth
If your site has http authentication, then you will be asked to enter the username and password for the site. These details are not stored. 

The script will carry out the test on every url, and then output a report of all the broken links found.