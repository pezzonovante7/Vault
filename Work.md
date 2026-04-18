- DEC Work
	- SOLSET needs to be enabled for HO users
	- SOLSET relevant to RO users needs to be enabled to AGM or CM in RO
	- SOLSET ALL needs to be enabled for Wing Heads

- ADAMANT
	- 1019

- Claude Configs
	- all read permissions allowed
	- the build engine menu skills feels like a mouthful to you. the fetch process for fetching the design from the spreadsheets can rebuilt into a separate skill and so is the test generation process.
		- for the new skill for fetching the design from the design spreadsheet URL, you can create a new skill. the skill will fetch the design from the given URL or Work ID. you can summarize your understanding of the design and confirm with me.
		- the test generation process can also be moved into a separate skill. you can use it to create tests for the changes that you make. the changes can be new menus, enhancements to existing menus or anything else.
		- the flow should go as follows - after a new task assignment, i will first provide you the design, you can fetch the design and summarize your understanding. if any edits i will do right then. after confirmation we can move to building the menu. once the menu is built inside out. we can then move to the text generation. all these processes should work independently so that it will flexible for any future changes.

- 488 issue contact Binu Sir
	- ```
	  	  Expected Response Format
		  {
		    "status": 1,
		    "statusMessage": "Success",
		    "suitDetails": {
		      "suitType": null,
		      "suitNumber": null,
		      "suitDate": null,
		      "plaintAmount": null,
		      "courtType": null,
		      "courtPlace": null,
		      "natureOfSuit": null,
		      "advocateName": null,
		      "abjStatus": null,
		      "abjDetails": null
		    },
		    "decreeDetails": [],
		    "epDetails": []
		  }
		
		  Current (Actual) Response Format
		
		  {
		    "status": 1,
		    "statusMessage": "Success",
		    "suitDetails": ,
		    "decreeDetails": [],
		    "epDetails": []
		  }
	  ```
	  API 488 returns a response that is not valid JSON — "suitDetails" is emitted with no value


- 1019
when I open 1019 menu with CONTROL ID 1019*1040*U for the customer with ID 492145300 no details are present. when I click on the SUBMIT button, an error is showing up saying Networth @ Sanction for CUST1001 - Enter Value. this is very inconsistent. this is present for the other errors as well. can you fix this
