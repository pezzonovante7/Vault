Implement a copy of Menu 998 in PGRS Module
the dropdown options should be
CPA        │ Unattended customer complaint│ 
DTS        │ KGB Tatkal Loan account│
CTA        | CIBIL Trigger Actions |  
    covering both
	CTAUR      │ Unverified records in CIBIL Trigger Actions │ 
	CTDEC      │ Pending Action in CIBIL Trigger requests    │       

for DTS, CTA CRWNG is authorised
for CPA PDWNG is authorised
ITWNG is as usual

DAY_END_CHECK_PGRS should be modified to use DAY_END_CHECK_EXEMPT_NEW instead