# DERA-ingest-pipeline

EDGAR Taxonomy information is here: <https://www.sec.gov/info/edgar/edgartaxonomies.shtml>

SEC company Search is here: <https://www.sec.gov/edgar/searchedgar/companysearch.html>

We presently load the "compact" numerical datasets from this location: <https://www.sec.gov/dera/data/financial-statement-data-sets.html>

The "complete" datasets are located here: <https://www.sec.gov/dera/data/financial-statement-and-notes-data-set.html>

The SEC comments back to filers via this public channel: <https://www.sec.gov/structureddata/osdstaffobsandguide>

Ex21 subsidiary information developed by CorpWatch (<http://api.corpwatch.org/documentation/faq.html>) made useable by CrocTail: <http://croctail.corpwatch.org/#cw_825,cw_825,2020>

This is an example of a commercial interface to SEC data: <https://pypi.org/project/sec-api/>
There are many others.

The ingestion pipeline supports an "incremental" (monkey-patch) option. This is useful for onboarding quarterly dumps of SEC data one by one. Alas, the way the `tag` files are constructed, incremental loading creates data inconsistencies in the tag data checks.

There's a comprehensive schema defined in "dbt/dera_transform/dera_base_schema.yml" that we don't want to overwrite. We copy that to "dbt/dera_transform/models/dera_schema.yml", which gets blown away every time we dump out the models directory.

There is presently confusion as to how `dbt deps` is supposed to populate dbt-labs/dbt-utils and friends.
