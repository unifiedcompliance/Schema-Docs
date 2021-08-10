# Common Uses of Federated Mapping

## Common Uses of Federated Mapping for Compliance Database and Data Structures

A Federated Compliance Mapping methodology, as well as the Unified Compliance data structures, are used in a wide variety of situations and scenarios. The following commercial applications from the Unified Compliance team use these databases and data structures:

Common Controls Hub \(CCH\) – an online repository of all active mapped Authority Documents in the Unified Compliance Framework. CCH users can add members of their team to groups and initiatives, and then created lists of Authority Documents to share with those groups and initiatives. They can also use the CCH to compare one Authority Document to the other, or groups of Authority Documents against groups of Authority Documents. Users can also create gap analyses of Authority Document implementation. Authority Document lists are the primary means of sharing regulatory compliance content with over 90% of the GRC market.

* **Compliance Dictionary** – the world’s largest dictionary of compliance related terms.
* **Research @ Unified Compliance** – a comprehensive research site allowing users to research compliance terms, Citations and Mandates from Authority Documents, Common Controls, Assets and their Configuration Information, the types of records that must be maintained for compliance, etc.
* **UCF Mapper** – a compliance mapping tool used by many of the Fortune 500 that allows users to map internal compliance documents against the Common Controls in their selected lists of Authority Documents.
* **STIGViewer** – a comprehensive list of Secure Technical Implementation Guides maintained by the Unified Compliance team.

## The interpretations of Compliance as Code

As you might guess, in any burgeoning field, there are going to be almost as many interpretations of Compliance as Code as there are practitioners. Here are the main players within the Compliance as Code universe _as of this writing_. We’ve listed who they are, their significance, and where you can find their schema.

### Akoma Ntoso

Akoma Ntoso \(“linked hearts” in the Akan language of West Africa\), an initiative of “Africa i-Parliament Action Plan“[\[1\]](), and a program of UN/DESA[\[2\]](), defines a set of electronic representations in XML format of parliamentary, legislative and judiciary documents[\[3\]](). In 2018 it became an Oasis standard[\[4\]](), and has spun off Oasis’ LegalDocML \(see reference under LegalXML\).

[https://theucf.info/schemas-AkomaNtoso](https://theucf.info/schemas-AkomaNtoso)

### Common Platform Enumeration \(CPE\)

CPE is a structured naming scheme for information technology systems, software, and packages. Based upon the generic syntax for Uniform Resource Identifiers \(URI\), CPE includes a formal name format, a method for checking names against a system, and a description format for binding text and tests to a name[\[5\]]().

[https://theucf.info/schemas-CPE](https://theucf.info/schemas-CPE)

### Common Vulnerability Enumeration \(CVE\)

CVE® is a list of records—each containing an identification number, a description, and at least one public reference—for publicly known cybersecurity vulnerabilities. CVE Records are used in numerous cybersecurity products and services from around the world, including the U.S. National Vulnerability Database \(NVD\)[\[6\]]().

[https://theucf.info/schemas-CVE](https://theucf.info/schemas-CVE)

### Citation Style Language \(CSL\)

Citation Style Language's goal is to facilitate scholarly publishing by automating the formatting of citations and bibliographies[\[7\]]().

[https://theucf.info/schemas-CSL](https://theucf.info/schemas-CSL)

### Control Correlation Identifier \(CCI\)

The US Department of Defense Control Correlation Identifier \(CCI\) provides a standard identifier and description for each of the singular, actionable statements that comprise an IA control or IA best practice[\[8\]](). CCI bridges the gap between high-level policy expressions and low-level technical implementations. CCI allows a security requirement that is expressed in a high-level policy framework to be decomposed and explicitly associated with the low-level security setting\(s\) that must be assessed to determine compliance with the objectives of that specific security control. This ability to trace security requirements from their origin \(e.g., regulations, IA frameworks\) to their low-level implementation allows organizations to readily demonstrate compliance to multiple IA compliance frameworks. CCI also provides a means to objectively rollup and compare related compliance assessment results across disparate technologies.

[https://theucf.info/schemas-CCI](https://theucf.info/schemas-CCI)

### Credential Transparency Description Langauge \(CTDL\)

The CTDL family of specifications is intended to describe "things" such as a Credential, Organization, Assessment, Learning Opportunity, Competency, and so on. The CTDL is designed to enable:

1. Creation of simple descriptions and to serve as a basis for website markup; and
2. Rich descriptions to support fairly refined comparisons among credentials.

[https://theucf.info/schemas-CDTL](https://theucf.info/schemas-CDTL)

### Derived Relationship Mapping \(DRM\)

The NIST Derived Relationship Mapping \(DRM\) is a Software as a Service, JSON structure, and methodology for mapping various Authority Documents \(they call them reference documents\) to NIST’s reference framework \(they call it the Focal Document\). The Analysis Tool provides users the ability to generate DRMs for Reference Documents with the Cybersecurity Framework as the Focal Document. The DRMs are non-authoritative and represent a starting point when attempting to compare Reference Documents[\[9\]](). Sections 3.3 – 3.5 of NIST Interagency Report \(IR\) 8278, National Cybersecurity OLIR Program: Guidelines for OLIR Users and Developers for additional guidance around understanding and utilizing Derived Relationship Maps[\[10\]]().

[https://theucf.info/schemas-DRM](https://theucf.info/schemas-DRM)

### Dictionary Society joint JSON structure

In late 2020, GRCSchema proposed a joint JSON structure between _all_ online dictionaries in the world, starting with dictonaries within the Dictonary Society \(DSNA\). As of this writing, compliancedictionary.com, Merriam-Webster, Oxford English Dictionary, and Wordnik have all agreed to participate in a joint JSON structure.

This is forthcoming and will be hosted at GRCSchema.org

### Functional Requirements for Bibliographic Records

The Functional Requirements for Bibliographic Records \(FRBR\) is a conceptual entity–relationship model developed by the International Federation of Library Associations and Institutions \(IFLA\) that relates user tasks of retrieval and access in online library catalogs and bibliographic databases[\[11\]]().

[https://theucf.info/schemas-FRBR](https://theucf.info/schemas-FRBR)

### GRCSchema

GRCschema.org produces a collaborative, community activity with a mission to create, maintain, and promote schemas for structured data within the Governance, Risk, and Compliance universe. It’s vocabulary can be used within the JSON-LD encoding, covering entities that converge the schemas designed for NIST’s Informative Reference Catalog, NIST’s Open Security Controls Assessment Language \(OSCAL\), TagVault.org’s Software Identification Tags \(SWID Tags\), the Unified Compliance Framework, and SIGLEX, a Special Interest Group on the Lexicon of the Association for Computational Linguistics[\[12\]]().

[https://theucf.info/schemas-GRC](https://theucf.info/schemas-GRC)

### LegalXML

LegalXML[\[13\]](), managed by Oasis Open[\[14\]](), is split into two working groups, LegalDocumentML \(LegalDocML\) TC[\[15\]](), and LegalRuleML TC[\[16\]]().The OASIS LegalDocML TC works to advance worldwide best practices for the use of XML within a Parliaments', Assembly's or Congress' document management processes, within courts' and tribunals' judgment management systems, and generally in legal documents including contracts. The work is based on the Akoma Ntoso-UN project. The OASIS LegalRuleML TC defines a rule interchange language for the legal domain. The work enables modeling and reasoning that allows implementers to structure, evaluate, and compare legal arguments constructed using the rule representation tools provided.

[https://theucf.info/schemas-LegalXML](https://theucf.info/schemas-LegalXML)

### MITRE ATT&CK

A knowledgebase of adversary tactics and techniques based on real-world observations. The ATT&CK knowledge base is used as a foundation for the development of specific threat models and methodologies in the private sector, in government, and in the cybersecurity product and service community[\[17\]]().

[https://theucf.info/schemas-MitreAtt&ck](https://theucf.info/schemas-MitreAtt&ck)

### Open Policy Agent \(OPA\)

Open Policy Agent is a project that started in 2016 aimed at unifying policy enforcement across different technologies and systems[\[18\]](). It is an open source, general-purpose policy engine that unifies policy enforcement across the stack. OPA provides a high-level declarative language that lets you specify policy as code and simple APIs to offload policy decision-making from your software. You can use OPA to enforce policies in microservices, Kubernetes, CI/CD pipelines, API gateways, and more. OPA policies are expressed in a high-level declarative language called Rego[\[19\]]().

[https://theucf.info/schemas-OPA](https://theucf.info/schemas-OPA)

### Open Security Controls Assessment Language \(OSCAL\)

NIST, in collaboration with industry, is developing the Open Security Controls Assessment Language \(OSCAL\). OSCAL is a set of formats expressed in XML, JSON, and YAML. These formats provide machine-readable representations of control catalogs, control baselines, system security plans, and assessment plans and results. The Federal Risk and Authorization Management program \(FedRAMP\) office within the General Services Administration, began partnering with NIST on OSCAL in 2019[\[20\]]() to develop machine readable System Security Plans \(SSPs\)[\[21\]]() so that machine readability can be applied to the publication, implementation, and assessment of security controls.

[https://theucf.info/schemas-OSCAL](https://theucf.info/schemas-OSCAL)

### ReSpec

ReSpec makes it easier to write technical documents. It was originally designed for writing W3C specifications, but now supports many output formats. A ReSpec document can be stored as JSON or rendered as an HTML document that brings in the ReSpec script, defines a few configuration variables, and follows a few conventions.

[https://theucf.info/schemas-RecSpec](https://theucf.info/schemas-RecSpec)

### Rich Skill Descriptors

In order to create an ecosystem of recognition around skills, where Achievements, Pathways, and Learner Records make machine-readable references to skills and allow systems to take action based on the skills learners hold, it is important for implementers to use skills in common ways. RSDs build on [CTDL-ASN](https://credreg.net/ctdl/handbook#ctdlasnschema) to enable skill authors to publish definitions that can be referenced from digital credentials \(including those that appear in learner records\), pathways, and job profiles.

[https://theucf.info/schemas-RSD](https://theucf.info/schemas-RSD)

### Software Identification \(SWID\) Tags

NIST has developed a SWID Tag validation methodology and schema that can be used to verify that a produced SWID has properly implemented the requirements defined in NISTIR 8060[\[22\]](). TagVault has turned it into a queryable API and reference framework[\[23\]]().

[https://theucf.info/schemas-SWID](https://theucf.info/schemas-SWID)

### Structured Threat Information Expression \(STIX™\)

Structured Threat Information Expression \(STIX™\) is a language and serialization format used to exchange cyber threat intelligence \(CTI\)[\[24\]]().

[https://theucf.info/schemas-STIX](https://theucf.info/schemas-STIX)

### Strategy Markup Language \(StratML\)

The Strategy Markup Language originated as an answer to the US’ eGov Act, requiring federal agencies to publish their strategic and performance plans and reports in searchable, machine-readable format[\[25\]](). This was followed by a series of Open Government Executive Orders, policies, and directives[\[26\]](). The goal of StratML is to facilitate the sharing, referencing, indexing, discovery, linking, reuse, and analyses of the elements of strategic plans, including goal and objective statements as well as the names and descriptions of stakeholder groups and any other content commonly included in strategic plans[\[27\]]().

[https://theucf.info/schemas-StratML](https://theucf.info/schemas-StratML)

### Trusted Automated eXchange of Intelligence Information \(TAXII™\)

Trusted Automated eXchange of Intelligence Information \(TAXII™\) is an application layer protocol for the communication of cyber threat information in a simple and scalable manner.

[https://theucf.info/schemas-TAXII](https://theucf.info/schemas-TAXII)

### Unified Compliance Framework

The UCF has been at the forefront of compliance frameworks before the term GRC was coined by Michael Rasmussen. The Unified Compliance team have multiple patents regarding compliance frameworks, dictionary structures, etc. Their structure and framework standard will be presented throughout[\[28\]]().

[See GRCSchema](https://theucf.info/schemas-GRC)

### Vocabulary for Event Recording and Incident Sharing \(VERIS\)

A set of metrics designed to provide a common language for describing security incidents in a structured and repeatable manner[\[29\]]().

[https://theucf.info/schemas-VERIS](https://theucf.info/schemas-VERIS)

### ZOTERO

Zotero is a free, easy-to-use tool to help you collect, organize, cite, and share research. However, it is also a JSON schema for organizing citation and bibliographic data, much like Citation Style Language[\[30\]]().

[https://theucf.info/schemas-Zotero](https://theucf.info/schemas-Zotero)

## Bibliography

“Africa I-Parliaments &gt; Home.” n.d. Accessed December 28, 2020. https://publicadministration.un.org/parliaments/\#.X-oTQWSQH6V.

Ahmed, Mohamed. n.d. “Introducing Policy As Code: The Open Policy Agent \(OPA\).” Accessed December 28, 2020. https://www.magalix.com/blog/introducing-policy-as-code-the-open-policy-agent-opa.

“Akoma Ntoso \| Akoma Ntoso Site.” n.d. Accessed December 28, 2020. http://www.akomantoso.org/.

“Akoma Ntoso Version 1.0. Part 1: XML Vocabulary.” n.d. Accessed December 28, 2020. http://docs.oasis-open.org/legaldocml/akn-core/v1.0/akn-core-v1.0-part1-vocabulary.html.

Blake E. Strom et. al. n.d. “MITRE ATT&CKO: Design and Philosophy.” Accessed January 1, 2021. https://attack.mitre.org/docs/ATTACK\_Design\_and\_Philosophy\_March\_2020.pdf.

“Checklist of Requirements for Federal Websites and Digital Services.” 2014. Digital.Gov. January 9, 2014. /resources/checklist-of-requirements-for-federal-digital-services/.

“Citation Style Language - Citation Style Language.” n.d. Accessed January 1, 2021. https://citationstyles.org/.

Computer Security Division, Information Technology Laboratory. 2016. “Derived Relationship Mapping - Cybersecurity Framework \| CSRC.” CSRC \| NIST. May 24, 2016. https://csrc.nist.gov/Projects/Cybersecurity-Framework/derived-relationship-mapping.

“Control Correlation Identifier \(CCI\) – DoD Cyber Exchange.” n.d. Accessed April 17, 2020. https://public.cyber.mil/stigs/cci/.

“CVE - Common Vulnerabilities and Exposures \(CVE\).” n.d. Accessed January 8, 2021. https://cve.mitre.org/.

“E-Gov Act of 2002.” 2015. Digital.Gov. September 29, 2015. /resources/e-gov-act-of-2002/.

“FedRAMP Moves to Automate the Authorization Process \| FedRAMP.Gov.” n.d. Accessed December 28, 2020. https://fedramp.gov/FedRAMP-moves-to-automate-the-authorization-process/.

“GRCschema.Org.” n.d. Accessed September 23, 2020. https://grcschema.org/PersonName.

IFLA Study Group on the Functional Requirements for Bibliographic Records. n.d. _FUNCTIONAL REQUIREMENTS FOR BIBLIOGRAPHIC RECORDS_. https://www.ifla.org/files/assets/cataloguing/frbr/frbr\_2008.pdf.

“Introduction to Open Policy Agent.” n.d. Open Policy Agent. Accessed December 28, 2020. https://openpolicyagent.org/docs/latest/.

“Introduction to STIX.” n.d. Accessed January 1, 2021. https://oasis-open.github.io/cti-documentation/stix/intro.html.

Keller, Nicole, Stephen Quinn, Karen Scarfone, Matthew Smith, and Vincent Johnson. 2020. “National Online Informative References \(OLIR\) Program: Program Overview and OLIR Uses.” NIST Internal or Interagency Report \(NISTIR\) 8278. National Institute of Standards and Technology. https://doi.org/10.6028/NIST.IR.8278.

“Legal XML.” n.d. Accessed December 28, 2020. http://www.legalxml.org/.

Nations, United. n.d. “UN Department of Economic and Social Affairs.” United Nations. United Nations. Accessed December 28, 2020. https://www.un.org/en/desa.

“NVD - CPE.” n.d. Accessed September 27, 2020. https://nvd.nist.gov/products/cpe.

“OASIS LegalDocumentML \(LegalDocML\) TC \| OASIS.” n.d. Accessed December 28, 2020. https://www.oasis-open.org/committees/tc\_home.php?wg\_abbrev=legaldocml.

“OASIS LegalRuleML TC \| OASIS.” n.d. Accessed December 28, 2020. https://www.oasis-open.org/committees/tc\_home.php?wg\_abbrev=legalruleml.

“OASIS Open.” n.d. OASIS Open. Accessed December 28, 2020. https://www.oasis-open.org/.

“OPA Policy Language.” n.d. Open Policy Agent. Accessed December 28, 2020. https://openpolicyagent.org/docs/latest/policy-language/.

“Open Government Initiative.” n.d. The White House. Accessed December 28, 2020. https://obamawhitehouse.archives.gov/node/860.

“Software Publishers \| TagVault.Org.” n.d. Accessed December 28, 2020. https://tagvault.org/software-publishers/.

“Strategy Markup Language \(StratML\).” n.d. Accessed December 28, 2020. https://stratml.us/.

“The VERIS Framework.” n.d. Accessed January 1, 2021. http://veriscommunity.net/.

“Unified Compliance Framework Unties Overlapping Compliance Standards.” n.d. Accessed September 15, 2020. https://searchcompliance.techtarget.com/tip/Unified-Compliance-Framework-unties-overlapping-compliance-standards.

Waltermire, David, Brant Cheikes, Larry Feldman, and Gregory Witte. 2016. “Guidelines for the Creation of Interoperable Software Identification \(SWID\) Tags.” NIST Internal or Interagency Report \(NISTIR\) 8060. National Institute of Standards and Technology. https://doi.org/10.6028/NIST.IR.8060.

“Zotero Schema.” n.d. Accessed January 1, 2021. https://api.zotero.org/schema.

## Endnotes

1.  \(“Africa I-Parliaments &gt; Home” n.d.\) [↑]()
2.  \(Nations n.d.\) [↑]()
3.  \(“Akoma Ntoso \| Akoma Ntoso Site” n.d.\) [↑]()
4.  \(“Akoma Ntoso Version 1.0. Part 1: XML Vocabulary” n.d.\) [↑]()
5.  \(“NVD - CPE” n.d.\) [↑]()
6.  \(“CVE - Common Vulnerabilities and Exposures \(CVE\)” n.d.\) [↑]()
7.  \(“Citation Style Language - Citation Style Language” n.d.\) [↑]()
8.  \(“Control Correlation Identifier \(CCI\) – DoD Cyber Exchange” n.d.\) [↑]()
9.  \(Computer Security Division 2016\) [↑]()
10.  \(Keller et al. 2020\) [↑]()
11.  \(IFLA Study Group on the Functional Requirements for Bibliographic Records, n.d.\) [↑]()
12.  \(“GRCschema.Org” n.d.\) [↑]()
13.  \(“Legal XML” n.d.\) [↑]()
14.  \(“OASIS Open” n.d.\) [↑]()
15.  \(“OASIS LegalDocumentML \(LegalDocML\) TC \| OASIS” n.d.\) [↑]()
16.  \(“OASIS LegalRuleML TC \| OASIS” n.d.\) [↑]()
17.  \(Blake E. Strom et. al. n.d.\) [↑]()
18.  \(Ahmed n.d.\) [↑]()
19.  \(“Introduction to Open Policy Agent” n.d.\), \(“OPA Policy Language” n.d.\) [↑]()
20.  [↑]()
21.  \(“FedRAMP Moves to Automate the Authorization Process \| FedRAMP.Gov” n.d.\) [↑]()
22.  \(Waltermire et al. 2016\) [↑]()
23.  \(“Software Publishers \| TagVault.Org” n.d.\) [↑]()
24.  \(“Introduction to STIX” n.d.\) [↑]()
25.  \(“E-Gov Act of 2002” 2015\), US Code sections amended: 44 U.S.C. ch. 1 § 101; 44 U.S.C. ch. 35, subch. I § 3501 et seq; US Code sections created: 44 U.S.C. ch. 36 § 3601 et seq. 44 U.S.C. ch. 35, subch. III § 3541 et seq. [↑]()
26.  \(“Open Government Initiative” n.d.\) , \(“Checklist of Requirements for Federal Websites and Digital Services” 2014\) [↑]()
27.  \(“Strategy Markup Language \(StratML\)” n.d.\) [↑]()
28.  \(“Unified Compliance Framework Unties Overlapping Compliance Standards” n.d.\) [↑]()
29.  \(“The VERIS Framework” n.d.\) [↑]()
30.  \(“Zotero Schema” n.d.\) [↑]()

