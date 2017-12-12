# Metadata Reporter

Script to report on various aspects of metadata retrieved via OAI-PMH. Currently in early, proof-of-concept development.

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
# save_records defaults to true
save_records = false
# output_dir defaults to records

[oai]
endpoint = http://digital.lib.sfu.ca/oai2
# set_spec defaults to none
set_spec = hiv_collection
# metadata_prefix and namespace default to oai_dc and http://purl.org/dc/elements/1.1/

[reports]
reports[] = element_count
reports[] = unique_element_values
# Defaults to unique_element_values_output_file.txt
unique_element_values_output_file = element_values.txt
```

## The reports

Currently, only two reports are availalbe, 'element_count' and 'unique_element_values'.

### element_count

This report lists all the elements used in the aggregated metadata harvested from the OAI endpoint. Its purpose is to provide an overview of which elements are repeated, and which are absent from the metadata. The `reporter` script prints a brief list of element names along with the total number of instances of the element, like this:

```
Element	Number occurances in all records
========================================
dc:title	73
dc:description	73
dc:date	73
dc:type	146
dc:identifier	292
dc:rights	73
```

### unique_element_values

This report lists all of the elements used in the aggregated metadata harvested from the OAI endpoint, and for each element, a list a all the unique values used in that element. Its purpose is to provide an overview of how consistent the values are, or if there are any empty elements (signified with an empty string, `""`, in the list of values). If you configure the 'unique_element_values' report to run, its output will be in the file located in your .ini file's [reports][unique_element_values_output_file] setting. The file will contain a section for each metadata element used in the set of metadata records, accompanied by a list of unique values in that element. Sample output (showing only three Dublin Core elements for brevity) looks like this:

```
dc:date
========================
""
1988
1989
1990
1991
1992
1993
1994
1995
1996
1997
1998
1999
2000


dc:type
========================
StillImage
postage stamps


dc:rights
========================
Reproduction of the material is subject to the approval of the Special Collections and Rare Books Librarian

```

Note that when applied to hierarchical XML formats like MODS, the 'unique_element_values' shows the text values for parent-level elements as well as for child elements. For example, for the MODS elements `<titleInfo>` and `<title>`, the report will have an entry for each, although the content of `<title>` will ve repeated in the content of `<titleInfo>` because `<title>` is a child of `<titleInfo>`.

## To do

* Test with OAI-PMH metadata formats other than oai_dc.
* Provide an option to include the XPath to the elements.
* Break our report generators into plugins.
* Allow reports to be formatted using Twig templates.

## License

![This work is in the Public Domain](http://i.creativecommons.org/p/mark/1.0/88x31.png)

To the extent possible under law, Mark Jordan has waived all copyright and related or neighboring rights to this work. This work is published from Canada. 

## Contributing

If you have any questions or suggestions, open an issue.
