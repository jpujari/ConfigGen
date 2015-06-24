ConfigGen
=========

Magento Config Data Generator

I firmly believe that you should try not to use the magento admin to make configuration adjustments.

The main mindset behind this is to prevent changes made in a development environment, not to go live with your deployment of code. 
It can be quite embarresing when your new super duper module works incorrectly on live, just because you forgot to configure live the same as your dev system.
A simple yes/no config change forgotten can make the world of difference on a new feature.

However, it is extremely time consuming (not to mention mundane) to create the required scription code, and having to do it multiple times just gets too frustrating.
 
This module eases the task in creating scripted admin config changes.

Once installed, a new menu option appears under Systsem->Tools simply called ProxiBlue Config Generator.

The new option will display a grid, which displays all the config values held in the core_config_data database table (thus all the admin config settings)
You can then simply select the options you wish to export, and a config script will be generated, and downloaded.
 
You can then place the generated script as one of your module install files, and it will reload the config values exported when your module install.

The script created will be like this:

<?php
/**
 * This file was generated by using ProxiBlue Config Generator
 * You can edit the generated config file by making changes in the template file
 * proxiblue_configgen.phtml located in the admin design folder.
 * 
 * Latest code available from our website www.proxiblue.com.au
 * 
 */

$installer = $this;
$installer->startSetup();

$config = new Mage_Core_Model_Config();

$configItems = json_decode('[{"config_id":"5","scope":"default","scope_id":"0","path":"web\/unsecure\/base_url","value":"http:\/\/giftpromodemo.dev.proxiblue.com.au\/"},{"config_id":"6","scope":"default","scope_id":"0","path":"web\/secure\/base_url","value":"http:\/\/giftpromodemo.proxiblue.com.au\/"}]');

foreach ($configItems as $configItem) {
    $config->saveConfig($configItem['path'], $configItem['value'], $configItem['scope'], $configItem['scope_id']);
}

$installer->endSetup();


Premium extentions:
----------------------
[Magento Free Gift Promotions](http://www.proxiblue.com.au/magento-gift-promotions.html "Magento Free Gift Promotions")
The ultimate magento gift promotions module - clean code, and it just works!

[Magento Dynamic Category Products](http://www.proxiblue.com.au/magento-dynamic-category-products.html "Magento Dynamic Category Products")
Automate Category Product associations - assign any product to a category, using various rules.

