## Intro for Milestone5

One static method was added inside the XML class:

- `public static void toJSONObject(Reader reader, Consumer<JSONObject> onSuccess, Consumer<Exception> onError) `

The method aims at making the converting process asynchronously, allowing the client code to proceed during the conversion.

To test the newly written method, 3 test cases were added inside the XMLTest.java, which names followed the naming convention of the original test cases:

- `shouldHandleAsyncXMLToJSON()`
- `shouldHandleAsyncTransformKeyAfterwards()`
- `shouldHandleAsyncFailure()`.

To build the whole project and run all the test cases, run:

- `mvn clean`
- `mvn compile`
- `mvn test`

To run single test case, use the following command under the root file (method name after # can be changed):  
`mvn test -Dtest=org.json.junit.XMLTest#shouldHandleAsyncXMLToJSON`
