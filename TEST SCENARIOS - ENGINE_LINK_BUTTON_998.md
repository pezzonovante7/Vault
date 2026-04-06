# Manual GUI Test Scenarios - Exempt Day End Check (Menu 998)

## How the Screen Works

1. Open Menu **998** from the Engine menu
2. The form loads with **Module** (dropdown), **SOLID/SOLSET** (text input + search), **SOL Name** (read-only), and a **Go** button
3. After clicking **Go** with valid inputs, the **Remarks** field and **Submit** / **Cancel** buttons become active
4. For **ALE** module only, an **Account Number** field appears after Go
5. Clicking **Submit** exempts the selected SOLID from day-end checks for the chosen module

---

## User Accounts for Testing

| User ID  | SOLID | Designation | Workclass | Purpose                      |
| -------- | ----- | ----------- | --------- | ---------------------------- |
| FRAN1875 | ITWNG | MAN         | 999       | Full access (IT Wing WC 999) |
| DEEP5093 | ITWNG | SEM         | 441       | IT Wing but WC not 999       |
| SHAR5475 | ITWNG | MAN         | 441       | IT Wing MAN but WC not 999   |
| SOBH2217 | CRWNG | CHM         | 641       | CRM Wing - ASM+ designation  |
| HARI6296 | CRWNG | ASM         | 441       | CRM Wing - ASM designation   |
| MATH6980 | CRWNG | OAS         | 241       | CRM Wing - below ASM         |
| ARUN5188 | ROTLY | SEM         | 421       | RO Trivandrum - ASM+ desig   |
| RIJE7989 | ROTLY | OAS         | 221       | RO Trivandrum - below ASM    |
| DILE1829 | CHKKD | ASM         | 421       | Branch user                  |

### SOLIDs for Testing

| SOLID | Type              | RO Code |
|-------|-------------------|---------|
| 40480 | Branch of ROTLY   | ROTLY   |
| 40499 | Branch of ROTLY   | ROTLY   |
| 40643 | Branch of ROEKM   | ROEKM   |
| ROTLY | Regional Office   | ROTLY   |
| ROEKM | Regional Office   | ROEKM   |

---

## SECTION 1: ACCESS CONTROL

### Scenario 1.1 - Branch user cannot access menu

> **Login as:** DILE1829 (CHKKD, ASM, WC 421)

1. Open Menu 998
2. **Expected:** Error message - *"Access restricted to IT Wing, CRM Wing and RO users only."*
3. The form should NOT load

---

### Scenario 1.2 - RO user with low designation cannot access menu

> **Login as:** RIJE7989 (ROTLY, OAS, WC 221)

1. Open Menu 998
2. **Expected:** Error message - *"Only Assistant Managers and above are authorised to access this menu in Regional Offices."*
3. The form should NOT load

---

### Scenario 1.3 - IT Wing user with workclass other than 999 cannot access menu

> **Login as:** DEEP5093 (ITWNG, SEM, WC 441)

1. Open Menu 998
2. **Expected:** Error message - *"Only users with Workclass 999 are authorised to access this menu in IT Wing."*
3. The form should NOT load

> **Also try with:** SHAR5475 (ITWNG, MAN, WC 441) - Even though designation is MAN, the check is on workclass not designation

---

### Scenario 1.4 - CRM Wing user with low designation cannot access menu

> **Login as:** MATH6980 (CRWNG, OAS, WC 241)

1. Open Menu 998
2. **Expected:** Error message - *"Only Assistant Managers and above are authorised to access this menu in CRM Wing."*
3. The form should NOT load

---

### Scenario 1.5 - IT Wing WC 999 can access menu

> **Login as:** FRAN1875 (ITWNG, MAN, WC 999)

1. Open Menu 998
2. **Expected:** Form loads successfully with title *"Exempt Day End Check"*
3. Module dropdown, SOLID/SOLSET field, and Go button should be **enabled**
4. Remarks field and Submit button should be **disabled/greyed out**

---

### Scenario 1.6 - CRM Wing ASM+ can access menu

> **Login as:** SOBH2217 (CRWNG, CHM, WC 641)

1. Open Menu 998
2. **Expected:** Form loads successfully
3. All key fields enabled, child fields disabled (same as 1.5)

---

### Scenario 1.7 - RO user with ASM+ can access menu

> **Login as:** ARUN5188 (ROTLY, SEM, WC 421)

1. Open Menu 998
2. **Expected:** Form loads successfully
3. All key fields enabled, child fields disabled (same as 1.5)

---

## SECTION 2: MODULE DROPDOWN DIFFERENCES

### Scenario 2.1 - IT Wing sees ALL option in Module dropdown

> **Login as:** FRAN1875 (ITWNG, MAN, WC 999)

1. Open Menu 998
2. Click the Module dropdown
3. **Expected:** First option is **ALL**, followed by PSR, MTR, LMS, VLP, MAR, CGT, ALC, ALE

---

### Scenario 2.2 - Non-IT Wing does NOT see ALL option

> **Login as:** SOBH2217 (CRWNG, CHM, WC 641)

1. Open Menu 998
2. Click the Module dropdown
3. **Expected:** Dropdown starts with **PSR** (no ALL option). Full list: PSR, MTR, LMS, VLP, MAR, CGT, ALC, ALE

---

## SECTION 3: GO BUTTON VALIDATIONS

### Scenario 3.1 - Go without selecting Module

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Leave Module dropdown empty
3. Click **Go**
4. **Expected:** Error - *"Module - Select Value"*

---

### Scenario 3.2 - Go without entering SOLID/SOLSET

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **MTR**
3. Leave SOLID/SOLSET empty
4. Click **Go**
5. **Expected:** Error - *"SOLID/SOLSET - Enter Value"*

---

### Scenario 3.3 - Go with invalid SOLID

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **MTR**
3. Type **XXXXX** in SOLID/SOLSET
4. Click **Go**
5. **Expected:** Error - *"SOLID/SOLSET - Invalid SOLID"*

---

### Scenario 3.4 - CRM Wing selects Module = ALL

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Open Menu 998
2. Note: ALL should not be in the dropdown. If somehow entered, attempt Go
3. **Expected:** Error - *"Module - ALL is restricted to IT Wing"*

---

### Scenario 3.5 - CRM Wing selects unauthorised module (MTR)

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Open Menu 998
2. Select Module = **MTR**
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:** Error - *"Module - CRM Wing is not authorised for this module"*

> **Also try with modules:** CGT - should also be blocked
>
> **Allowed modules for CRWNG:** PSR, LMS, VLP, MAR, ALC, ALE

---

### Scenario 3.6 - CRM Wing selects authorised module (PSR)

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Open Menu 998
2. Select Module = **PSR**
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:** Form proceeds - Remarks field and Submit become **enabled**, key fields become **disabled**
6. SOL Name field should populate with the name of SOLID 40480

---

### Scenario 3.7 - RO user - Module access blocked for all modules

> **Login as:** ARUN5188 (ROTLY, SEM)

1. Open Menu 998
2. Select any Module (e.g. **MTR**)
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:** Error - *"Module - Regional Office is not authorised for this module"*

> **Try all modules** - PSR, MTR, LMS, VLP, MAR, CGT, ALC, ALE. **All should be blocked for RO users.**

---

### Scenario 3.8 - SOLID/SOLSET = ALL by CRM Wing

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Open Menu 998
2. Select Module = **PSR**
3. Type **ALL** in SOLID/SOLSET
4. Click **Go**
5. **Expected:** Error - *"SOLID/SOLSET - ALL is restricted to IT Wing"*

---

### Scenario 3.9 - SOLID/SOLSET = ALL by IT Wing (allowed)

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **MTR**
3. Type **ALL** in SOLID/SOLSET
4. Click **Go**
5. **Expected:** Form proceeds successfully - child fields enabled

---

### Scenario 3.10 - CRM Wing trying to exempt own SOLID (CRWNG)

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Open Menu 998
2. Select Module = **PSR**
3. Type **CRWNG** in SOLID/SOLSET
4. Click **Go**
5. **Expected:** Error - *"SOLID/SOLSET - Cannot exempt your own SOLID"*

---

### Scenario 3.11 - Successful Go with valid inputs (IT Wing)

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **MTR**
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:**
   - Module dropdown and SOLID/SOLSET field become **disabled**
   - Go button becomes **disabled**
   - SOL Name field shows the name of SOLID 40480
   - Remarks field becomes **enabled**
   - Submit button becomes **enabled**
   - Cancel button remains **enabled**
   - Account Number field should **NOT** be visible

---

### Scenario 3.12 - Go with ALE module shows Account Number field

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **ALE**
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:** Same as 3.11, but additionally an **Account Number** field appears (line 203)

---

### Scenario 3.13 - Go with ALC module does NOT show Account Number field

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Select Module = **ALC**
3. Enter SOLID/SOLSET = **40480**
4. Click **Go**
5. **Expected:** Same as 3.11 - Account Number field should **NOT** be visible (only ALE shows it)

---

## SECTION 4: SUBMIT BUTTON VALIDATIONS

> For all tests in this section, first complete a successful **Go** to enable the Submit button.

### Scenario 4.1 - Submit with empty Remarks

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Leave Remarks **empty**
3. Click **Submit**
4. **Expected:** Error - *"Remarks - Enter Value"*

---

### Scenario 4.2 - Submit with Remarks too short (less than 3 characters)

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Type **AB** in Remarks
3. Click **Submit**
4. **Expected:** Error - *"Remarks - Minimum 3 characters expected"*

---

### Scenario 4.3 - Submit with invalid characters in Remarks

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Type **Test@#$%** in Remarks
3. Click **Submit**
4. **Expected:** Error - *"Remarks - Invalid characters. Only alphanumeric, space, and .,:;-()/ are allowed"*

> **Valid characters:** Letters, numbers, space, and . , : ; - ( ) /

---

### Scenario 4.4 - Submit with Remarks exceeding 100 characters

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Type a very long remark (over 100 characters), e.g.:
   *"This is a very long remark that exceeds the one hundred characters limit to test the maximum length validation"*
3. Click **Submit**
4. **Expected:** Error - *"Remarks - Cannot exceed 100 characters"*

---

### Scenario 4.5 - ALE module Submit without Account Number

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **ALE**, SOLID = **40480**, click **Go**
2. Account Number field should now be visible
3. Type valid Remarks (e.g. *"Testing ALE"*)
4. Leave Account Number **empty**
5. Click **Submit**
6. **Expected:** Error - *"Account Number - Enter Value"*

---

## SECTION 5: SUCCESSFUL SUBMISSIONS

### Scenario 5.1 - Submit MTR exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Enter Remarks = **Testing MTR exemption**
3. Click **Submit**
4. **Expected:** Success message - *"Exempted Day End Checks successfully"*
5. **Verify in DB:**
   - New row in `DAY_END_CHECK_EXEMPT_NEW` with DECE_MODULE = 'MTR', DECE_EXEMPT_SOLSET = '40480'
   - Rows deleted from `DAY_END_CHECK` where DEC_SOLID = '40480' and DEC_REQUIRED_ACTION IN ('MTRIS', 'MTRFS', 'MTRIC', 'MTRFC')

---

### Scenario 5.2 - Submit LMS exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **LMS**, SOLID = **40480**, click **Go**
2. Enter Remarks = **Testing LMS exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for actions: AOP, PAOPP, PEMCV

---

### Scenario 5.3 - Submit VLP exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **VLP**, SOLID = **40499**, click **Go**
2. Enter Remarks = **Testing VLP exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for actions: VLPSU, VLPVP

---

### Scenario 5.4 - Submit PSR exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **PSR**, SOLID = **40425**, click **Go**
2. Enter Remarks = **Testing PSR exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for actions: PSRDS, PSROA

---

### Scenario 5.5 - Submit MAR exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MAR**, SOLID = **40426**, click **Go**
2. Enter Remarks = **Testing MAR exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for actions: MACK, MASU, MAUN, MPUP

---

### Scenario 5.6 - Submit CGT exemption

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **CGT**, SOLID = **40489**, click **Go**
2. Enter Remarks = **Testing CGT exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for action: VP

---

### Scenario 5.7 - Submit ALL module, ALL SOLSET (IT Wing only)

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **ALL**, SOLID = **ALL**, click **Go**
2. Enter Remarks = **Testing ALL exemption**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DAY_END_CHECK deletes for ALL required actions: MTRIS, MTRFS, MTRIC, MTRFC, AOP, PAOPP, PEMCV, VLPSU, VLPVP, PSRDS, PSROA, MACK, MASU, MAUN, MPUP, VP

---

### Scenario 5.8 - Submit by CRM Wing user (allowed module)

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Select Module = **PSR**, SOLID = **40480**, click **Go**
2. Enter Remarks = **CRM Wing PSR test**
3. Click **Submit**
4. **Expected:** Success message
5. **Verify:** DECE_CREATE_SOLID = 'CRWNG', DECE_UUSER = 'SOBH2217'

---

## SECTION 6: ALC AND ALE - API CALL FLOW

These modules trigger an external API call before completing.

### Scenario 6.1 - ALC Submit (first call triggers API)

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **ALC**, SOLID = **40480**, click **Go**
2. Enter Remarks = **Testing ALC postpone**
3. Click **Submit**
4. **Expected:** The system makes an API call (L483 link) with the SOLSET as input
5. **What to watch for:**
   - If API succeeds: *"Exempted Day End Checks successfully"*
   - If API fails: An error message from the API (e.g. *"Connection timeout"*, *"API call failed"*)

---

### Scenario 6.2 - ALE Submit (first call triggers API with Account Number)

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **ALE**, SOLID = **40480**, click **Go**
2. Enter Remarks = **Testing ALE exclude**
3. Enter Account Number = **1234567890**
4. Click **Submit**
5. **Expected:** The system makes an API call (L484 link) with SOLSET^ACCOUNTNO as input
6. **What to watch for:**
   - If API succeeds: *"Exempted Day End Checks successfully"*
   - If API fails: Error message from the API
7. **Verify:** DECE_VALUE1 in DAY_END_CHECK_EXEMPT_NEW should contain the account number

---

### Scenario 6.3 - ALC by CRM Wing (allowed)

> **Login as:** SOBH2217 (CRWNG, CHM)

1. Select Module = **ALC**, SOLID = **40480**, click **Go**
2. Enter Remarks = **CRM ALC test**
3. Click **Submit**
4. **Expected:** API call should trigger (same flow as IT Wing)

---

### Scenario 6.4 - ALE by CRM Wing (allowed)

> **Login as:** HARI6296 (CRWNG, ASM)

1. Select Module = **ALE**, SOLID = **40480**, click **Go**
2. Enter Remarks = **CRM ALE test**
3. Enter Account Number = **5555555555**
4. Click **Submit**
5. **Expected:** API call should trigger (same flow as IT Wing)

---

## SECTION 7: RO-SPECIFIC SOLID RESTRICTIONS

### Scenario 7.1 - RO user trying to exempt their own RO SOLID

> **Login as:** ARUN5188 (ROTLY, SEM)

1. Open Menu 998 (note: RO users are blocked at module level currently, but test the SOLID validation path)
2. Attempt with SOLID = **ROTLY** (their own RO)
3. **Expected:** Error - *"SOLID/SOLSET - Select SOLID under your RO"*

---

### Scenario 7.2 - RO user trying to exempt branch under a different RO

> **Login as:** ARUN5188 (ROTLY, SEM)

1. Attempt with SOLID = **40643** (belongs to ROEKM, not ROTLY)
2. **Expected:** Error - *"SOLID/SOLSET - Select SOLID under your RO"*

---

### Scenario 7.3 - RO user exempting branch under their own RO (would be valid for SOLID check)

> **Login as:** ARUN5188 (ROTLY, SEM)

1. Attempt with SOLID = **40480** (belongs to ROTLY)
2. **Expected:** SOLID validation passes (but module check will block RO users first)

> **Note:** Currently, RO users are blocked at the module level (Scenario 3.7). This scenario would only be reachable if the module restriction is lifted in the future.

---

## SECTION 8: CANCEL BUTTON

### Scenario 8.1 - Cancel resets the form

> **Login as:** FRAN1875 (ITWNG)

1. Select Module = **MTR**, SOLID = **40480**, click **Go**
2. Enter some Remarks
3. Click **Cancel** (instead of Submit)
4. **Expected:**
   - Form resets to initial state
   - Module dropdown and SOLID/SOLSET become **enabled** again
   - Remarks field becomes **disabled/empty** again
   - Submit button becomes **disabled** again
   - No data is inserted into any table

---

## SECTION 9: SEARCH BUTTON (SOL Search)

### Scenario 9.1 - Use search to find a SOLID

> **Login as:** FRAN1875 (ITWNG)

1. Open Menu 998
2. Click the **Search** icon next to SOLID/SOLSET
3. **Expected:** A search popup opens listing SOLIDs with their names
4. Select a SOLID from the list
5. **Expected:** The SOLID/SOLSET field populates with the selected value

---

## QUICK REFERENCE: Module to DEC_REQUIRED_ACTION Mapping

| Module | Actions Deleted from DAY_END_CHECK       |
|--------|------------------------------------------|
| ALL    | MTRIS, MTRFS, MTRIC, MTRFC, AOP, PAOPP, PEMCV, VLPSU, VLPVP, PSRDS, PSROA, MACK, MASU, MAUN, MPUP, VP |
| MTR    | MTRIS, MTRFS, MTRIC, MTRFC              |
| LMS    | AOP, PAOPP, PEMCV                       |
| VLP    | VLPSU, VLPVP                            |
| PSR    | PSRDS, PSROA                            |
| MAR    | MACK, MASU, MAUN, MPUP                  |
| CGT    | VP                                       |
| ALC    | (API call - postpones day end)           |
| ALE    | (API call - excludes permanently)        |

## QUICK REFERENCE: Access Rules

| User Type        | Rule                                        |
|------------------|---------------------------------------------|
| Branch users     | Blocked entirely                            |
| ITWNG            | Only WC 999 allowed                         |
| CRWNG            | Only ASM+ designation allowed               |
| CRWNG            | Modules restricted to: PSR, LMS, VLP, MAR, ALC, ALE |
| CRWNG            | Cannot exempt own SOLID (CRWNG)             |
| CRWNG            | Cannot use SOLSET = ALL                     |
| RO (ASM+)        | Can access menu but blocked at module level |
| RO               | Cannot exempt own RO SOLID                  |
| RO               | Can only exempt branches under their RO     |
| Only ITWNG       | Can use Module = ALL and SOLSET = ALL       |
