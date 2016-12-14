#BrainScan Utility Library - Reference Documentation

**brainutility.lib** contains many function useful in many situations, and is recommended for use on all WebDNA pages.

All functions and global variables defined in the brainutility.lib begin with the prefix "but", short for brainutility.

###Formatting
The code style guidelines used here include the following:
- Global identifiers intended for public use begin with "but"
- Global identifiers intended for private use within the library begin with "_but"
- Local text variable name begin with a lowercase "t", followed by a camel-case descriptive name
- If the value of a text variable has been URL'ed, the variable name begins with a "u" instead of the "t"
- Local math variables begin with "m"

Within the documentation, required function parameters are **bold**, and optional parameters are *italicised*. A parameter shown in (parentheses) is "direct" or unnamed parameter (e.g. [myFunction anUnnamedParameterValue]). In some cases a parameter may be either named or direct, with naming required if additional optional parameters are passed in.

___
##Table of Contents
<table><tr><td>
<a href="#butTrue">butTrue</a><br />
<a href="#butFalse">butFalse</a><br />
<a href="#butVersion">butVersion</a><br />
<a href="#butFunctions">butFunctions</a><br />
<a href="#butFunctionParam">butFunctionParam</a><br />
<a href="#butFunctionParamList">butFunctionParamList</a><br />
<a href="#butLineEnder">butLineEnder</a><br />
<a href="#butMin">butMin</a><br />
<a href="#butMax">butMax</a><br />
<a href="#butInc">butInc</a><br />
<a href="#butDec">butDec</a><br />
<a href="#butExponent">butExponent</a><br />
<a href="#butRound">butRound</a><br />
<a href="#butRandom">butRandom</a><br />
<a href="#butGetWebDNAPref">butGetWebDNAPref</a><br />
<a href="#butDefaultValue">butDefaultValue</a><br />
<a href="#butEndsWith">butEndsWith</a><br />
<a href="#butTrim">butTrim</a><br />
<a href="#butShowHTML">butShowHTML</a><br />
<a href="#butElapsedTime">butElapsedTime</a><br />
<a href="#butSortList">butSortList</a><br />
</td><td>
<a href="#butPassword">butPassword</a><br />
<a href="#butWeekdayOffset">butWeekdayOffset</a><br />
<a href="#butDaysToDate">butDaysToDate</a><br />
<a href="#butSecondsToTime">butSecondsToTime</a><br />
<a href="#butIsDefined">butIsDefined</a><br />
<a href="#butNotDefined">butNotDefined</a><br />
<a href="#butIsTextVar">butIsTextVar</a><br />
<a href="#butIsMathVar">butIsMathVar</a><br />
<a href="#butIsFormVar">butIsFormVar</a><br />
<a href="#butIsNumeric">butIsNumeric</a><br />
<a href="#butIsInteger">butIsInteger</a><br />
<a href="#butIsLower">butIsLower</a><br />
<a href="#butIsUpper">butIsUpper</a><br />
<a href="#butIsEmpty">butIsEmpty</a><br />
<a href="#butIsFile">butIsFile</a><br />
<a href="#butIsFolder">butIsFolder</a><br />
<a href="#butExactMatch">butExactMatch</a><br />
<a href="#butIDTagComponents">butIDTagComponents</a><br />
<a href="#butCapitalize">butCapitalize</a><br />
<a href="#butSplitMixedCaseWord">butSplitMixedCaseWord</a><br />
<a href="#butTextSet">butTextSet</a><br />
</td><td>
<a href="#butMathSet">butMathSet</a><br />
<a href="#butArraySet">butArraySet</a><br />
<a href="#butHost">butHost</a><br />
<a href="#butMIMEDate">butMIMEDate</a><br />
<a href="#butCookieExpire">butCookieExpire</a><br />
<a href="#butCookieDomain">butCookieDomain</a><br />
<a href="#butSiteRoot">butSiteRoot</a><br />
<a href="#butThisPage">butThisPage</a><br />
<a href="#butListToArray">butListToArray</a><br />
<a href="#butUpdateList">butUpdateList</a><br />
<a href="#butListContainsItem">butListContainsItem</a><br />
<a href="#butAuthorizeNet">butAuthorizeNet</a><br />
<a href="#butTCPFetch">butTCPFetch</a><br />
<a href="#butToday">butToday</a><br />
<a href="#butNow">butNow</a><br />
<a href="#butShowNonBlank">butShowNonBlank</a><br />
<a href="#butAddressFormat">butAddressFormat</a><br />
<a href="#butPhoneFormat">butPhoneFormat</a><br />
<a href="#butAge">butAge</a><br />
<a href="#butZip">butZip</a><br />
<a href="#butLoadRecord">butLoadRecord</a><br />
</td><td>
<a href="#butFedExLink">butFedExLink</a><br />
<a href="#butFedExTracking">butFedExTracking</a><br />
<a href="#butUPSLink">butUPSLink</a><br />
<a href="#butShippingLink">butShippingLink</a><br />
<a href="#butTextMap">butTextMap</a><br />
<a href="#butTextMapRaw">butTextMapRaw</a><br />
<a href="#butHTMLMap">butHTMLMap</a><br />
<a href="#butHTMLNoBreakMap">butHTMLNoBreakMap</a><br />
<a href="#butISO">butISO1Map</a><br />
<a href="#butUTF">butUTF8Map</a><br />
<a href="#butEntityMap">butEntityMap</a><br />
<a href="#butEditMap">butEditMap</a><br />
<a href="#butAsciiCodeMap">butAsciiCodeMap</a><br />
<a href="#butSmartMap">butSmartMap</a><br />
<a href="#butShortenString">butShortenString</a><br />
<a href="#butGetWord">butGetWord</a><br />
<a href="#butCountOccurrences">butCountOccurrences</a><br />
<a href="#butWordList">butWordList</a><br />
<a href="#butFileSize">butFileSize</a><br />
<a href="#VersionHistory">Version History</a><br />
</td></tr></table>

___
##<a name="butTrue">butTrue</a> and <a name="butFalse">butFalse</a>

These are global text variables defined to improve the readability of conditional expressions. They are defined as:

	[text]butTrue=1=1[/text]
	[text]butFalse=1=0[/text]

These values evaluate TRUE or FALSE in an [if], [showif] or [hideif] expression, and can be used to make code much more readable. For example, if the variable "tDoTheThing" is set to [butTrue] or to [butFalse] depending on an earlier logic decision, then you can have an expression like:

	[if [tDoTheThing]][then] (do it) [then][else] (don't do it) [/else][/if]

or

	[showif [tDoTheThing]] (do it) [/showif]

###Example
Given an email address in [tEmail], search your member.db database for that member then set a flag indicating whether a the member's status flag is set to "Active":

	[text]tActive=[butFalse][/text]
	[search db=/db/member.db&eqmemEmaildatarq=[url][tEmail][/url]][founditems]
	  [showif [memStatus]=Active][text]tActive=[butTrue][/text][/showif]
	[/founditems][/search]

Later in the page, you can then reference the tActive variable to determine what message to show the user:

	[if [tActive]][then]
	  [tEmail] is an active member.
	[/then][else]
	  [tEmail] is NOT an active member.
	[/else][/if]

###Why This Works
When WebDNA processes the "[if [tActive]]" statement, it first substitutes "[tActive]" with the stored value of the text variable named tActive, resulting in "[if 1=1]" or "[if 1=0]", depending on whether tActive was set to butTrue or butFalse. WebDNA then interprets the post-substitution statement and executes either the [then] clause or the [else] clauses.

These same values also work in the [showif], [hideif] and [switch] contexts.

___
##<a name="butVersion">butVersion</a>
This is a global text variable that indicates the version of the brainutility.lib that has been included.

___
##<a name="butFunctions">butFunctions</a>
Returns a list of the functions defined in the included brainutility.lib, each on a new line.

___
##<a name="butFunctionParam">butFunctionParam</a>
Get the value of an optional parameter to a function


Get the value of an optional parameter to a function

###Input
- **name**	- Name of the parameter
- **params**	- The params_string from the calling function
- *default*	- Default value if not found, optional, defaults to nothing
- *trim*	- T or F (default) - Trim whitespace from value?
	
###Output
- The value of the named parameter if found, otherwise the default value

###Discussion
When writing custom functions intended for multiple use cases, there is often a great benefit to allowing for optional parameters. For example, this function itself has two optional parameters - *default* can be used to specify the values for parameters that are not passed in if something other than a blank value is desired, and *trim* provides the option to ignore leading and trailing spaces in the parameter value.

The `butFunctionParam` function provides a convenient way to implement optional parameters in your custom function.

###Example
This function tests whether the given *number* is a numeric value, and optionally requires that it is less than a *minimum* value. If no *minumum* parameter is given, it requires a minimum of zero:

	[function name=validNumber]
		[text]uParams=[url][params_string][/url][/text]
		[text]tNumber=[butFunctionParam name=number&params=[uParams]&default=MISSING&trim=T][/text]
		[text]tMinimum=[butFunctionParam name=minimum&params=[uParams]&default=0&trim=T][/text]
		[if "[math][tNumber][/math]"="[tNumber]"][then]
			[if [tNumber]<[tMinimum]][then]
				[return][butFalse][/return]
			[/then][else]
				[return][butTrue][/return]
			[/else][/if]
		[/then][else]
			[return][butFalse][/return]
		[/else][/if]
	[/function]

	[validNumber] returns [butFalse] because no `number` was passed in
	[validNumber number=13] returns [butTrue] because `number` contains a number and it's not less than the default minumum of zero<br>
	[validNumber number=-1] returns [butFalse] because `number` is less than the default minimum of zero<br>
	[validNumber number=13&minimum=10] returns [butTrue] because `number` contains a number and it's not less than the specified minimum of 10<br>
	[validNumber number=13&minimum=20] returns [butFalse] because `number` contains a number and it's  less than the specified minimum of 20<br>
	[validNumber number=-1&minimum=-10] returns [butTrue] because `number` contains a number and it's not less than the specified minimum of -10<br>

###Why This Works
There is a minimally documented system tag called `params_string` that is available inside a function, containing the full parameter string passed in to the function. So, if you call `[mufunction a=1&b=2\`, then `[params_string]` will have the value "`a=1&b=2`". The `butFunctionParam` function looks at `params_string` to see if it contains the requested parameter name, and returns it's value if found or the default value if it's not found.

___
##<a name="butFunctionParamList">butFunctionParamList</a>
Return a comma-delimited list of parameter names passed in to a function

###Input
- **(params_string)**	- The params_string from the calling function
	
###Output
- Comma-delimited list of the names of the parameters in params_string
- If no named variables but non-blank, returns, literally, "params_string"

###Discussion
This function allows for the creation of very flexible functions that can operate on any number of parameters without pre-defining the names of those parameters.

###Example:
This function will update a record in the member.db with the values passed in, adding a "mem" prefix to the field name if not provided (so you could pass in "FirstName" or "memFirstName" and both would map to the "memFirstName" field in the member.db).

	[function name=memberUpdate]
		[text]tParamList=[butFunctionParamList [params_string]][/text]
		[text]uParams=[url][params_string][/url][/text]
		[text]tMemID=[butFunctionParam name=ID&params=[uParams]&default=NO_ID][/text]
		[if "[tMemID]"="NO_ID"][then]
			[return][butFalse][/return]
		[/then][else]
			[text]tData=[/text]
			[listwords words=[tParamList]]
				[text]uValue=[url][butFunctionParam name=[word]&params=[uParams]&trim-T][/url][/text]
				[text]tData=[tData]&[hideif [word]~mem]mem[/hideif][word]=[uValue][/text]
			[/listwords]
			[replace db=/db/member.db&eqmemIDdatarq=[tMemID]]memModDate=[butToday]&memModTime=[butNow][tData][/replace]
			[return][butTrue][/return]
		[/else][/if]
	[/function]

___
##<a name="butLineEnder">butLineEnder</a>
Returns un-URL'ed %0D, %0A or %0D%0A depending on the server OS. This is particularly useful when building email messages to send with WebDNA's `[sendmail]` context.

###Input
- *System*	- UNIX, MAC or WINDOWS. If not specified, the [platform] tag is used to determine the system.
	
###Output
- UNURL'ed value of one of the following:
		%0D	on Classic Mac OS (it's an old old function)
		%0A on Unix / MacOS X
		%0D%0A on Windows

___
##<a name="butMin">butMin</a>
Returns lesser of multiple listed values

###Input
- **ValueList** or direct param	-	The List of values to find the minimum of (required)
- Alpha		-	T for alphabetic minimum, F for numeric (optional, assumes F)
- Delimiters	-	Delimiters for listwords on the passed-in ValueList (optional, assumes WebDNA default delimters)

Output:
	The minimum value from the given list

Calling conventions:
[raw]
	[text]tMin=[butMin ValueList=[url][val1],[val2],[val3],...[/url]...][/text]
[/raw]

___
##<a name="butMax">butMax</a>
Returns greater of listed values

___
##<a name="butInc">butInc</a>
Increment a global variable

___
##<a name="butDec">butDec</a>
Decrement a global variable

___
##<a name="butRandom">butRandom</a>
Random with easier controls

___
##<a name="butGetWebDNAPref">butGetWebDNAPref</a>
Get the value of a WebDNA preference field

___
##<a name="butDefaultValue">butDefaultValue</a>
Returns given value if it is not blank, default value if it is

___
##<a name="butTrim">butTrim</a>
Trim returns and leading tabs and spaces from each line passed in

___
##<a name="butShowHTML">butShowHTML</a>
Maps < to &lt; and > to &gt; so HTML is visible instead of interpreted

___
##<a name="butElapsedTime">butElapsedTime</a>
Elapsed time, expressed in hours, minutes, seconds

___
##<a name="butSortList">butSortList</a>
Returns sorted list of passed-in values

___
##<a name="butPassword">butPassword</a>
Returns an algorithmically generated password

___
##<a name="butWeekdayOffset">butWeekdayOffset</a>
Calculates a number of weekdays offset from specified date

___
##<a name="butDaysToDate">butDaysToDate</a>
Formats a Days Since value as a user-readable date

___
##<a name="butSecondsToTime">butSecondsToTime</a>
Formats a Seconds Since value as a user-readable time

___
##<a name="butIsDefined">butIsDefined</a>
Returns butTrue if given name is a defined tag or variable, else butFalse

___
##<a name="butNotDefined">butNotDefined</a>
Returns butTrue if given name is NOT a defined tag or variable, else butFalse

___
##<a name="butIsTextVar">butIsTextVar</a>
Returns butTrue if given name is a defined text variable, else butFalse

___
##<a name="butIsMathVar">butIsMathVar</a>
Returns butTrue if given name is a defined math variable, else butFalse

___
##<a name="butIsFormVar">butIsFormVar</a>
Returns butTrue if given name is a defined form variable, else butFalse

___
##<a name="butIsNumeric">butIsNumeric</a>
Returns butTrue if given value is numeric, else butFalse

___
##<a name="butIsInteger">butIsInteger</a>
Returns butTrue if given value is an integer, else butFalse

___
##<a name="butIsLower">butIsLower</a>
Returns butTrue if given value contains no upper-case characters

___
##<a name="butIsUpper">butIsUpper</a>
Returns butTrue if given value contains no lower-case characters

___
##<a name="butIsEmpty">butIsEmpty</a>
Returns butTrue if given variable has blank value, else butFalse

___
##<a name="butIsFile">butIsFile</a>
Returns butTrue if given path represents an existing file, else butFalse

___
##<a name="butIsFolder">butIsFolder</a>
Returns butTrue if given path represents an existing folder, else butFalse

___
##<a name="butExactMatch">butExactMatch</a>
Returns butTrue if values pass case-sensitive comparison

___
##<a name="butIDTagComponents">butIDTagComponents</a>
Break an ID tag value into prefix, number and suffix

___
##<a name="butCapitalize">butCapitalize</a>
Capitalize text, but only if all caps or all lowercase

___
##<a name="butSplitMixedCaseWord">butSplitMixedCaseWord</a>
Break up mixed case word into separate capitalized words

___
##<a name="butTextSet">butTextSet</a>
Set a text variable

___
##<a name="butMathSet">butMathSet</a>
Set a text variable with a math expression

___
##<a name="butArraySet">butArraySet</a>
Set an indexed array value

___
##<a name="butHost">butHost</a>
Returns the host name, extracted from MIME headers

___
##<a name="butMIMEDate">butMIMEDate</a>
Returns MIME-compatible date, calculated with offsets from current date/time

___
##<a name="butCookieExpire">butCookieExpire</a>
Returns date/time formatted for SetCookie tag

___
##<a name="butCookieDomain">butCookieDomain</a>
Returns the domain name for this site for a SetCookie tag (eg. ".mysite.com")

___
##<a name="butSiteRoot">butSiteRoot</a>
Returns relative path to site root (eg. "../../")

___
##<a name="butThisPage">butThisPage</a>
Returns the name of the current page (stripped from thisurl)

___
##<a name="butListToArray">butListToArray</a>
Returns contents of list formatted for populating an array

___
##<a name="butUpdateList">butUpdateList</a>
Add or remove items from a delimited list of values

___
##<a name="butListContainsItem">butListContainsItem</a>
Look for one or more items in a delimited list of values

___
##<a name="butListPosition">butListPosition</a>
Return position of a value in a delimited list of values

___
##<a name="butAuthorizeNet">butAuthorizeNet</a>
Posts a transaction to Authorize.Net via its AIM protocol

___
##<a name="butTCPFetch">butTCPFetch</a>
Gets content from a web page via TCPConnect

___
##<a name="butToday">butToday</a>
Current date, numeric or formatted

___
##<a name="butNow">butNow</a>
Current time, numeric or formatted

___
##<a name="butShowNonBlank">butShowNonBlank</a>
Show value with prefix and suffix if value is not blank

___
##<a name="butAddressFormat">butAddressFormat</a>
Format parameters as an address (U.S.)

___
##<a name="butPhoneFormat">butPhoneFormat</a>
Format value as a phone number

___
##<a name="butAge">butAge</a>
Determine an age based on the date of birth and the current or specified date

___
##<a name="butZip">butZip</a>
Use shell "zip" command to create an archive of one or more files

___
##<a name="butLoadRecord">butLoadRecord</a>
Search for a record and store its fields in global text variables

___
##<a name="butFedExLink">butFedExLink</a>
Return URL for shipment tracking via FedEx

___
##<a name="butFedExTracking">butFedExTracking</a>
Fetch FedEx Tracking status information and store into global text variables

___
##<a name="butUPSLink">butUPSLink</a>
Return URL for shipment tracking via UPS

___
##<a name="butShippingLink">butShippingLink</a>
Determines shipping company and returns URL for tracking

___
##<a name="butTextMap">butTextMap</a>
Map as text, html code shows on the page

___
##<a name="butTextMapRaw">butTextMapRaw</a>
Map as text, just converting line enders and tabs

___
##<a name="butHTMLMap">butHTMLMap</a>
Map as HTML, adding line breaks at returns

___
##<a name="butHTMLNoBreakMap">butHTMLNoBreakMap</a>
Map as HTML, no added line breaks

___
##<a name="butISO">butISO1Map</a>

___
##<a name="butUTF">butUTF8Map</a>

___
##<a name="butEntityMap">butEntityMap</a>

___
##<a name="butEditMap">butEditMap</a>

___
##<a name="butAsciiCodeMap">butAsciiCodeMap</a>

___
##<a name="butSmartMap">butSmartMap</a>
Map text for display from database, intelligently choosing whether to map HTML and line breaks

___
##<a name="butShortenString">butShortenString</a>
Show part of a string with inserted ellipsis

___
##<a name="butGetWord">butGetWord</a>
Get word at specified index from a string

___
##<a name="butCountOccurrences">butCountOccurrences</a>

___
##<a name="butWordList">butWordList</a>
* SEE butUpdateList *

___
##<a name="butFileSize">butFileSize</a>
Convert Bytes to friendly view - KB, MB, GB, TB


___
##<a name="VersionHistory">Version History</a>
	Version		Date		Who				Changes
				27Jan2004	Brian Fries		Initial development
				06Feb2004	Brian Fries		Added butInc and butElapsedTime functions
				24Mar2004	Brian Fries		Added butVersion and butFunctions functions
				19May2004	Brian Fries		Added butDaysToDate and butSecondsToTime functions
				21May2004	Brian Fries		Added butIsDefined, butIsTextVar, butIsMathVar, butIsFormVar
				25May2004	Brian Fries		Added butIsNumeric, butCookieExpire, butCookieDomain, butSiteRoot, butThisPage
				26May2004	Brian Fries		Added butListToArray
				28May2004	Brian Fries		Added butAuthorizeNet
				31May2004	Brian Fries		Added WebDNA version test in butListToArray to avoid crashing bug (blank array value)
				18Jun2004	Brian Fries		Added butTrim
				27Jun2004	Brian Fries		Added butHost
				01Jul2004	Brian Fries		Added butTCPFetch, butShowHTML, butMIMEDate
				09Jul2004	Brian Fries		Added butIsEmpty
				01Oct2004	Brian Fries		Added butTextSet, butMathSet, butArraySet, loaded toggle variable
				08Oct2004	Brian Fries		Added butToday, butNow
				14Oct2004	Brian Fries		Support direct parameter with default format to butDaysToDate and butSecondsToTime
				19Oct2004	Brian Fries		Added butPhoneFormat, define butTrue and butFalse
				25Oct2004	Brian Fries		Support butPhoneFormat on WebDNA 5 (no listchars)
				01Nov2004	Brian Fries		Added %0B and %1D to butTrim characters
				08Nov2004	Brian Fries		Added butAge function
				19Nov2004	Brian Fries		Added butIsInteger function
				20Dec2004	Brian Fries		Fixed syntax error in butPhoneFormat
				18Jan2005	Brian Fries		Added butIsFile and butIsFolder functions; use :local: in referencing parameters
				24May2005	Brian Fries		Eliminate confusing characters from butPassword generator (l1IO0); Add butZip
				25May2005	Brian Fries		Fixed butZip to work on systems without Absolute Path prefix (*) enabled 
				29Jun2005	Brian Fries		Set butValue global from butIsDefined, butIsTextVar, butIsMathVar and butIsFormVar
				08Sep2005	Brian Fries		Added "Friendly" parameter to butDaysToDate (strip leading zeroes from %d and %m values)
				25Oct2005	Brian Fries		Added "Friendly" parameter to butToday (use butDaysToDate)
				07Nov2005	Brian Fries		Fixed Friendly dates when %d or %m starts the format string; Cleaner handling of friendly param to butToday with no dateformat param;
											Added Friendly and Lower params to butNow and butSecondsToTime (strip zeroes from %I values; lowercase am/pm)
				02Mar2006	Brian Fries		Added butLoadRecord, butIsLower, butIsUpper, butExactMatch
				04May2006	Brian Fries		Added butFedExLink
				06Jun2006	Brian Fries		Added butCapitalize
				21Jun2006	Brian Fries		Added butDec
				03Mar2007	Brian Fries		Added butTextMap, butHTMLMap, butHTMLNoBreakMap and butSmartMap
				16Mar2007	Brian Fries		Added butRandom
				14Dec2007	Brian Fries		Added butFedExTracking
				17Dec2007	Brian Fries		Bug fix in butFedExTracking
				12Jan2008	Brian Fries		Added _butTimePatch to fix seconds_to_time but in Linux version
				04Apr2008	Brian Fries		Added butNotDefined
				23May2008	Brian Fries		New URL for to butFedExTracking; added sanity checks
				04Feb2009	Brian Fries		Updated butFedExTracking for new FedEx page layout
				09Apr2010	Brian Fries		Fixed "max" bug in butRandom
											Added butShortenString
	01.00.00b19	09Dec2010	Brian Fries		Added butEndsWith
	01.00.00b20	20Sep2011	Brian Fries		Added butSpellNumber
	01.00.00b21	21Sep2011	Brian Fries		Add www. prefix to fedex.com links
	01.00.00b22	06Mar2012	Brian Fries		Add butFunctionParam, butFunctionParamList
	01.00.00b23	12Mar2012	Brian Fries		Enhanced butTrim to strip trailing whitespace from each line
	01.00.00b24	20Mar2012	Brian Fries		Add butShowNonBlank, butAddressFormat, Changed butVersion to a text var
	01.00.00b25	28Mar2012	Brian Fries		Support <br /> in butSmartMap
	01.00.00b26	29Mar2012	Brian Fries		Add butTextMapRaw
	01.00.00b27	23Apr2012	Brian Fries		Add butDefaultValue
	01.00.00b28	03May2012	Brian Fries		Added butGetWord
	01.00.00b29	16May2012	Brian Fries		Added butWeekdayOffset
	01.00.00b30	05Jun2012	Brian Fries		Added &eacute; to text conversions
	01.00.00b31	12Jun2012	Brian Fries		Added "break" parameter to butAddressFormat; Use <br /> throughout
	01.00.00b32	25Jun2012	Brian Fries		Added butUpdateList
				26Jul2012	Rob Freiburger	Added butUPSLink
				26Jul2012	Rob Freiburger	Added butShippingLink
	01.00.00b33	14Aug2012	Brian Fries		Added butFileSize
	01.00.00b34	06Nov2012	Brian Fries		Fixed butTCPFetch to include trailing slash if provided
	01.00.00b35	29Nov2012	Brian Fries		Fixed butAddressFormat to add line break between street and city
	01.00.00b36	18Dec2012	Brian Fries		Added and used butGetWebDNAPref, supporting both WebCatalog Prefs and webdna.ini
											Updated butFunctionParam for WebDNA 7 compatibility (can't use defined keywords like "default" as parameters)
											... Probably gonna need more work along these lines
											Converted to TEXT encapsulation instead of comments
	01.00.00b37	16Jan2013	Brian Fries		Added POST support to butTCPFetch
	01.00.00b38	19Jan2013	Brian Fries		Added butWordList
	01.00.00b39	26Feb2013	Brian Fries		Added butExponent, butRound
	01.00.00b40	10Apr2013	Brian Fries		Added butISO1Map, butUTF8Map, butEntityMap, butEditMap, butAsciiCodeMap, butCountOccurrences
	01.00.00b41	19Jan2013	Brian Fries		Added butListContainsItem
	01.00.00b42	26Jun2013	Brian Fries		Added TRIM parameter to butFunctionParam
	01.00.00b43	13Jan2014	Brian Fries		Accept item as synonym for items in butListContainsItem
											Added butListPosition
	01.00.00b44	04Feb2014	Brian Fries		50% faster version of butFunctionParam
	01.00.00b45	19Feb2014	Brian Fries		Added butSplitMixedCaseWord
	01.00.00b46	21Feb2014	Brian Fries		Fixed butSplitMixedCaseWord to keep runs of caps together
	01.00.00b47	05Mar2014	Brian Fries		Fixed trim param broken in rewrite of butFunctionParam
	01.00.00b48	16Sep2014	Brian Fries		FedExLink uses comma instead of %0D%0A as delimiter now
	01.00.00b49	14Oct2014	Brian Fries		Added butCSVValue; make butPhoneFormat default to 3-4 format if exactly 7 characters passed in
	01.00.00b50	15Jan2015	Brian Fries		Added butIDTagComponents
	01.00.00b51	17Jan2015	Brian Fries		Added special characters butVLF, butCR, butLF, butTab, butVTB
											Fixed butTrim to not unurl parameter unless it contains a % - because [unurl]+[/unurl] maps to a space
	01.00.00b52	07Jan2016	Brian Fries		Added curly quotes to butEntityTable; Map %u201D to right double curly quote
	01.00.00b53	07Jun2016	Brian Fries		Fixed reference to "delimiter" parameter in butListContainsItem
											Cleaned up some code to pass syntax check
	01.00.00b54	11Aug2016	Brian Fries		Added USPS and DHL support to butShippingLink; also added carrier parameter
	01.00.00b55	11Aug2016	Brian Fries		Accept "delimiter" or "delimiters" parameters interchangeably throughout
	01.00.00b56	22Sep2016	Brian Fries		Rewrote butFunctionParam to support WebDNA 8+, which didn't like the "default" parameter
	01.00.00	13Dec2016	Brian Fries		Adapted for public use and released to Github
