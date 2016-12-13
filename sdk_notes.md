# Notes on the KBase SDK

## The App Catalog

If you visit the App Catalog interface, there is a lot of useful information about the state of apps:
https://narrative.kbase.us/#catalog
[![KBase Catalog](images/KBaseCatalog.png)](https://narrative.kbase.us/#catalog)

## The Narrative spec.json file

The Google Doc that describes the Narrative UI Specification file can be found here:
[https://docs.google.com/document/d/1CZ1GOKsRr1NsScG9E2EesJyk_ViOrM9OazrVFKCkyHs/edit?usp=sharing](https://docs.google.com/document/d/1CZ1GOKsRr1NsScG9E2EesJyk_ViOrM9OazrVFKCkyHs/edit?usp=sharing)

For archival purposes, there is a PDF snapshot of the document [included in this repo](sample_files/NarrativeUIMethodSpecification.pdf).
This local copy is likely to be out of date at the time the reader looks at it, but may be useful in case the Google Doc is unavailable.

The following code fragment is an example from the Megahit repo and has some annotation using Javascript comments "//" inline.
A large portion of the file has been removed so that the "behavior" property can be focused on - this controls the interaction
between the front end form fields displayed in Narrative App Cells, and the backend API call. Sections that have been deleted
are noted with elipses "..."

~~~
{
	"ver": "1.0.4",
	
	"authors": [
		"msneddon"
	],
	"contact": "help@kbase.us",
	"visible": true,
	"categories": ["active","assembly","communities"],
	"widgets": {
		"input": null,
		"output": "no-display"
	},

    ...

	"behavior": { 
		"service-mapping": { // This is the main attribute you will use
			"url": "",
			"name": "MEGAHIT",
			"method": "run_megahit", // This definition is for the run_megahit function in the KIDL file
			"input_mapping": [ // Mapping between input form fields to the parameters in the KIDL spec
				{
					"narrative_system_variable": "workspace", // Internal value/variable in narrative
					"target_property": "workspace_name" // the workspace where this should run in the app
				},
				{
					"input_parameter": "read_library_ref", // Form field on the app input form
          			"target_property": "read_library_ref", // destination property from the KIDL spec
          			"target_type_transform": "resolved-ref" // "resolved-ref" converts from textual name to numeric wsid
				},
				{
					"input_parameter": "output_contigset_name",
          			"target_property": "output_contigset_name"
				},
    ...
			],
			"output_mapping": [ //map from output object from KIDL to UI fields
                                // if there is a declaration with "input_parameter"
                                // this will just copy from the input box to the output field
				{
					"narrative_system_variable": "workspace",
					"target_property": "workspace_name"
				},
				{
					"service_method_output_path": [0,"report_name"], // use the first object returned and grab the "report_name" field
					"target_property": "report_name"
				},
				{
					"service_method_output_path": [0,"report_ref"],
					"target_property": "report_ref"
				},
				{
					"constant_value": "16",
					"target_property": "report_window_line_height"
				}
			]
		}
	},
	"job_id_output_field": "docker"
}
~~~~
