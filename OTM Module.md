
create a new Menu 1004 - Whitelisting of Accounts 

under inspection module - /Routines/Inspection/

design is provided in the attached image 

Purpose

        Whitelisting of accounts, OTM Report ID wise for excluding the accounts from OTM Listing

User Access

        Branchs users only
        Maker and checker should be different
        Checker should be Branch Manager

    Workflow

        Add Mode

            Capture Account Number and OTM Report ID
            Ensure that atleast an entry exist for the account in the otm master table against the login user solid
            Should not allow if a record already exists for the account and report id where valid upto date is >= current date

        Other Modes

            Account Number and OTM Report ID are display fields, with OTM Report name displayed

        Justification and valid upto is mandatory

            Valid upto - Should permit a maximum of 3 months

        Lock option should be provided, if the current date is <= valid upto date

    Table

        OTM_WHITELIST_MASTER

DROP TABLE IF EXISTS OTM_WHITELIST_MASTER;
    CREATE TABLE OTM_WHITELIST_MASTER
    (
        OWM_WHITELIST_ID                             INT,
        OWM_CREATE_DATE                              DATE,
        OWM_LOCK_DATE                                DATE,
        OWM_CREATE_SOLID                             VARCHAR(8),
        OWM_ACCOUNT_NUMBER                           VARCHAR(20),
        OWM_OTM_REPORT_ID                            VARCHAR(20),
        OWM_JUSTIFICATION                            VARCHAR(500),
        OWM_VALID_UPTO                               DATE,
        OWM_RECORD_STATUS                            INT,
        OWM_UUSER                                    VARCHAR(15),
        OWM_UDATE                                    DATETIME
    );
    CREATE INDEX OTM_WHITELIST_MASTER_IDX1 ON OTM_WHITELIST_MASTER (OWM_WHITELIST_ID);
    CREATE INDEX OTM_WHITELIST_MASTER_IDX2 ON OTM_WHITELIST_MASTER (OWM_CREATE_SOLID);
    CREATE INDEX OTM_WHITELIST_MASTER_IDX3 ON OTM_WHITELIST_MASTER (OWM_ACCOUNT_NUMBER,OWM_OTM_REPORT_ID);
