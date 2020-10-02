---
description: >-
  This document provides an overview of GRCschema’s process for developing and
  changing GRC schemas.
---

# How we work

This document provides an overview of GRCschema’s process for developing and changing GRC schemas.

### Schema definitions

Each type can have one or more supertypes, although it is rare to have more than one supertype. This provides the main hierarchical navigational structure of GRCschema.org: a tree of types with each Thing at the root. A great example of this is shown below for the [ChildIDs](https://grcschema.org/ChildIDs) object:

![ChildID Tree](https://developer.unifiedcompliance.com/uploads/child_id_tree.png)

#### Schema states

There are four states to every object in the schema -

* **proposed** - a proposed change for any object is in the works. During this phase discussion about the object is in play. Discussions for each object can be found in the [Community Forum](https://theucf.info/schcom) maintained by the UCF team \(for now\).
* **voting** - the proposed object is now up for a vote. Each  object up for a vote will be documented in GRCschema.org’s [proposed vocabulary](https://docs.grcschema.org/proposed-vocabulary/) section. Each object up for a vote will have links for voting and seeing the status of the vote, as shown below:

![Voting](https://developer.unifiedcompliance.com/uploads/grcschema_vote.png)

* **accepted** - the proposed object is now accepted as a part of some release version.
* **withdrawn** objects will be removed, but the documentation surrounding them will be maintained in the docs site.

#### How is this related to other Authority Documents that have/use JSON schemas, such as

* NIST SP 800-70, 
* NIST’s Informative Reference Catalog, 
* NIST’s Open Security Controls Assessment Language \(OSCAL\), 
* TagVault.org’s Software Identification Tags \(SWID Tags\), 
* the Unified Compliance Framework, and 
* SIGLEX, a Special Interest Group on the Lexicon of the Association for Computational Linguistics?

GRCschema.org is a way of _converging_ these together into a workable schema with a productive API back end that facilitates adding and extracting content from a central repository - _irrespective_ of where the content came from. As schema objects get approved, they will be translated into API calls that are hosted on various API marketplaces. Anyone with a valid API key will be allowed to access the existing content.

### What skills do we need to participate?

English - its in English, and no it won’t be translated any time soon. If the explanations of an object aren’t clear, there’s a way for you to post a comment in the community. If a grouping isn’t clear - the same thing. If you want to suggest changes to a _proposed_ object, you can do so in the voting process we have. If you want to copy the JSON-LD, its there for you. If you want to see it visualized, that’s there too for you to explore as you see fit.

### What license do we need to apply this?

Admittedly, the Unified Compliance team have several patents that read on this \(see their patent page [here](https://www.unifiedcompliance.com/patents/). If you are consuming or adding to the data via the forthcoming API, a Patent License Agreement and any payment for it is built in. If you so choose to _not_ use the API and to build out the full data model shown [here](https://d1qmdf3vop2l07.cloudfront.net/dear-squash.cloudvent.net/compressed/_min_/ba5997edb6e3bd24885652f35022ab00.png) on your own, you’ll need to sign the forthcoming Patent License Agreement. Because the full data model isn’t published yet, nothing is necessary at this time.

