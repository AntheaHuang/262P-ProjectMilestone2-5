## Intro for Milestone3

One static method was added inside the XML class:

- `public static JSONObject toJSONObject(Reader reader, Function<String, String> keyTransformer) `

The method used a modified parse methods to achieve its function:

- `parseForTransformKey(XMLTokener x, JSONObject context, String name, XMLParserConfiguration config, int currentNestingDepth, Function<String,String> keyTransformer)`

To test the newly written method, 5 test cases were added inside the XMLTest.java, which names followed the naming convention of the original test cases:

- `shouldHandleAddPrefixToKey()`
- `shouldHandleReverseKey()`
- `shouldHandleUppercaseKey()`
- `shouldHandleEmptyNewKey()`
- `shouldHandleNullTransformationFunc()`.

To build the whole project and run all the test cases, run:

- `mvn clean`
- `mvn compile`
- `mvn test`

To run single test case, use the following command under the root file (method name after # can be changed):  
`mvn test -Dtest=org.json.junit.XMLTest#shouldHandleAddPrefixToKey`

Comparison for Performance:

- Transform keys in client code as in Milestone 1:
  - Step A: Convert the XML into JSONObject;
  - Step B: Go through the JSONObject and transform the keys.
- Transform keys inside the library:
  - Only 1 step is needed: When converting the XML into JSONObject, the transformed keys would be directly put into the JSONObject.

Thus, doing so inside the library has a better performance.
