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
	- {Police Department Details} addition to lien marking remarks in Finacle
	- RM Wing should create new lien reason code in Finacle
        Check through Front End
        RM Wing to take up with PMO and block the SMS sending for the reason code

Purpose

        Add Police Department details to lien marking remarks in Finacle

    Location
        
        @FUNCTION GET_API_419_XML.sql
        FUNCTION GET_API_419_XML
        Rmks element in AcctLienAdd and AcctLienMod XML

    Current Format

        CYBER CRIME NCRP_<Acknowledgement_ID>; Layer - <Layer>

    New Format

        CYBER CRIME NCRP_<Acknowledgement_ID>; Layer - <Layer>; <Police_Department>

    Source of Police Department
    
MTM_REQUEST_DEPARTMENT from MULE_TICKET_MASTER 
            and 
            MTE_STATE from MULE_TICKET_ENTRIES