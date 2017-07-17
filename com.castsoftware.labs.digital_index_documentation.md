# _com.castsoftware.labs.digital-index_ Description

This extension provides computation of the following new assessment indicator\(s\)

* the _Digital Ready index_
* supporting Technical Criteria

## Problem Statement

In order to leverage legacy IT assets via a digital transformation program, there is a need to assess the challenges IT organizations would face.

## Research Labs proposal

The Research Labs offer a solution based on CAST AIP Assessment Model, following a Goal-Question-Metric approach.

* The _Digital Ready Index_ goal, modeled as a Business Criterion, based on the answers to the following three questions:
* The _Architecture Ready Index_ question: is the software complying to the official architecture blueprint? 
* The _Transaction Ready Index_ question: are the existing transactions from the software safe enough to be exposed and reused during the digital transformation?
* The _Data Ready Index_ question: assumming there are clean transactions managing the data entities from the software, are they safe from side-processes that use them as well?  

To answer these questions, the following metrics are implemented:
* Architecture Model compliance, based on application-specific target model
* Transaction-level Quality Rules, identifying transactions which accumulates too many ("too many" being supported by user-defined thresholds) issues in their midst that are related to the following areas: error and exception handling, data and sql efficiency, unexpected behaviors, expensive calls in loops 
* Data entity-level Quality Rules, identifying data entities which which accumulates too many ("too many" being supported by user-defined thresholds) issues in the software items that do use them, directly or not, that related to the following areas: error and exception handling, data and sql efficiency, unexpected behaviors, injections, SQL querying complexity, algorithmic complexity, data access architecture, and documentation 

  
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

The Data Ready Index is based on the following Quality Rules
* Avoid data entities with too many severe Efficiency - SQL and Data Handling Performance issues
* Avoid data entities with too many severe Programming Practices - Error and Exception handling issues
* Avoid data entities with too many severe Programming Practices - Unexpected Behavior issues
* (_Critical_) Avoid data entities with SQL injection issues
* Avoid data entities with too many severe Complexity - SQL Queries issues
* Avoid data entities with too many severe Architecture - Multi-Layers and Data Access issues
* Avoid data entities with too many severe Documentation - Volume of Comments issues
* Avoid data entities with too many severe Complexity - Algorithmic and Control Structure Complexity issues



# In what situation should you install this extension?

If you are interested in getting a preview of what the Digital Ready Index would be and are willing to share the results to help the CAST Research Labs validate them.

# Release notes

## 1.0.0
Initial release.

# _com.castsoftware.labs.digital-index_ technology support

All technologies supported out-of-the-box by CAST AIP are supported.
In case of technologies supported by some AIP extensions, contact the Research Labs to build a compatible CloudReady index.

# Function Point, Quality and Sizing support

This extension is designed to bring new quality indicator aside existing ones.

# CAST AIP compatibility

This extension is compatible with:

* 8.2.x out-of-the-box \(AIP release 8.2.0 used for the tests\)

# Supported DBMS servers

This extension is currently supported on CAST databases installed on CAST Storage Service only.

# Prerequisites

* An installation of any compatible release of CAST AIP \(see support information above\)
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
