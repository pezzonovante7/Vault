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

- Queries to RMWNG
	- Check with RM Wing, whether they are expecting the same value stored in MTT_POS_TRANSACTION_ID
		- REMOVE PREFIX "POS"
	- Get other options for MTE_CLOSE_REASON from RM Wing

- Queries 
	- should Lien Marked row be dropped when Freeze Account is enabled ???
		- if yes, A new field MTE_FREEZE_REASON is also needed ???
			- BOTH LIEN MARK AND FREEZE OPTIONS ARE NEEDED AS PER RMWNG

- PAN number not getting populated all the time.
	- populated for ticket ID -  2292

- when the finacle API returns data it is returning both 22 char tran ID and 16 char tran ID
- SAMPLE FORMAT - KLGBN52026010536344510,KLGBH26005366982
- need to add a new row in the popup grid to show both 22 char tran ID and 16 char tran ID
- even in the data grid with header
	|Head|Status|Tran Date|Tran ID|Tran Amount|More Info|
	the transactionID should be shown in separate lines in the same cell (no additional row needed)

- Display both 16 digit and 22 digit UTR Number for NEFT/RTGS transactions. for other transactions only a single field Transaction Id needs to be shown.
- 