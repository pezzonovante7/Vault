- RO User for Letter modules


- OTS Module
	- remove the OSL_EVENT_ID column from the table. 
	- a
	- when verify is absent insert with 51 status


THE CONCAT STATEMENT NEED NOT BE VERTICALLY ALIGNED

CURRENT CODE 

SET GLINK2                      := CONCAT('E0501102911A000CYN^Cancel#D#1012*CANCEL*',
                                                      IFNULL(GOTSID, ''),
                                                      '*',
                                                      IFNULL(GMODE, ''),
                                                      '|');

EXPECTED 

SET GLINK2                      := CONCAT('E0501102911A000CYN^Cancel#D#1012*CANCEL*', IFNULL(GOTSID, ''), '*', IFNULL(GMODE, ''), '|');