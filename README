# JSON Java fork

This is a fork of the original JSON Java implementation made by Douglas Crockford.

## Enhancements

With this fork it is possible to find an object or type using a path to the type instead of just a key.
This gives means to find a single string from a complex JSON structure in just one line.
The nodes are separated with a (dot) and array index surrounded by square braces.
The array selection can even be an expression giving the possibility to find a particular object and
a type within.

## Example

For all examples below this is the JSON we are using and it is parsed into a JSONObject called jsonObject:

	{
		"array": [
			{
				"id": 12, 
				"address": {
					"zip": 12345
				}, 
				"name": "value1"
			}, 
			{
				"id": 2, 
				"name": "value2"
			}, 
			{
				"id": 1, 
				"address": {
					"zip": 45678
				}, 
				"name": "value3"
			}
		]
	}
 
#### Find the name of the first object in the array

	String name = jsonObject.getString("array[0].name");
	
_Name contains "value1" after the statement has been run._
	
#### Find the id of the third object

	int id = jsonObject.getInt("array[2].id");
	
_The variable id contains 1 after this statement._

#### Find the name of the first object which address zip code is larger than 20000

	String name = jsonObject.getString("array[address.zip>20000].name");
	
_Name contains "value3" after the statement has been run._

#### Find the name of the first found object that has a zip code not equal to 12345
	
	String name = jsonObject.getString("array[address.zip!=12345].name");

_Name contains "value3" after the statement has been run._

#### Find the name of the object in the array which id equals 2

	String name = jsonObject.getString("array[id==2].name");



## Possible operands to use in array object selections

In case of arrays this syntax can be used:

`jsonObject.getString("first[element**operand**value].second[element.element**operand**value].string");`

These test operands can be used:

	== : Equality test
	!= : Not equal test
	 < : Less than test
	 > : Greater than test
	<= : Less than or equal test
	>= : Greater than or equal test
	*= : Contains text test
	!* : Not contains text test
	^= : Starts with text test
	!^ : Not starts with text test
	$= : Ends with text test
	!$ : Not ends with text test

The value used after the operand can have the pipe (|) character to separate several alternatives. 
Maybe this doesn't make sense with the comparators <, >, <=, >=, ^= and $= but for the others
it's a quite neat feature.

#### Find the id of the object that doesn't have the name value1 or value3

	int id = jsonObject.getInt("array[name!=value1|value3].id");
	
_The variable id contains 2 after this statement._

#### Find the name of the object that doesn't have the id 1 or 2

	String name = jsonObject.getString("array[id!=1|2].name");
	
_The variable name contains value1 after this statement._


## What if the JSON keys contains dot or brackets

Some times you could come across JSON data which has keys that contains a dot or brackets.
You can solve that by using the new setter for the path search specific characters:

	jsonObject.setSearchByPathChars('/', '{', '}');
	String name = jsonObject.getString("array{id!=1|2}/name");

_The characters can be changed to any valid chars_

#### This is for instance a valid case
The only important thing to know is that the characters you choose does not exist in any key and that they has to be different from each other.

    jsonObject.setSearchByPathChars('§', '`', '\'');
    String value = jsonObject.getString("array.json`0'§crazy{}/key");








# Original Douglas Crockford README

	JSON in Java [package org.json]
	
	Douglas Crockford
	douglas@crockford.com
	
	2011-02-02
	
	
	JSON is a light-weight, language independent, data interchange format.
	See http://www.JSON.org/
	
	The files in this package implement JSON encoders/decoders in Java.
	It also includes the capability to convert between JSON and XML, HTTP
	headers, Cookies, and CDL.
	
	This is a reference implementation. There is a large number of JSON packages
	in Java. Perhaps someday the Java community will standardize on one. Until
	then, choose carefully.
	
	The license includes this restriction: "The software shall be used for good,
	not evil." If your conscience cannot live with that, then choose a different
	package.
	
	The package compiles on Java 1.2 thru Java 1.4.
	
	
	JSONObject.java: The JSONObject can parse text from a String or a JSONTokener
	to produce a map-like object. The object provides methods for manipulating its
	contents, and for producing a JSON compliant object serialization.
	
	JSONArray.java: The JSONObject can parse text from a String or a JSONTokener
	to produce a vector-like object. The object provides methods for manipulating
	its contents, and for producing a JSON compliant array serialization.
	
	JSONTokener.java: The JSONTokener breaks a text into a sequence of individual
	tokens. It can be constructed from a String, Reader, or InputStream.
	
	JSONException.java: The JSONException is the standard exception type thrown
	by this package.
	
	
	JSONString.java: The JSONString interface requires a toJSONString method,
	allowing an object to provide its own serialization.
	
	JSONStringer.java: The JSONStringer provides a convenient facility for
	building JSON strings.
	
	JSONWriter.java: The JSONWriter provides a convenient facility for building
	JSON text through a writer.
	
	
	CDL.java: CDL provides support for converting between JSON and comma
	delimited lists.
	
	Cookie.java: Cookie provides support for converting between JSON and cookies.
	
	CookieList.java: CookieList provides support for converting between JSON and
	cookie lists.
	
	HTTP.java: HTTP provides support for converting between JSON and HTTP headers.
	
	HTTPTokener.java: HTTPTokener extends JSONTokener for parsing HTTP headers.
	
	XML.java: XML provides support for converting between JSON and XML.
	
	JSONML.java: JSONML provides support for converting between JSONML and XML.
	
	XMLTokener.java: XMLTokener extends JSONTokener for parsing XML text.
