Based on your Locality List and Address List, you want to identify if any locality (even partially) appears in each address. Here’s how to set this up in Excel:

Locality List: This is your list of localities, as shown in the image (let’s assume it’s in Sheet2!A2
).
Address List: This is where you have the addresses you want to check, let's say in Sheet1, Column A.
Formula
In Sheet1, where your address list is, enter the following formula in B2 (next to your first address) and drag it down for all addresses:

excel
Copy code
=IFERROR(TEXTJOIN(", ", TRUE, FILTER(Sheet2!A$2:A$25, ISNUMBER(SEARCH(Sheet2!A$2:A$25, A2)), "No Match")), "No Match")
Explanation
SEARCH(Sheet2!A$2
$25, A2):

This searches for each locality in Sheet2!A$2
$25 within the address in A2.
SEARCH returns a number if it finds the locality (even partially) in the address. If not, it returns an error.
ISNUMBER(...):

Converts the output of SEARCH into TRUE or FALSE for each locality.
Returns TRUE if a locality is found in the address, FALSE if not.
**FILTER(Sheet2!A$






