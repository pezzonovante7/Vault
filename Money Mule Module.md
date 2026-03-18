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
	- 

- Queries to RMWNG
	- {Police Department Details} addition to lien marking remarks in Finacle
	- RM Wing should create new lien reason code in Finacle
        Check through Front End
        RM Wing to take up with PMO and block the SMS sending for the reason code
	- details of duplicate lien marking in Finacle


- the values Reported in Multiple :
Transactions : x times
Complaints : y times are optional. they maybe present or may not be present the details of the account for the transactions which do not have these values are being ignored by the current script. make the necessary changes to make sure the transaction details are captured and written in the output.txt file regardless of these lines in the data.txt


there can be cases where there is an additional value after the disputed : xxxx the particular value is the reference no. this value needs to be ignored. the current script runs into error when this happens. 
sample transaction without reference no
2	Account Credited to :
 Kerala Gramin Bank
40247111000876
KLGB0040247
Layer : 5
Reported in Multiple :
Transactions : 1 times
Complaints : 5 times
JAKAN12026010801008749	Transaction : 57000
Disputed : 1999.41
08/01/2026 17:10:PM	03/01/2026 11:02:AM	-32897.39	

TAMIL NADU


: JNK Bank API

:

: Jammu and Kashmir Bank

Date :18/03/2026 11:14:AM

sample transaction with reference no.

2	Account Credited to :
 Kerala Gramin Bank
40247111000876
KLGB0040247
Layer : 5
Reported in Multiple :
Transactions : 1 times
Complaints : 5 times
JAKAN12026010801008749	Transaction : 57000
Disputed : 1999.41	ALL
08/01/2026 17:10:PM	03/01/2026 11:02:AM	-32897.39	

TAMIL NADU


: JNK Bank API

:

: Jammu and Kashmir Bank

Date :18/03/2026 11:14:AM