# Generation Metadata Schema for Data Warehouse Automation

## Intent

To provide a collaborative space to discuss an exchange format concerning ETL generation metadata, supporting Data Warehouse Automation. This adapter should contain all metadata necessary to generate the transformation logic for a Data Warehouse solution.

### Links / structure

The following directories have been set up:

* Generic interface, containing the JSON schema definition.
* Class Library (DataWarehouseAutomation) containing the object model for deserialization, as well as various utility classes such as validation of files against the JSON schema definition.
* Code examples (examples_handlebars), containing C# examples using the generic interface for various purposes.
* Regression test project (test_project)

### Hypothesis

Across most, if not all, metadata models there is a core set of information that is required for any generation of ETL. If we can separate this from the UI / management of metadata we could have an exchange format that allows anyone to 'plug in' their own desired technology.

As an example '[TEAM](https://github.com/RoelantVos/TEAM)' has the intent to separate UI with a view of limiting data entry and validation, but does not focus on SQL generation. Rather, these functions are separated by an adapter that is accessible as JSON or database view.

#### Requirements

The fundamental requirements of the metadata adapter are:

* Containing all metadata required to generate ETL output. This notably includes:
  * source-to-target mappings
  * physical model metadata (columns and tables, data types etc.)
  * connectivity information, or proxy
* Text-based to support version control

#### Background

In the Data Warehouse Automation (DWA) domain there are many specialists (i.e. ETL developers, Data Warehouse and Data Architects, BI analysts etc.) who have been, or are working on, proprietary meta models to support forward-engineering of code and designs.

Some of these are built inside existing tools (i.e. ERwin, Powerdesigner) using SDKs or macros. Others use different development frameworks (.net, Java) and most use differently modelled repositories or file formats to persist data on disk.

This is in addition to the many off-the-shelf DWA platforms, each of which has their own repository and format as well.

In the broader sense of meritocracy, it is worth pursuing if a common exchange format for metadata can be defined in a way that any developer can develop to in whatever technology or way their passion drives them.

#### Working guidelines

For any change, create a new branch (no direct commits to master branch).