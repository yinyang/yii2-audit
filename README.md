# yii2-audit


Yet another auditing module.
This is based on a couple of other projects out there:

 * [Sammaye Yii2 Audit Trail](https://github.com/Sammaye/yii2-audittrail)
 * [Cordernote Audit Module](https://github.com/cornernote/yii-audit-module)

## Features
Installs as a simple module so it can be added without too much hassle.

Once added, this module tracks all incoming pageviews witht he ability to add custom data to a view.

It logs the user-id (if any), IP, superglobals ($_GET/$_POST/$_SERVER/$_FILES/$_COOKIES), memory usage, referrer and origin.

## Installing

* Add a `require` line to your `composer.json`: `'bedezign/yii2-audit: "*"`
* Run the migrations from the `migrations` folder.
* Add a module to your configuration (with optional extra settings) and if it needs to auto trigger, also add it to the bootrap.

Example:

    'bootstrap' => ['log', 'auditing', ...],
    'controllerNamespace' => 'frontend\controllers',

    'modules' => [
        'auditing' => [
            'class'             => 'bedezign\yii2\audit\Auditing',
            'ignoreActions'     => 'debug/*',
        ],
    ],

This installs the module with auto loading, instructing it to not log anything debug related.

### Error Logging

If you also want errors to be logged, you have to register the included errorhandler as well in you configuration:

    'errorHandler' => [
       'class'       => '\bedezign\yii2\audit\components\web\ErrorHandler',
       'errorAction' => 'site/error',
    ],

## Usage

You can then access the auditing module through the following URL:

http://localhost/path/to/index.php?r=auditing/request/index

### Screenshots

![Index example](docs/screenshots/audit-index.png?raw=true)
![View example](docs/screenshots/audit-view.png?raw=true)