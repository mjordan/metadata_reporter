# Metadata Reporter

## System requirements and installation

To install and run this script, you will need:

* PHP 5.5.0 or higher command-line interface
* [Composer](https://getcomposer.org)

To install the reporter:

* Clone the Git repo
* `cd metadata_reporter`
* `php composer.phar install` (or equivalent on your system, e.g., `./composer install`)

## Usage

Run `./reporter test.ini`, where 'test.ini' specifies an output directory, an OAI-PMH entpoint, and a setSpec.

```
[general]
output_dir = test

[oai]
endpoint = http://digital.lib.sfu.ca/oai2
set_spec = hiv_collection
```
## License

![This work is in the Public Domain](http://i.creativecommons.org/p/mark/1.0/88x31.png)

To the extent possible under law, Mark Jordan has waived all copyright and related or neighboring rights to this work. This work is published from Canada. 

## Contributing

If you have any questions or suggestions, open an issue.
