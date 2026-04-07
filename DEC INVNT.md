inventory module has a different day end check compared to other modules
the day end check is exempted by DAY_END_CHECK_INVNT
currently when a record exists in DAY_END_CHECK_EXEMPT, the DEC is ignored
instead, DAY_END_CHECK_EXEMPT_NEW should have two types of records one exempting Unverified Create Indents and the other for inventory stock marking
the DEC should be exempted separately instead
the 998 menu should be modified accordingly for the drop down to include two values