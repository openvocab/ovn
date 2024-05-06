# External namespaces and terms

Most applications using VF will need terms defined in various other vocabularies.  In fact, we consider these to be essential to a complete value flows core vocabulary.  Below are the elements we are re-using from well established vocabularies (web ontologies).


## OM2

[http://www.ontology-of-units-of-measure.org/resource/om-2/](http://www.ontology-of-units-of-measure.org/resource/om-2/)

* [`om2:Measure`](http://www.ontology-of-units-of-measure.org/resource/om-2/Measure)
* [`om2:hasUnit`](http://www.ontology-of-units-of-measure.org/resource/om-2/hasUnit)
* [`om2:hasNumericalValue`](http://www.ontology-of-units-of-measure.org/resource/om-2/hasNumericalValue)


* [`om2:Unit`](http://www.ontology-of-units-of-measure.org/resource/om-2/Unit)
    * See the page also in this section called Units of Measure.
    * VF will use (at least) `rdfs:label` and `om2:symbol` as properties of Unit.


## TIME

[https://www.w3.org/TR/owl-time](https://www.w3.org/TR/owl-time)

Some useful constructs, others here: https://www.w3.org/TR/owl-time/#topology, see the Interval Relations.

* [`time:inXSDDateTimeStamp`](https://www.w3.org/TR/owl-time/#time:inXSDDateTimeStamp)
* [`time:hasDuration`](https://www.w3.org/TR/owl-time/#time:hasDuration)
* [`time:before`](https://www.w3.org/TR/owl-time/#time:before)
* [`time:after`](https://www.w3.org/TR/owl-time/#time:after)
* [`time:intervalDuring`](https://www.w3.org/TR/owl-time/#time:intervalDuring)

`vf` defines property chain axioms for `vf:hasBeginning` , `vf:hasEnd`, and `vf:hasPointInTime` as slight variant
of [Alignment of PROV-O with OWL-Time](https://www.w3.org/TR/owl-time/#time-prov).

## GEO

[https://www.w3.org/2003/01/geo/wgs84_pos#](https://www.w3.org/2003/01/geo/wgs84_pos#)

* [`geo:lat`](https://www.w3.org/2003/01/geo/wgs84_pos#lat)
* [`geo:long`](https://www.w3.org/2003/01/geo/wgs84_pos#long)
* [`geo:alt`](https://www.w3.org/2003/01/geo/wgs84_pos#alt)


