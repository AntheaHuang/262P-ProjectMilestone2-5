## Intro for Milestone2

Two static methods were added inside the XML class:

- `public static JSONObject toJSONObject(Reader reader, JSONPointer path)`
- `public static JSONObject toJSONObject(Reader reader, JSONPointer path, JSONObject replacement)`

These two methods used two modified parse methods to achieve their functions respectively:

- `parseForExtract(XMLTokener x, JSONObject context, String name, XMLParserConfiguration config, int currentNestingDepth, JSONPointer path, String currPath)`
- `parseForReplace(XMLTokener x, JSONObject context, String name, XMLParserConfiguration config, int currentNestingDepth, JSONPointer path, String currPath, JSONObject replacement)`

To test the newly written method, 5 test cases were added inside the XMLTest.java, which names followed the naming convention of the original test cases:

- `shouldHandleExtractNestedObject()`
- `shouldHandleExtractSimpleObject()`
- `shouldHandleExtractInvalidPath()`
- `shouldHandleReplaceSuccess()`
- `shouldHandleReplaceFailure()`.

To build the whole project and run all the test cases, run:

- `mvn clean`
- `mvn compile`
- `mvn test`

To run single test case, use the following command under the root file (method name after # can be changed):  
`mvn test -Dtest=org.json.junit.XMLTest#shouldHandleExtractNestedObject`
