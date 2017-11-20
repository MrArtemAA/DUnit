IMatcher is an "interface" which is passed to Assert.Equals() method.

There are several default implementations of IMatcher (ru.livescripts.dunit.matchers):
* SimpleValueMatcher - compares two values. Is not type-safe
* DocumentItemsMatcher - compares items in two documents by given item names array
* DatabaseMatcher - compares whether two db references point to the same database
* DocumentMatcher - compares whether two doc references point to the same document in the same database and all items are identical (uses DatabaseMatcher and DocumentItemsMatcher)

To write your own matcher, create class, extend IMatcher "interface" ```Class CustomMatcher As IMatcher``` and implement ```Public Function Matches() As Boolean``` method