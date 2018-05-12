# Banana

The Banana project was forked from [Kibana](https://github.com/elastic/kibana), and works with all kinds of time series
(and non-time series) data stored in [Apache Solr](https://lucene.apache.org/solr/). It uses Kibana's powerful dashboard
configuration capabilities, ports key panels to work with Solr, and provides significant additional capabilities,
including new panels that leverage [D3.js](http://d3js.org).

The goal is to create a rich and flexible UI, enabling users to rapidly develop end-to-end applications that leverage
the power of Apache Solr. Data can be ingested into Solr through a variety of ways, including
[Logstash](https://www.elastic.co/products/logstash), [Flume](https://flume.apache.org) and other connectors.

## Resources

* [Banana Wiki Tutorials](https://github.com/lucidworks/banana/wiki/Tutorials)

## Installation

Download banana from [Banana Github](https://github.com/lucidworks/banana) (use the Download or Clone button, then select Download ZIP). 
Extract the zip package into the `$SOLR_HOME\server\solr-webapp\webapp\banana` directory.

Start Solr. You can access Banana at http://localhost:8983/solr/banana/src/index.html#/dashboard .
