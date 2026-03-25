
- Add Mode

            Capture Account Number and OTM Report ID
            Ensure that atleast an entry exist for the account in the otm master table against the login user solid
            Should not allow if a record already exists for the account and report id where valid upto date is >= current date


    DROP TABLE IF EXISTS OTM_MASTER;
    CREATE TABLE OTM_MASTER
    (
        OM_OTM_ID                                       INT,
        OM_OTM_DATE                                     DATE,
        OM_SOLID                                        VARCHAR(8),
        OM_REPORT_ID                                    INT,
        OM_ACCOUNT_NO                                   VARCHAR(20),

        OM_LYING_AT                                     VARCHAR(8),
        OM_LYING_SINCE                                  DATE,

        OM_LAST_ACTION_SOLID                            VARCHAR(8),
        OM_LAST_ACTION                                  VARCHAR(5),
        OM_LAST_ACTION_RECORD_STATUS                    INT,
        OM_LAST_ACTION_DATE                             DATE,

        OM_OTM_STATUS                                   VARCHAR(5),
        OM_CLOSE_DATE                                   DATE,
        OM_IS_ANNEXURE2_SUBMITTED                       VARCHAR(2),

        OM_RECORD_STATUS                                INT,
        OM_UUSER                                        VARCHAR(15),
        OM_UDATE                                        DATETIME
    );
    CREATE INDEX OTM_MASTER_IDX1 ON OTM_MASTER (OM_OTM_ID);
    CREATE INDEX OTM_MASTER_IDX2 ON OTM_MASTER (OM_SOLID,OM_OTM_DATE);
    CREATE INDEX OTM_MASTER_IDX3 ON OTM_MASTER (OM_LYING_AT,OM_OTM_STATUS);
    CREATE INDEX OTM_MASTER_IDX4 ON OTM_MASTER (OM_ACCOUNT_NO);

    <!-- OM_IS_ANNEXURE2_SUBMITTED -->
    <!-- Y - Yes -->
    <!-- N - No -->
    <!-- NULL or NA - Not Applicable -->

    -- OM_OTM_STATUS Pickup
    -- Default: BUA (Branch Unattended) with OM_CLOSE_DATE = NULL
    DELETE FROM PARAM_PICKUP_ALPHA WHERE PICKUP_CODE = 'OM_OTM_STATUS';
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', '0', 'OTM Record Status', 51, 'Y', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'BUA', 'Branch Unattended', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'BIN', 'Branch Initiated', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'BRE', 'Returned to Branch', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'RUA', 'Regional Office Unattended', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'RIN', 'Regional Office Initiated', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'RRE', 'Returned to Regional Office', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'SUA', 'Section Unattended', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'SIN', 'Section Initiated', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OM_OTM_STATUS', 'CLS', 'Closed', 51, 'N', 'SYSTEM');
    COMMIT;

    DELETE FROM PARAM_PICKUP_ALPHA WHERE PICKUP_CODE = 'OTM_RISK_CATEGORY';
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OTM_RISK_CATEGORY', '0', 'OTM RISK CATEGORY', 51, 'Y', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OTM_RISK_CATEGORY', '1', 'High', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OTM_RISK_CATEGORY', '2', 'Medium', 51, 'N', 'SYSTEM');
    INSERT INTO PARAM_PICKUP_ALPHA VALUES ('OTM_RISK_CATEGORY', '3', 'Low', 51, 'N', 'SYSTEM');
    COMMIT;