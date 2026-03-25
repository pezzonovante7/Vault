- Files Modified
	- ENGINE_LINK_BUTTON_844
	- GET_IS_MULE_MODULE_AUTHORISED_USER
	- ENGINE_LINK_BUTTON_849
	- FN_ENGINE_SEARCH_GETCOUNT_849
	- FETCH_ENGINE_SEARCH_DATA_849
	- 
	- ENGINE_LINK_BUTTON_836
	- FN_MULE_IS_FREEZE_MARKED_IN_CBS
	- FN_MULE_IS_LIEN_MARKED_IN_CBS
	- FREEZE_MARKED_INTIMATION_EMAIL
	- API_420_CALL
	- GET_API_420_XML
	- FN_ENGINE_SEARCH_GETCOUNT_836
	- FETCH_ENGINE_SEARCH_DATA_836
	-  
	- ENGINE_LINK_BUTTON_846
	- 
	- MULE_GET_EARLIER_INCIDENTS_EXIST
	- ENGINE_LINK_BUTTON_846
	- GET_API_419_XML
	- ENGINE_LINK_BUTTON_836

- RMWNG ip address
	- 10.130.170.27
	- 

- Queries to RMWNG
	- {Police Department Details} addition to lien marking remarks in Finacle
	- RM Wing should create new lien reason code in Finacle
        Check through Front End
        RM Wing to take up with PMO and block the SMS sending for the reason code
	- details of duplicate lien marking in Finacle
- New Bug Report - another field present as ALL

- Unassign Specific
- for @PROCEDURE ENGINE_LINK_BUTTON_846.sql- a new option needs to be added to the dropdown - Unassign Specific. when the option is selected, the Assigned To and Acknowledgement ID are mandatory. the details entered needs to validated and ticket should be in a pending status(MTM_UPDATE_DATE IS NULL) only then the ticket needs to be unassigned.

- the number of complaints is currently not being stored in the DB. the number of complaints is part of the input string provided for parsing. it appears just before the transaction ID with delimited ~ separating them. the number of complaints for each entry needs to be captured and stored in MTE_NO_OF_COMPLAINTS in MULE_TICKET_ENTRIES. I made some changes but it is still not working. can you fix this issue.


- Pending
	- Enhancement 1

        Support for debit transaction
        Get examples from RM Wing and Implement
        Also see that after implementing, data is coming from Finacle during data fetch and ensure that it is correct
        If not rectify the same. Seek assistance from Binu

- 3 bugs fix
	- 20260317122922
	- 20260317123131
	- 20260317123303
- 