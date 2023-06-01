# ONS Administrative Areas SPARQL Queries

This repo contains SPARQL queries in the main they are connected with UK ONS Administrative Areas.

For those accessing http://statistics.data.gov.uk for administrative area data for the first time the process can be complex.

## LSOA - An Explanation
LSOA stands for Lower Super Output Area, they are part of a hierarchy of a national administrative area naming schema managed by the ONS and part of a wider scheme know as International Territorial Level (ITL) known as Nomenclature of Territorial Units for Statistics (NUTS) prior to 2021.  These areas are used to report statistics about the population and land so it is important they are comprehensive (cover everyone), mutually exclusive (don't overlap or duplicate coverage) and consistently representative (each layer represents a consistent level of granularity) and offer a continuity of coverage over time so that useful comparisons can be made.
### Hierarchy
Each geographic entity in the hierarchy has a nine character code, the leftmost character is a letter; E, W, S, N indicating England, Wales, Scotland or Northern Ireland. The next two characters are numbers indicating the entity type:

Lower Super Output Area (LSOA): E01, W01, S01
Unitary Authority (UA): E06, W06, S12
Non-Metropolitan District (NMD): E07
Metropolitan Borough (MB): E08
London Borough (LB): E09
County (CTY): E10
Metropolitan County (MC): E11
English Region (RGN): E12
Inner and Outer London (IOL): E13

The remaining six characters are digits identifying the entity eg E01013995: Herefordshire 017D
### LSOAs
So, focusing on LSOAs.  LSOAs are supposed to represent a local population of a certain size of around 1000 to 3000 persons.  There are 33,755 LSOAs in England and 1,917 in Wales.  LSOAs are co-terminus within their administration area hierarchy, that is, their boundaries fall within the parent area - they do not overlap and a number of LSOA will cover the entire area (more precisely the population) of the parent.  In this respect, they are unlike postcodes.  Postcodes may overlap the boundary of an LSOA or any other administrative area.  Postcode lookups use the centre of the population density to determine in which administrative area the postcode is located.

LSOAs are reviewed after each census, the 2021 census results fed through to new LSOAs being released within two years of the census.

LSOAs can be retired or terminated and new ones introduced as populations move.

Many organisations publish LSOA data; their data may come from other third party organisations or direct from the ONS.  The ONS offers csv data files for download as well as an API endpoint that can be used in machine to machine data transfer using the SPQARL query language .  Data consistency between data suppliers can be an issue, even different data sources managed by the ONS offer different versions where LSOA may be available in one and not another.  Other government departments also replicate the delivery of LSOA data, such as the Department for Levelling Up, Housing and Communities that replicate the ONS and administrative geographical data, closely based on the ONS geographies, but currently out of date.

When reviewing the LSOA data entities, there is no identifier that determines if an LSOA entity is derived from 2001, 2011 or 2021 census (known as  LSOA01, LSOA11, LSOA21), the collection of live LSOA codes covering England and Wales is made up of current live LSOA that may have originated from the 2001, 2011 or 2021 census, some LSOA01 and LSOA11 codes were used in the 2021 census and some were terminated and replaced.

### Entity Status 
LOSA21 codes all have a status of 'live' rather than 'terminated'

LSOA prior to 2021 rely on OperativeDate and TerminatedDate

However, some codes such as E01000147 were introduced as a result of the 2001 census but have since had some property changes, leading to the OperativeDate being updated.  If the geometrical boundary changes, then a new code is always issued, but occasionally other non-essential properties are changed without replacing the code.

When an LSOA entity is recorded as Terminated with TerminatedDate or status of 'terminated', there is no consistent method in the data to indicate the new LSOA entity or entities that have adopted the old entiies population.  One terminated LSOA may be superceded by a number of new LSOA. Without inspecting the data (ie looking at the location the of the items covered by the old LSOA) it is not always possible to determine which new LSOA should be adopted in its place - it might be one of a number.

So, to determine if an LSOA is live we need to know that the highest-number code of LSOA used before the 2021 census was E01033768 all subsequent codes will have a status of 'live' or 'terminated' all prior codes will not have a TerminatedDate.

- 

Thanks for contributions from : Bill Roberts, [swirl.com](https://swirl.com)