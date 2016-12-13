# Notes on the KBase SDK

## The App Catalog

If you visit the App Catalog interface, there is a lot of useful information about the state of apps:
https://narrative.kbase.us/#catalog
[![KBase Catalog](images/KBaseCatalog.png)](https://narrative.kbase.us/#catalog)

## The Narrative spec.json file

The Google Doc that describes the Narrative UI Specification file can be found here:
[https://docs.google.com/document/d/1CZ1GOKsRr1NsScG9E2EesJyk_ViOrM9OazrVFKCkyHs/edit?usp=sharing](https://docs.google.com/document/d/1CZ1GOKsRr1NsScG9E2EesJyk_ViOrM9OazrVFKCkyHs/edit?usp=sharing)

For archival purposes, there is a PDF snapshot of the document [included in this repo](.
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
	"parameters": [ 
		{
			"id": "read_library_ref",
			"optional": false,
			"advanced": false,
			"allow_multiple": false,
			"default_values": [ "" ],
			"field_type": "text",
			"text_options": {
				"valid_ws_types": ["KBaseAssembly.PairedEndLibrary","KBaseFile.PairedEndLibrary"]
			}
		},
		{
		    "id" : "output_contigset_name",
		    "optional" : false,
		    "advanced" : false,
		    "allow_multiple" : false,
		    "default_values" : [ "MEGAHIT.contigs" ],
		    "field_type" : "text",
		    "text_options" : {
		     	"valid_ws_types" : [ "KBaseGenomeAnnotations.Assembly" ],
		    	"is_output_name":true
		    }
		},
		{
		    "id" : "megahit_parameter_preset",
		    "optional" : true,
		    "advanced" : false,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "dropdown",
		    "dropdown_options":{
		      "options": [
		        {
		          "value": "meta",
		          "display": "meta - General metagenome assembly, e.g. gut"
		        },
		        {
		          "value": "meta-sensitive",
		          "display": "meta-sensitive - More sensitive assembly, but slower"
		        },
		        {
		          "value": "meta-large",
		          "display": "meta-large - Large and complex assembly, e.g. soil"
		        },
		        {
		          "value": "bulk",
		          "display": "bulk - (experimental) bulk sequencing assembly"
		        },
		        {
		          "value": "single-cell",
		          "display": "single-cell - (experimental) single-cell assembly"
		        }
		      ]
		    }
		},
		{
		    "id" : "min_count",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int"
		    }
		},
		{
		    "id" : "k_min",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int",
      			"min_int" : 1,
      			"max_int" : 127
		    }
		},
		{
		    "id" : "k_max",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int",
      			"min_int" : 1,
      			"max_int" : 127
		    }
		},
		{
		    "id" : "k_step",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int",
      			"min_int" : 1,
      			"max_int" : 28
		    }
		},
		{
		    "id" : "k_list",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : true,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int",
      			"min_int" : 15,
      			"max_int" : 127
		    }
		},
		{
		    "id" : "min_contig_len",
		    "optional" : true,
		    "advanced" : true,
		    "allow_multiple" : false,
		    "default_values" : [ "" ],
		    "field_type" : "text",
			"text_options" : {
			    "validate_as": "int",
      			"min_int" : 1
		    }
		}
	],
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
				{
					"input_parameter": "megahit_parameter_preset",
          			"target_property": "megahit_parameter_preset"
				},
				{
					"input_parameter": "min_count",
          			"target_property": "min_count"
				},
				{
					"input_parameter": "k_min",
          			"target_property": "k_min"
				},
				{
					"input_parameter": "k_max",
          			"target_property": "k_max"
				},
				{
					"input_parameter": "k_step",
          			"target_property": "k_step"
				},
				{
					"input_parameter": "k_list",
          			"target_property": "k_list"
				},
				{
					"input_parameter": "min_contig_len",
          			"target_property": "min_contig_len"
				}
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
