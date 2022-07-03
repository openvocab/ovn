# Units of Measure

Valueflows uses the units of measure from [OM2](https://github.com/HajoRijgersberg/OM).  This page adds specific information to OM2 in the Other Namespaces page in this section.  As of now, a file of units has been extracted to make it easier for user groups to choose their set of standard units.  Using agreed upon standard units will facilitate network interoperability into the future.

The complete rdf reference for OM2 can be found [here](https://raw.githubusercontent.com/HajoRijgersberg/OM/master/om-2.0.rdf).

A csv file derived from that can be found [here](https://lab.allmende.io/valueflows/valueflows/-/tree/master/units/unit-en-useful.csv).  This file includes units from OM2 as of 2022/06. It includes only the English version for now.  The currencies have been removed, since we recommend these be set up as Resource Specifications instead.  We have added classifications (partial) to facilitate search for needed units. See [this directory](https://lab.allmende.io/valueflows/valueflows/-/tree/master/units/) for other potentially useful artifacts. The columns in this file are, left to right:

* OM2 owl Class.  When a Unit belonged to multiple classes, those were consolidated to one row, under "Unit".
* Identifier in OM2.  These can be prefixed with "" for direct access.
* Label for the unit, to be used in Valueflows.
* Symbol for the unit, to be used in Valueflows.
* Description.
* Classification(s), added by us (not from OM), to facilitate search in the csv file, or ifn an application (if one is created) for groups to choose their units.  This column is incomplete, possibly not the best granularity, and in some places possibly wrong.  Updates are welcome!
