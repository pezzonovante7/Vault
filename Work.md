- DEC Work
	- SOLSET needs to be enabled for HO users only for CHM or AGM 
	- SOLSET relevant to RO users needs to be enabled to AGM / CM in RO
	- SOLSET ALL needs to be enabled for Wing Heads
	- Letter
		- Day end check report new - needs to be created
		- Sub Dept wise exemption, only for RO/HO

- Claude Configs
	- all read permissions allowed
	- the build engine menu skills feels like a mouthful to you. the fetch process for fetching the design from the spreadsheets can rebuilt into a separate skill and so is the test generation process.
		- for the new skill for fetching the design from the design spreadsheet URL, you can create a new skill. the skill will fetch the design from the given URL or Work ID. you can summarize your understanding of the design and confirm with me.
		- the test generation process can also be moved into a separate skill. you can use it to create tests for the changes that you make. the changes can be new menus, enhancements to existing menus or anything else.
		- the flow should go as follows - after a new task assignment, i will first provide you the design, you can fetch the design and summarize your understanding. if any edits i will do right then. after confirmation we can move to building the menu. once the menu is built inside out. we can then move to the text generation. all these processes should work independently so that it will flexible for any future changes.

- 488 issue contact Binu Sir
	- ```json
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

- Question to Franklin Sir
	- new param sequence for each EVENTID or a single global one
	- pickups not defined for a lot of fields in Suit and a field in RR
	- for account no 40267131000584 in Suit, suit details are empty but other are not
		- ![[Pasted image 20260420163240.png]]
	- same issue with account no - 40267131008850 (M)

- when SOLID ALL is selected while selecting module as ALL, the SUB DEPT row should appear. if the user selects some sub department X, all the DEC related that selected sub dept in all SOLIDs should be cleared. the SUB DEPT should only appear when the module is selected as Letters, it should not be visible for module ALL.
