# 4.0.0
## 3/1/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 3/1/2025 | Collection<br>Dataset | dct:identifier | Change to 1:1 | There is only one dct:identifier for a Dataset or Collection<br><br>Issue -- if the identifier can be both a string and an HTTP URI, then we may want to keep this as 1:N to capture both<br>4/7/25 - email from Alvin that in at least Dataset this is being used 1:N so should not change | Do not change |

## 4/3/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 4/3/2025 | Grant | schema:url and/or 1:N cardinality for schema:identifier | Add or change or both? | See also row 47<br>We have a DATMM URI for each schema:Grant, but sometimes the grant/funding organization has its own URL or URI for the grant/fund and we're not capturing that. There are 2 options and both can be added -- <br>1) Schema:identifier will take strings or "URL (URI) links" (NJF takes this to mean a URI since a URL is a Web location which falls under schema:url, see below), so if we change the cardinality to 1:N then we can have both a number and/or a HTTP URI if one exists<br>2) schema:url is used for URLs (which is NOT a URI, see above) so we could use this when the identifier has a URL that we want to be able to provide a link for and we know is not a URI<br>5/29/25 - Agreed not to use schema:url for this (see below), but could follow #1 above to change cardinality to 1:N to accept an HTTP URI representing the grant | HOLD |

## 5/23/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 5/23/2025 | Agent | schema:memberOf<br>schema:affiliation<br>org:hasMembership<br>org:memberOf | Add agent affilitations | For use behind the scenes for improving MeSH - MeSH is greatly improved when have Agent affiliations; will need to allow multiple affiliations per Agent in case they change<br>Do we want to get into this level of detail?  Yes<br>There can be a lot of agents for each dataset - not foreseen as a problem<br>will need to allow multiple uses<br><br>org:memberOf <br>see https://www.w3.org/TR/vocab-org/#org:memberOf  where domain is foaf:Agent<br>Indicates that an agent (person or other organization) is a member of the Organization with no indication of the nature of that membership or the role played. Note that the choice of property name is not meant to limit the property to only formal membership arrangements, it is also intended to cover related concepts such as affiliation or other involvement in the organization. Extensions can specialize this relationship to indicate particular roles within the organization or more nuanced relationships to the organization. | Changed 6/23/25 |
| 5/23/2025 | Repository | dct:subject > skos:Concept | Add concepts for the repository itself | To know what each repository is mainly about so we can pull in a variety of repositories with different topical foci and determine what kind of repos we need to keep the topics evenly distributed <br>Do we want want this in DATMM or kept in a local file re the databases held, dismissed, under review, pending review?  How would this apply to databases we have not yet ingested?<br>optional field; not applicable for general repos, for domain specific repos | Changed 6/23/25 |

## 5/28/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 5/28/2025 | Grant | schema:url  | Add a URL to more info re the grant | See also row 44<br>To provide access to fuller Grant info than we currently have. Specifically for NIH Reporter (https://reporter.nih.gov/) where search results for NIH grant info include the grant name, id, exact grantor/funder (in addition to NIH), concepts, any PubvMed articles that cite the grant, etc.   <br>Alvin needs to meet with them to get a better idea of what they have and how we can use it<br>Might create a bridge for PubMed and Dataset Catalog<br>5/29/2025 - Agreed to use this to capture URL links to pertinent grant/funding information, e.g., NIH Reporter  | Changed 6/23/25 |

## 6/11/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 6/11/2025 | Dataset<br>Collection | schema:status<br>dct:accessRights<br>datmm:status<br>adms:status | Add a property to indicate that a dataset is active, inactive, or changed (i.e., new version - though this would be covered by dct:isVersionOf) | Stick with just active/inactive<br><br>schema:status : The status of a study<br>This fits in terms of definition and one expected value is text, so it can be used.  The only concern is that our use is with Dataset and Collection but it's used in schema.org with MedicalCondition, MedicalProcedure, and MedicalStudy - NO as it's scope of Classes doesn't work for us<br><br>dct:accessRights : Information about who access the resource or an indication of its security status. <br>Access Rights may include information regarding access or restrictions based on privacy, security, or other policies. - NO as it's not quite on point<br><br>Another option is to create datmm:status - NO would really not like to do this<br><br>See https://semiceu.github.io/ADMS/releases/2.00/ adms:status = The status of the Asset in the context of a particular workflow process.<br>$4 Conformance - In this vocabulary [ADMS] the rdfs:Resource class is used to denote any possible resource. Thus meaning no restriction in usage. | Changed 6/23/25 |

## 6/13/2025

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 6/13/2025 | Concept | dct:source | source of a subject | Not the scheme where it lives, but how it was generated, e.g., Dataset Catalog generated MeSH as<br>author supplied<br>repository supplied<br>keword derived<br>title/description derived<br>PubMed supplied | Changed 6/23/25 |

# 3.0.0

## 5/26/2022

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 5/26/2022 | Collection |  | Add Collection Class | Add a Collection Class. NLM Team will determine properties.<br><br>Some sites have related datasets as part of a Collection along with other materials.  We agreed to create a Collection Class and record each Dataset individually but related to the Collection.  Keep the Collection peroperties minimal but useful | changed |

## 12/9/2022

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 12/9/2022 | Concept | skos:inScheme | Repository supplied keywords often don't have an inScheme value. We either need to hardcode something for these or change the constraint to optional | Decided to keep it mandatory and use the source repository as the scheme name, e.g., "ImmPort_repository provided" | no change |
| 12/9/2022 | DataDownload | schema:encodingformat | Change Constraint to Optional | data not always available | changed |
| 12/9/2022 | Dataset | dct:language | Change Constraint to Optional | data not always available | changed |
| 12/9/2022 | Dataset | dct:rights<br>dct:accessRights<br>dct:license | Add dct:accessRights since statement in dct:rights is not also about access.  We have already split out dct:license from dct:rights (dct:license is a subproperty of dct:rights) | Keep dct:rights for both access and license info and change use to 1:N (can use property multiple times with different info each time) and delete dct:license. <br><br>Since both dct:accessRights and dct:license are subproperties of dct:rights, we will just use dct:rights for all rights data, Therefore we will also delete dct:license.  | changed |
| 12/9/2022 | Documentation | prism:doi | Remove from model | not needed; will use dct:identifier instead | changed |
| 12/9/2022 | Documentation | rdf:type | Change Constraint to Optional | data not always available | changed |
| 12/9/2022 | Documentation | dct:title | Change Constraint to Optional | data not always available; sometimes just a URL link is given | changed |
| 12/9/2022 | Funding | frapo:isFundedBy | Change Constraint to Optional | This was put forth with the assumption that we'd break apart funds and funding agents into different properties but we decided to hold off on that.  Per Alvin, we don’t yet have any datasets where either the funding agency or fund name are NOT available. | no change |
| 12/9/2022 | Funding | frapo:isFundedBy | ImmPort has grant numbers but no foaf:Agent. They have grant names instead of funder names. Should we create different classes for funding agent and fund name? frapo does have the option of a single property to cover both and separate properties for each. | Keep frapo:isFundedBy for both funding agency and funding/grant titles BUT remove its relationship with foaf:Agent.<br><br>Using both frapo:hasFundingAgency and frapo:isFundedBy serves no obvious advantage as the grant name (in isFundedBy) would not be searchable in foaf:name but the granting agency name would.  When there is only a grant name given (e.g., IMMPORT), that doesn't help and makes finding the data confusing. So, both will be searchable via frapo:isFundedBy and removed from foaf:name.<br>Down the road if we see a need to revise this by separating this date we can do so. | changed |
| 12/9/2022 | Funding | frapo:hasGrantNumber | Change Constraint to Optional | data not always available | changed |

## 1/19/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 1/19/2023 | Funding | frapo:hasFunderIdentifier | Add with optional constraint | Alvin asked if there is a way to include URIs for funders if we have them and this would work.  dct:identifier would not work as the Funding Class includes both funder/fund names and the fund ID, so what dct:identifier applies to would be questionable.   | changed |
| 1/19/2023 | Dataset | dct:rights | Add standard statement when no rights/access rights/license info is given for the dataset | Agreed this should be done; rather than leaving Access Rights blank in the user interface, add the statement 'No information provided; contact the repository owner' | changed |
| 1/19/2023 | DataDownload |  | Is this Class needed? | We are of mixed feelings about the utility of creating a download in the user interface with no explanation of what it will do/where it will send users - the sites themselves are inconsistent in how this is handled.  Currently, our UI may send the user to the general external dataset site for download info or it may just start downloading data to the users computer (which could be problematic in that the user doesn't know what or how much data is being downloaded). One suggestion was to remove this Class entirely and point the user to the originating site for downloading data<br>DECISION: get usability feedback from testing to decide how to move forward | REMOVED  - SEE ROW 17 |

## 1/23/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 1/23/2023 | Collection | dct:isVersionOf<br>dct:hasPart | Whether to use dct:isVersionOf or dct:hasPart to reference prior/other superseded collections | dbGaP is showing collections that are superseded by later collections, sometimes by a couple later collections and sometmes by alot of them. The earlier superseded collections are showing up in our data as a dataset that is part of a later collection, sometimes the current/active collection, but sometimes not.  - see dbGaP sample emailed by Pete 1/17/23<br><br>We can add dct:isVersionOf to Collection to link those earlier versions of collections to the later versions OR use dct:hasPart to show that a superseded collection is part of a newer collection, which may not be true and was not its intended use, i.e., dct:hasPart was intended for use with live/active Collections that are part of other Collections.  <br><br>Decision:  Add dct:isVersionOf to Collection; use in the latest/current version to relate it to the earliest/orginal version, i.e., the current/active collection is a version of the earliest collection | changed |

## 2/2/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 2/2/2023 | DataDownload | ALL | Remove from model | This is problematic as the data differs from site to site and not alwau=ys avaibale to a user without signing into a site; we do want the user to go the site to download, our purpose is simply to help the user find the dataset(s)<br><br>Decision: remove DataDownload from the model | changed |
| 2/2/2023 | Dataset | schema:distribution | Remove from model | Need to remove the link to DataDownload from Dataset | changed |

## 2/10/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 2/10/2023 | Funding<br>Contribution<br>Documentation | All Funding properties<br>bf:role (Contribution)<br>fabio:PubMedID (Documentation) |  | All of the SPAR ontologies we use appear to no longer be active RDF sources (URIs bring you to the top of the page) and need to be replaced.  For our model, this includes FRAPO (all funding), SCORO (used with Contribution/bf:role), and FABIO (Documentation/fabio:PubMedID)<br><br>Contact with the developers indicates that they are aware the SPAR ontologies are not ideal for human readability/understanding of the relation of a URI to a term in the real world and are looking into fixing that within the next 2 years.  Also, the developers indicated that OpenCitations uses the SPAR onotologies, but since it is their own site that is not much of a recommendation  | see individual issues below at rows 20-22 |

## 3/2/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 3/2/2023 | Contribution | bf:role | find new LD source for contribution roles | 1) Library of Congress has a LD list of creator roles at https://id.loc.gov/vocabulary/relators.html.  These are not as precise as the SCORO roles but might suffice. <br>2) There is also the Contributor Role Ontology: A classification of the diverse roles performed in the work leading to a published research output in the sciences. CRO is at https://www.ebi.ac.uk/ols/ontologies/cro  <br>3) Look at Wikidata as well, e.g., see https://www.wikidata.org/wiki/Q7245082 for principal investigator<br><br>Most of the SCORO roles have an exact match in Wikidata, except for 'Other' and 'Site Manager'<br><br>Decision: use Wikidata roles per spreadsheet and use 'other' from id.loc.gov Relators LD vocab for both 'Other' and 'Site Manager' roles and any other roles that cannot be easily defined<br><br>Down the road, may look into adding an 'Other' role that is more precise for our needs into the Wikidata vocab | THIS DECISION WAS SUPERCEDED - see below at row 23  for how to use bf:role<br> |
| 3/2/2023 | Funding | ALL | find new LD source for funding Class and properties | schema:Grant can be used with properties schema:identifier for the grant/fund id and schema:funder or schema:name for the funder name.  schema:funder would not include the grant, so schema.name might be a better choice.  NB - We had agreed previously not to add funders as Agents.<br><br>Will also need to change Dataset/frapo:isSupportedBy to Dataset/schema:funding<br><br>Decision: Agreed to use  <br>schema:Grant with schema:identifier for grant/fund id and schema:name for grant/funder name. Also, use Dataset/schema:funding as the lead in to schema:Grant | changed |
| 3/2/2023 | Documentation | fabio:hasPubMedId | find new property | When we closed out the prism:doi we agreed to use dct:identifier instead, so that's a reasonable solution for this as well and is already a property under Documentation.<br>Posiible problem:  PubMed does not include a source in its identifiers, i.e., it does NOT say PubMed12345, however, since the URL indicates the source as PubMed that may not be a problem<br><br>Decision: move all ids to dct:identifier and if we disover it is problematic that the PubMed ID is not identified as coming from PubMed then we'll look at this again | changed |

## 3/16/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 3/16/2023 | Contribution | bf:roles | determine what role terms to use | dbGaP has over 500 roles listed. Many are variations/extended versions of investigator and primary investigator, but it also includes funders, collaborators, researcher, and no real roles at all (e.g., institution or department names).  Our expectations is that this will not be a unique occurrence in dbase sites we ingest.  <br><br>Options in we discussed are to 1) cull out only certain roles and names, e.g., just primary investigators, or 2) show all names and all roles as conveyed in the site or 3) show all names and make the role 'Contributor' for all.<br> #1 is too prescriptive and we cannot determine what roles might be synonyms for primary investigator and  investigator. For #2 we would not necessarily have a LD term for each role and it would take alot of translation to figure out what role to apply from a LD ontology.  <br>We will use #3, and so will apply the 'Contributor' role to all names/institutions associated with a dataset. We will use the Wikidata URI for Contributor http://www.wikidata.org/entity/Q20204892<br>In some cases, that may mean including funders if they are not separated out from other roles related to the creation of a dataset.   | changed  |

## 4/27/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 4/27/2023 | Collection |  | Wrong prefix | dct:Collection should be dcmitype:Collection; dct and dcmitype are from different parts of the Dublin Core vocab  | changed |
| 4/27/2023 | Collection |  | Definition adjustment | From "An aggregation of resources (Use to indicate when a dataset is part of a collection or when one collection is part of another collection)"<br>To "An aggregation of resources" | changed |
| 4/27/2023 | Collection<br>Dataset | dct:description | Definition adjustment | From "An account of the resource; may include but is not limited to: an abstract, a table of contents, a graphical representation, or a free-text account of the resource."<br>To "An account of the resource." | changed |
| 4/27/2023 | Collection<br>Dataset | dct:issued | Definition adjustment | From "Date of formal issuance (e.g., publication) of the resource."<br>To "Date of formal issuance of the resource." | changed |
| 4/27/2023 | Collection<br>Dataset | dct:subject | Definition adjustment | From "The topic of the resource"<br>To "A topic of the resource." | changed |
| 4/27/2023 | Dataset | dct:alternative | Definition adjustment | From "An alternative name (title) for the resource."<br>To "An alternative name for the resource."<br><br>It is correct in Repository so no need to change there | changed |
| 4/27/2023 | Agent | foaf:name | Definition adjustment | From "The name of something as a simple textual string"<br>To "The foaf:name of something is a simple textual string." | changed |
| 4/27/2023 | Documentation | rdf:type | Definition adjustment | From "states that a resource is an Instance of a Class"<br>To "rdf:type is used to state that a resource is an instance of a class." | changed |
| 4/27/2023 | Grant | schema:identifier | Definition adjustment | From "The identifier property represents any kind of identifier for any kind of Thing"<br>To "The identifier property represents any kind of identifier for any kind of Thing, such as ISBNs, GTIN codes, UUIDs etc. " | changed |

## 4/27/2023<br>4/4/2024

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 4/27/2023<br>4/4/2024 | Concept | rdfs:label | Definition adjustment | From "used to provide a human-readable version of a resource's name"<br>To "rdfs:label may be used to provide a human-readable version of a resource's name."<br>4/4/24 This defintion is from the text; the formal definition is at sec 6.2 https://www.w3.org/TR/2014/REC-rdf-schema-20140225/#ch_sumproperties and is changed to match that | changed |
| 4/27/2023<br>4/4/2024 | Documentation | rdf:type | Definition adjustment | From "states that a resource is an Instance of a Class"<br>To "rdf:type is used to state that a resource is an instance of a class."<br>4/4/2024 - This definition is part of the textual explanation; the formal definition is at section 6.2 https://www.w3.org/TR/2014/REC-rdf-schema-20140225/#ch_sumproperties so definition is changed  | changed |

## 7/12/2023

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 7/12/2023 | Grant | schema:name | change to Optional | A recently reviewed data source listed names of grants and grant numbers/identifiers separately in its metadata, with more grant ids than names.  The grant names were not useful in re finding info about the grants and the grant ids included grants that were not named.  Overall the grant names were not helpful and were incomplete.  So we decided to use only the grant identifiers.<br><br>Result is to chante Grant/schema:name from Reqiured to Optional | changed  |

## 9/4/2024

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 9/4/2024 | Dataset | dct:accrualPeriodicity<br>dct:conformsTo<br>pav:createdWith<br>dct:format<br>dct:temporal | Delete | These properties are niot used as we're not recording download info<br>dct:format - This info is not generally available to download and even if it is, we decided that it's info the user can get from the homesite and is a detail about the dataset that we don’t need to provide<br>dct:temporal - This is data about the dates covered by the dataset itself that users can get from the homesite information; it's not generally provided in the metadata although Datacitte does sometimes have it | Changed 12/18/24 |
| 9/4/2024 | Dataset<br>Collection | dct:isVersionOf | Keep but monitor use | This is not currently used for any repository but down the road it could be pertinent for others entering datasets.  <br>Keep this for now and revisit down the road | no change; REVIEW AGAIN AT A LATER DATE |
| 9/4/2024 | Collection | dct:identifier<br>dct:isPartOf | change to Required | All collections have identifiers and all collections are part of a repository | changed 12/18/24 |
| 9/4/2024 | Collection | dct:hasPart | change to Optional | A collection is not necessarily related to another collection, which this property is meant to state | changed 12/18/24 |
| 9/4/2024 | Contribition | bf:role | change to Required | All entities have sone role; If the role is unknown we currently lump the entity in as role=contributor (which are using for all other roles as there are too many to define).<br>We are adding role=funder from Wikidata for those that are associated with grants/funding in the metadata and were requested to this by repositories | changed 12/18/24 |

## 11/1/2024

| Date | Class | Property | Suggested Change | Decision/Notes | Status |
|---|---|---|---|---|---|
| 11/1/2024 | Grant | schema:funder | Add property for funder and link to contribution | Currently we are putting boith funder and funding in Grant/schema:name, but some repositories have asked about clearly identifying funders wihen they have a URI.  We agreed to link Grant to Contribution as schema:Grant > schema:funder > bf:Contribution > bf:role = ‘funder’ and bf:agent > foaf:Agent > foaf:name and dct:identifier | changed 12/18/24 |
| 11/1/2024 | Contribution | bf:role | Add URI for 'funder' | Per the agreement to include Grant funder as a Contribution role, add the Wikipedia URI for that role http://www.wikidata.org/entity/Q106905641 | Changed 12/18/24 |
| 11/1/2024 | Grant | schema:name | Change to 1:1 | Since this is now only used for the name of the Grant, change the cardinality from 1:N to 1:1; Grant can be repeated if there are multiple Grants associated with a Dataset or Collection | Changed 12/18/24 |
