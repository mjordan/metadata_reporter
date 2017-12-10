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

Run `./reporter test.ini`, where 'test.ini' specifies whether or not to save the records to disk, an output directory, an OAI-PMH entpoint, a setSpec, and a list of reports:

```
[general]
save_records = false
output_dir = records

[oai]
endpoint = http://digital.lib.sfu.ca/oai2
set_spec = hiv_collection

[reports]
reports[] = element_count
```

Currently, only the 'element_count' report is available. The script will output something like the following:

```
Fetching records from http://digital.lib.sfu.ca/oai2...
Fetched 73 records from http://digital.lib.sfu.ca/oai2.

Element	Number occurances in all records
========================================
dc:title	73
dc:description	73
dc:date	73
dc:type	146
dc:identifier	292
dc:rights	73
```

## To do

* Add 'unique_values' report.

## License

![This work is in the Public Domain](http://i.creativecommons.org/p/mark/1.0/88x31.png)

To the extent possible under law, Mark Jordan has waived all copyright and related or neighboring rights to this work. This work is published from Canada. 

## Contributing

If you have any questions or suggestions, open an issue.
