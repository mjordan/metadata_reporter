# Metadata Reporter

Script to report on various aspects of metadata retrieved via OAI-PMH. Currently in inital development.

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

The script will output something like the following:

```
Fetching records from http://digital.lib.sfu.ca/oai2...
array(6) {
  ["dc:title"]=>
  string(23) "CAMPAÑA CONTRA EL SIDA"
  ["dc:description"]=>
  string(11) "65 centavos"
  ["dc:date"]=>
  string(4) "2000"
  ["dc:type"]=>
  string(10) "StillImage"
  ["dc:identifier"]=>
  string(55) "http://content.lib.sfu.ca/cdm/ref/collection/hiv/id/167"
  ["dc:rights"]=>
  string(107) "Reproduction of the material is subject to the approval of the Special Collections and Rare Books Librarian"
}
array(6) {
  ["dc:title"]=>
  string(23) "NACP: COMBATING DISEASE"
  ["dc:description"]=>
  string(6) "$12.00"
  ["dc:date"]=>
  string(4) "2000"
  ["dc:type"]=>
  string(10) "StillImage"
  ["dc:identifier"]=>
  string(55) "http://content.lib.sfu.ca/cdm/ref/collection/hiv/id/217"
  ["dc:rights"]=>
  string(107) "Reproduction of the material is subject to the approval of the Special Collections and Rare Books Librarian"
}

[...]

Fetched 73 records from http://digital.lib.sfu.ca/oai2.
```

## License

![This work is in the Public Domain](http://i.creativecommons.org/p/mark/1.0/88x31.png)

To the extent possible under law, Mark Jordan has waived all copyright and related or neighboring rights to this work. This work is published from Canada. 

## Contributing

If you have any questions or suggestions, open an issue.
