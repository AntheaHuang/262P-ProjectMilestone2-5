## Intro for Milestone4

One static class was added inside the JSONObject class:

- `private static class JSONObjectSpliterator implements Spliterator<JSONObject>`

One method which used this newly added class and turn a JSONObject into Stream was added inside the JSONObject class:

- `public Stream<JSONObject> toStream()`

### Type of stream implemented:

- The data unit that is passed through the stream is a JSONObject representing a single leaf value. The content of the key and value is exactly the same as they are in the original JSON Object, without displaying the path in the key as well. The reason for this is to meet the requirement of "unless the client code explicitly collects the data into an object, the data should simply flow in small parts to the next operation".

- However, there's also a downside of this method. Since the original leaf values are NOT a JSON Object, new JSON Objects have to be created to store the value and pass into the stream. This results in calling forEach() and doing transformation would not change the original JSON Object.

- If changes to the original JSON Object are wanted, the data passing into the stream should be a JSON Object that's a part of the original one, instead of a newly created one. However, if implementing by this way, the criteria of "which kind of JSON Object should be passed in" is unclear, since there are different sizes of them nesting around, and the whole original JSON Object also counts as well, which would violate the rules of "flow in small parts".

To test the newly written method, 3 test cases were added inside the JSONObjectTest.java, which names followed the naming convention of the original test cases:

- `shouldHandleExtractWithStream()`
- `shouldHandleFilterAndTransformWithStream()`
- `shouldHandleForEachWithStream()`.

To build the whole project and run all the test cases, run:

- `mvn clean`
- `mvn compile`
- `mvn test`

To run single test case, use the following command under the root file (method name after # can be changed):  
`mvn test -Dtest=org.json.junit.JSONObjectTest#shouldHandleExtractWithStream`
