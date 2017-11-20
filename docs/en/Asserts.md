In order to use asserts in your tests use Assert class (to obtain an instance of Assert class, call Assert() function).  
There are several asserts implemented:

* Assert.True(expr as Boolean)
* Assert.False(expr as Boolean)
* Assert.Equals(matcher as IMatcher) See [Matchers](Matchers.md) for more info.

If assert fails, in log there will be information with assert name and line in test.
