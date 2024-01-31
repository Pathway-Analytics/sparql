# Recipies

Using this endpoint https://statistics.data.gov.uk/sparql-beta

## Find an LSOA and Its Parents

SELECT ?link ?code ?name ?status ?within
 WHERE { 
  
   VALUES ?item {'E01034155'}
     VALUES ?entityCode { <http://statistics.data.gov.uk/id/statistical-entity/E01> }
     ?link <http://statistics.data.gov.uk/def/statistical-entity#code> ?entityCode ;
          <http://www.w3.org/2004/02/skos/core#notation> ?item .
     ?link <http://publishmydata.com/def/ontology/foi/displayName>  ?name .
     ?link <http://statistics.data.gov.uk/def/statistical-geography#status> ?status .
     ?link <http://publishmydata.com/def/ontology/foi/within> ?withinLink .
   ?withinLink <http://www.w3.org/2004/02/skos/core#notation> ?within

     FILTER (?status = "live")
 }

## Find the Children Of...
 
SELECT ?link ?code ?name ?status ?within
 WHERE { 
  
   VALUES ?within {'E07000213'}
     VALUES ?entityCode { <http://statistics.data.gov.uk/id/statistical-entity/E01> }
     ?link <http://statistics.data.gov.uk/def/statistical-entity#code> ?entityCode ;
          <http://www.w3.org/2004/02/skos/core#notation> ?item .
     ?link <http://publishmydata.com/def/ontology/foi/displayName>  ?name .
     ?link <http://statistics.data.gov.uk/def/statistical-geography#status> ?status .
     ?link <http://publishmydata.com/def/ontology/foi/within> ?withinLink .
   ?withinLink <http://www.w3.org/2004/02/skos/core#notation> ?within

     FILTER (?status = "live")
 }
