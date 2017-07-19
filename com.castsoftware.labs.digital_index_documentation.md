# _com.castsoftware.labs.digital-index_ Description

This extension provides computation of the following new assessment indicator\(s\)

* the _Digital Ready index_
* supporting Technical Criteria
* supporting Quality Rules

## Problem Statement

In order to leverage legacy IT assets via a digital transformation program, there is a need to assess the challenges IT organizations would face.
Typically, the challenges revolve around the following aspects:
* can you reliably trust transformation plans designed to open business data and processes to new communication channels and third-party software that are based on theoritical architecture? In other words, is the software really built the way you think it is so that your transformational plans are applicable?
* can you comfortably rely on existing accesses to business data and processes? In other words, can you easily reuse existing transactions?
* can you comfortably rely on existing business data? In other words, can you easily reuse existing data entities without risk that the software (in its entirety, not only the transactions you plan to reuse and expose) will corrupt it, make it unavailable or slow to access?
Any negative answer would mean at least some additional effort, ranging from a "simple" clean-up of the issues to major re-engineering.
Assessing the likelyhood of such additional effort is the problem at hand.

## Research Labs proposal

The Research Labs offer a solution based on CAST AIP Assessment Model, following a Goal-Question-Metric approach.

* The _Digital Ready Index_ goal, modeled as a Business Criterion, is based on the answers to the following three questions:
* The _Architecture Ready Index_ question: is the software complying to the official architecture blueprint? 
* The _Transaction Ready Index_ question: are the existing transactions from the software safe enough to be exposed and reused during the digital transformation?
* The _Data Ready Index_ question: assumming there are clean transactions managing the data entities from the software, are they safe from side-processes that use them as well?  

To answer these questions, the following metrics are implemented:
* Architecture Model compliance, based on application-specific target model
* Transaction-level Quality Rules, identifying transactions which accumulates too many ("too many" being supported by user-defined thresholds) issues in their midst that are related to the following areas: error and exception handling, data and sql efficiency, unexpected behaviors, expensive calls in loops 
* Data entity-level Quality Rules, identifying data entities which which accumulates too many ("too many" being supported by user-defined thresholds) issues in the software items that do use them, directly or not, that related to the following areas: error and exception handling, data and sql efficiency, unexpected behaviors, injections, SQL querying complexity, algorithmic complexity, data access architecture, and documentation 

What about transaction- and data entity-level Quality Rules?
* The transaction-level Quality Rules allow to focus on the parts of the software that matter most for the task at hand: the goal is not to cleanse the whole software from structural quality issues but to reuse and adapt what needs be, no more, no less.
* The data entity-level Quality Rules follow the same focussed approach with an additional twist to it: "side-processes" can also jeopardize the data even though they are not involved in exposed transactions. 
* Both kinds of Quality Rules rely on a super-additivity principle: individual structural quality issues are already part of traditional AIP assessment; what makes the difference here is the accumulation in inter-connected software components of similar issues.
* Both kinds of Quality Rules leverage the ability to bridge the gap between software components and business-related knowledge (which user-facing transactions are interesting, business-wise, for such transformation? which data entities?)
* Both kinds of Quality Rules are compliant with the AFP (Automated Function Points) OMG standard, meaning that only functional data entities and transactions are assessed, thus removing the noise from technical data and transactions)
  
The Research Labs released this first version of the Digital Ready Index to leverage the expertise and experience of customers in order to fine-tune its exact composition and collect feedback.

## Formula

The Digital Ready Index is based on the following Technical Criteria

* Architecture Ready Index, 
* Data Ready Index,
* Transaction Ready Index

The Architecture Ready Index is based on the following Quality Rules
* 1-to-many automated Architecture Checker rules

The Transaction Ready Index is based on the following Quality Rules
* Avoid transactions with too many severe Efficiency - Memory, Network and Disk Space Management issues along the path
* Avoid transactions with too many severe Efficiency - SQL and Data Handling Performance issues along the path
* Avoid transactions with too many severe Programming Practices - Error and Exception Handling issues along the path
* Avoid transactions with too many severe Efficiency - Expensive Calls in Loops issues along the path
* Avoid transactions with too many severe Programming Practices - Unexpected Behavior issues along the path

Default transaction-rule settings require to spot issues in more than 2 distinct objects for more than 2 distinct rules to mark a transaction as a violation. Considered transactions are AFP transactions. Considered issues are violations to severe enough rules related to the Technical Criterion referenced in the rule name. E.g.: "Avoid transactions with too many severe Programming Practices - Error and Exception Handling issues along the path" rule consider accumulation of violations to quality rules from the "Programming Practices - Error and Exception Handling" Technical Criterion that have either the Critical Contribution flag either a large enough Violation Index ("large enough" is defined by |ln(VI)| > 3). The list of considered violations is therefore dynamic and would adapt to languages, frameworks, and technologies covered by AIP extensions).

The Data Ready Index is based on the following Quality Rules
* Avoid data entities with too many severe Efficiency - SQL and Data Handling Performance issues
* Avoid data entities with too many severe Programming Practices - Error and Exception handling issues
* Avoid data entities with too many severe Programming Practices - Unexpected Behavior issues
* (_Critical_) Avoid data entities with SQL injection issues
* Avoid data entities with too many severe Complexity - SQL Queries issues
* Avoid data entities with too many severe Architecture - Multi-Layers and Data Access issues
* Avoid data entities with too many severe Documentation - Volume of Comments issues
* Avoid data entities with too many severe Complexity - Algorithmic and Control Structure Complexity issues

Default data-rule settings require to spot issues in more than 1 distinct object for more than 1 distinct rule to mark a data entity as a violation. Considered data entities are AFP data entities. Considered issues are violations to severe enough rules related to the Technical Criterion referenced in the rule name (similarly to the transaction-rule above)

# In what situation should you install this extension?

If you are interested in getting a preview of what the Digital Ready Index would be and are willing to share the results to help the CAST Research Labs validate them.

# Release notes

## 1.0.0
Initial release.

# _com.castsoftware.labs.digital-index_ technology support

All technologies supported out-of-the-box by CAST AIP are supported.
In case of technologies supported by some AIP extensions, the delivery of AFP configuration settings and of severe-enough Quality Rules to contribute to the Technical Criteria that are covered by the transaction- and data entity-level Quality Rules is enough to make the extension work.

# Function Point, Quality and Sizing support

This extension is designed to bring new quality indicators aside existing ones.

# CAST AIP compatibility

This extension is compatible with:

* 8.2.x out-of-the-box \(AIP release 8.2.0 used for the tests\)

# Supported DBMS servers

This extension is currently supported on CAST databases installed on CAST Storage Service only.

# Prerequisites

* An installation of any compatible release of CAST AIP \(see support information above\)
* For best results, ensure the data entities identifications is properly configured (if not, the Data Risk Index will be N\/A)
* For best results, ensure the transaction identifications is properly configured (if not, the Transaction Risk Index will be N\/A)

# Bug Fix List

N\/A

# Download and installation instructions

Please see:  [Extension Link Installation](http://doc.castsoftware.com/display/DOCEXT/Extension+download+and+installation)

The installation steps are the following:

* download the extension through the CAST Extend server (https://extend.castsoftware.com) or the CAST Extension Downloader using the https://extend.castsoftware.com:443/labs download server
* open Server Manager 8.2+
* select the existing set of databases to update \/ install a new set of databases
* manage extensions of the existing set of database \/ follow the installation wizard up to the manage extension pane
* select _com.castsoftware.labs.digital-index_ version _1.0.0_
* run the update \/ the installation  
* open CAST Management Studio
* import the Assessment Model from the Dashboard Service processed in steps \#3 to \#6 above; this is a _Mandatory_ step to start computing the new indicator, one MUST import and use the Assessment Model from the Dashboard that was updated with the extension
* to allow investigation along the Digital Ready Index findings in CAST AED, you need to change the "filterHealthFactor" parameter from the ..\\engineering\\resources\\ced.json web application configuration file to "false" from "true"
* to offer a direct access to Digital Ready Index analytics in CAST AAD, you need to add "QualityIndicatorResult" and "QualityIndicatorResults" tiles targeting the ID 2015200 in ..\\portal\\resources\\app.json and ..\\portal\\resources\\cmp.json web application configuration files

# Packaging, delivering and analyzing your source code

Packaging, delivering and analyzing your source code is performed the same way as usual, with extra care on the configuration of _transaction identification_.

To get results:

* run a new snapshot

To avoid computing the Digital Ready Index for applications that are not candidate to digital transformation:

* open CAST Management Studio
* edit the Dashboard Service\(s\) you are publishing the Snapshots of the N\/A application\(s\)
* select the Assessment Model tab
* create an exclusion for the Digital Ready index and the N\/A application\(s\)

# What results can you expect?

## Objects

N\/A

## Links

N\/A

## Quality rules

List of new Quality Rules

* Avoid transactions with too many severe Efficiency - Memory, Network and Disk Space Management issues along the path
* Avoid transactions with too many severe Efficiency - SQL and Data Handling Performance issues along the path
* Avoid transactions with too many severe Programming Practices - Error and Exception Handling issues along the path
* Avoid transactions with too many severe Efficiency - Expensive Calls in Loops issues along the path
* Avoid transactions with too many severe Programming Practices - Unexpected Behavior issues along the path
* Avoid data entities with too many severe Efficiency - SQL and Data Handling Performance issues
* Avoid data entities with too many severe Programming Practices - Error and Exception handling issues
* Avoid data entities with too many severe Programming Practices - Unexpected Behavior issues
* (_Critical_) Avoid data entities with SQL injection issues
* Avoid data entities with too many severe Complexity - SQL Queries issues
* Avoid data entities with too many severe Architecture - Multi-Layers and Data Access issues
* Avoid data entities with too many severe Documentation - Volume of Comments issues
* Avoid data entities with too many severe Complexity - Algorithmic and Control Structure Complexity issues


## Technical Criteria

List of new Technical Criteria

* Architecture Ready Index, 
* Data Ready Index,
* Transaction Ready Index

## Business Criteria

List of new Business Criteria

* Digital Ready index

# Limitations

N\/A
