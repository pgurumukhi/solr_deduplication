# solr_deduplication
technical details about implementing solr dedupe strategy in solr single node 6.4

## Goal
* Goal is to set a Unique Field that is a combination of 2 fields member_id (type=string), member_joindate (type=date). This is other than the Solr generated Id field.

## Defining Unique field in Schema
* Define unique field in managed-schema
<field name="signatureField" type="string" multiValued="false" required="true" indexed="true" stored="true"/>


## Define processors to manage data in solrconfig.xml
* Add updateRequestProcessorChain
* Add processor SignatureUpdateProcessorFactory to update signatureField
* Define the fields that will form the signatureField
* Set the updateRequestProcessorChain in request handler /update