# BMEcat Export Add-on for Pimcore Data Director

This bundle adds a result callback function template to Data Director's attribute mapping to create a BMEcat export feeds. 

As it uses Data Director's export capabilities, your BMEcat exports profit by:

* everything is configurable in Pimcore backend user interface - no creation of PHP files or anything similar necessary
* access any data which is connected to exported products, for example when you can easily access assigned categories, price information, manufacturers, product features images etc.
* full flexibility in setting up a transformation pipeline to change values to the desired format (e.g. some BMEcat-processing applications have restrictions on length of some fields)
* supported BMEcat versions: 1.2, 2005.1
* automatically execute exports whenever a product object gets saved whose data gets exported to:
    * prepare export once the data changes, so that the data does not have to be generated in the moment when the export is requested -> very fast exports because the export document is already available in the moment of request -> you will have an always up-to-date BMEcat export
    * upload exports automatically to a target system to always have up-to-date data there
    * automatically send data the other APIs
* intelligent checks whether anything changed since the last export. If nothing changed, export document gets delivered from cache
* access exports via URL, for example to pull BMEcat export into an external system

## Installation
To use this plugin you have to first buy and install [Pimcore Data Director](https://pimcore.com/en/developers/marketplace/blackbit_digital_commerce/pimcore-data-director_e103850).

Please contact us to get access to the bundle's [Bitbucket repository](https://bitbucket.org/blackbitwerbung/pimcore-plugins-data-director-bmecat) or you get the plugin code as a zip file. 
When we permit your account to access our repository, please add the repository to the `composer.json` in your Pimcore root folder (see [Composer manual about repositories](https://getcomposer.org/doc/05-repositories.md#vcs)):
```json
"repositories": [
    {
        "type": "vcs",
        "url": "https://bitbucket.org/blackbitwerbung/pimcore-plugins-data-director-facebook"
    }
],
```

Alternatively if you received the plugin code as zip file, please upload the zip file to your server (e.g. to the Pimcore root folder) and add the following to your `composer.json`:
```json
"repositories": [
    {
        "type": "artifact",
        "url": "path/to/directory/with/zip-file/"
    }
]
```

Then you should be able to execute `composer require blackbit/data-director-bmecat` (or `composer update blackbit/data-director-bmecat --with-dependencies` for updates if you already have this bundle installed) from CLI.

You can always access the latest version by executing `composer update blackbit/data-director-bmecat` on CLI.

## Setup export

Select `BMEcat Export` from the list of templates for the `Result Callback function` in data director's attribute mapping.

Then the fields which the BMEcat standard defines will appear as *virtual* fields in attribute mapping. To those fields you can map your data object class fields via drag & drop (and additional callback functions if necessary). Afterwards you can access the export either via manual import or via URL (via Data Director's REST API).