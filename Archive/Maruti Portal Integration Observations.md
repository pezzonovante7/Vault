
- KGB
	- ROEKM
		- RO Users
			- RATH2498
			- SNEH4827
		- Branches
			- 40611
				- ARUN5242
				- ANAN6964
				- Loan Account No 61115359000126

- Remarks optional and if entered should contain at least 3 chars
- 
- disbursement date is not captured
- 984 menu date required for updating in portal as well
	- currently the date column is showing create date of the status which is irrelevant
- 984 menu alignment of table elements not perfect
	- number right
	- text left
	- date center
- details needed for RO users
	1. Application ID
	2. Current status
	3. Disbursal amount
	4. Sanction date
	5. Disbursal date
	6. Rejection date
	7. Remarks
- prompt to make the necessary changes
	- currently the Pending button click in menu 984 gives records with details 
	- |SL|Status ID|Proposal ID|Maruti App No|Branch|Status|Date|Confirm|
	- the Status ID, Branch, Status Date can be dropped
	- Instead these details needs to be displayed in the datagrid
		1. Disbursal amount
		2. Sanction date 
		3. Disbursal date 
		4. Rejection date
		5. Remarks
- alignment in datagrid
	- numbers left aligned
	- text right aligned
	- date is center aligned
- when status is marked as SD, should disbursement date and sanction date be updated to open date.