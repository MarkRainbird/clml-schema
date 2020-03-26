
# Legislation Schema
The schemas provided are intended to describe UK Legislation.
Crown copyright 2018

## Release Notes
### Version 2.1
Release date: TBD
Features and Fixes (TBC):

* New schema version numbering scheme introduced (see below)

* New schema release documentation (this file)

* Issue 171209490 - new attribute values supported for EU Minor document classification in BlockAmendment (with refactoring and re-use of MinorType)

* Issue 171488633 - the legislation.xsd schema can now be used for validation with MSXML4 or .Net validators (changes to atom.xsd and xml.xsd)

* Issue 161958070 - changed the model for the attributes on ukm:Correction to have stricter validation rules

* Issue 171599021 - removed default values for FragmentAttributes and ContentsAttributes

* Issue 171654037 - Effect ukm:InForce Qualification attribute now validates against a set of approved string values (including empty string for historical reasons)

* Issue 171841757 - changes for ASC project (changed DocumentMainTypeBasic to add "WelshParliamentAct" and added "WelshParliament" to Laid values) as a result of http://www.legislation.gov.uk/anaw/2020/1/enacted#section-3

* Issue 171578804 - renamed TSOMetadata to LegislationMetadata

* TBD

## Top-level schemas

The following schema (from the "schema" folder") are "top-level" schema that should be used to validate various types of legislative documents.

* legislation.xsd - used to validate primary and secondary UK legislation data sets including those available from legislation.gov.uk and from the bulk downloads site http://leggovuk.s3-website-eu-west-1.amazonaws.com

* en.xsd - used to validate explanatory notes and explanatory memoranda.

* impactAssessment.xsd - used to validate UK Impact Assessments.

* fragment.xsd - used to validate subsets of primary and secondary UK legislation data files during the editing process.

## Schema versioning and documentation of change

If a change is made to the schema that breaks old data or significantly changes the meaning of existing semantics then the schema versions will change in such a way that old data can point to old schema and new data to new schema. This is to be avoided if at all possible (as has been the case with legislation). The change would be reflected by a change to the namespace (by adding a version). This would invalidate all old data and require updates to all systems/scripts and schema modules. This is to be avoided unless entirely necessary!

As with most software releases, the major version will change when there is a significant re-issue of a whole schema with new features and/or re-modelling. Small improvements and or bug fixes are shown with a minor version number. e.g. "2.3" has major version of "2" and minor of "3" and The next minor version would be "2.4" and the next major version would be "3.0".

The schema version number will be recorded in the version attribute on the schema. We will only update a schema modules' version number when they themselves change for a minor update - this makes it easier for developers to know what modules have changed. We will also increment the version number of the top-level schemas (see above) even if they did not change as their content may have changed as a result of a change to the included schema modules and it will help developers know what version of the schema they are dealing with. We will of-course also update the top-level schemas version if they themselves change. When we issue a major release (version 3.0 is next) we update all TSO schema module versions to match the major number.
All of these chnages will also trigger a change to the schema's dcq:modified date element in the Dublin Core Metadata.

The schema developer will document each change (made for a bug fix or new feature) at the top of the schema file with a version number BUT if a number of schema changes are being made over a period of a few weeks for a given RELEASE of the schema then it is likely that a number of changes within a single schema file will have the same version number (as they are part of the same release). The change log in BitBucket will supply those with access to a more granular "what individual change happened on what date WITHIN a given release" and so no there is no requirement to add additional point point release numbers.

Schema developers should always include a file level xsd:documentation history comment which matches the change to a specific version. This provides context for changes for those who cannot access the Bitbucket repository.

Any development that effects a change in the currently released data model or its meaning should be documented using xs:documentation at element/type level.
This change will then be refelected in both dynamically generated documentation but also must be changed by the developer in any static information that supplements it (in the new documentation set to be developed soon).
When a release is made, the new version of the documentation will be generated and released.

Any code level (as opposed to file level) developer comment that describes a change that does not affect the data model should be recorded using an XML comment <!-- --> and should link the change to the appropriate Pivotal issue. 

Any change will be agreed in advance of release with TNA Schema Change Board.

Any change to the schema will be applied to the unified-schema in bitbucket https://bitbucket.org/tsoltd/unified-master-schema/src/master/

Schemas versions will be released formally and distributed automatically to all systems. 
