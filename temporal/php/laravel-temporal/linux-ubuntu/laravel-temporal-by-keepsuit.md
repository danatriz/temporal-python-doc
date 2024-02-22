# Laravel Temporal by Keepsuit

### Instalasi dependensi Laravel Temporal by Keepsuit

Instalasi dependensi menggunakan composer

* `composer require keepsuit/laravel-temporal`

### Install untuk menjalankan roadrunner versi terbaru

* `php artisan temporal:install`

### Mempublikasi file konfigurasi:

* `php artisan vendor:publish --tag="temporal-config"`

### Konfugurasi yang dipublikasikan `config/temporal.php`:

```php
<?php

return [
    /**
     * Temporal server address
     */
    'address' => env('TEMPORAL_ADDRESS', 'localhost:7233'),

    /**
     * Temporal namespace
     */
    'namespace' => env('TEMPORAL_NAMESPACE', \Temporal\Client\ClientOptions::DEFAULT_NAMESPACE),

    /**
     * Default task queue
     */
    'queue' => \Temporal\WorkerFactory::DEFAULT_TASK_QUEUE,

    /**
     * Default retry policy
     */
    'retry' => [

        /**
         * Default retry policy for workflows
         */
        'workflow' => [
            /**
             * Initial retry interval (in seconds)
             * Default: 1
             */
            'initial_interval' => null,

            /**
             * Retry interval increment
             * Default: 2.0
             */
            'backoff_coefficient' => null,

            /**
             * Maximum interval before fail
             * Default: 100 x initial_interval
             */
            'maximum_interval' => null,

            /**
             * Maximum attempts
             * Default: unlimited
             */
            'maximum_attempts' => null,
        ],

        /**
         * Default retry policy for activities
         */
        'activity' => [
            /**
             * Initial retry interval (in seconds)
             * Default: 1
             */
            'initial_interval' => null,

            /**
             * Retry interval increment
             * Default: 2.0
             */
            'backoff_coefficient' => null,

            /**
             * Maximum interval before fail
             * Default: 100 x initial_interval
             */
            'maximum_interval' => null,

            /**
             * Maximum attempts
             * Default: unlimited
             */
            'maximum_attempts' => null,
        ],
    ],
    
    /**
     * Interceptors (middlewares) registered in the worker
     */
    'interceptors' => [
    ],

    /**
     * Manual register workflows
     */
    'workflows' => [
    ],

    /**
     * Manual register activities
     */
    'activities' => [
    ],

    /**
     * Directories to watch when server is started with `--watch` flag
     */
    'watch' => [
        'app',
        'config',
    ],

    /**
     * Integrations options
     */
    'integrations' => [

        /**
         * Eloquent models serialization/deserialization options
         */
        'eloquent' => [
            /**
             * Default attribute key case conversion when serialize a model before sending to temporal.
             * Supported values: 'snake', 'camel', null.
             */
            'serialize_attribute_case' => null,

            /**
             * Default attribute key case conversion when deserializing payload received from temporal.
             * Supported values: 'snake', 'camel', null.
             */
            'deserialize_attribute_case' => null,

            /**
             * If true adds a `__exists` attribute to the serialized model
             * which indicate that the model is saved to database and it is used on deserialization when creating the model.
             * If false (or `__exists` is not present) the model will be created as existing model if primary key is present.
             */
            'include_exists_field' => false,
        ],
    ],
];
```

### Membuat Activity

Jalankan perintah berikut:

```
php artisan make:activity {name}
```

contoh:&#x20;

```
php artisan make:activity TemporalActivity
```

source code:

```
```

### Membuat Workflow

Jalankan perintah berikut:

```
php artisan make:workflow {name}
```

contoh:

```
php artisan make:workflow TemporalWorkflow
```

source code:

```
```

