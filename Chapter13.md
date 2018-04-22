# Chapter 13 : Null/nil references

 ### Which does the language use? (null/nil/etc)
 Swift use nil to present empty reference.
 ### Does the language have features for handling null/nil references?
You set an optional variable to a valueless state by assigning it the special value nil:
```
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```
If you define an optional variable without providing a default value, the variable is automatically set to nil for you:
```
var surveyAnswer: String?
// surveyAnswer is automatically set to nil
```
