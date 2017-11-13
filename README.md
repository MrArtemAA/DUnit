# DUnit
Unit test framework for IBM Notes/Domino LotusScript
## Getting started
1. Clone project
2. Make new/Update existing \*.nsf from On-Disk Project (ODP folder)
3. Copy LotusScript libs to target database (unit tests and DUnit libs must be in database with code to be tested)
4. Write & run tests

## Writing tests
1. Include ru.livescripts.dunit.matchers (it already includes ru.livescripts.dunit.core)
2. Create Test class, extending it from AbstractTest (ru.livescripts.dunit.core) class
3. Create Sub to test statements or exceptions (errors). View ru.livescripts.dunit.demo lib for examples
### Testing statements
Surround your test code with
```
    On Error GoTo ErrorHandler
    Const FuncName = "TestClassName.TestSubName ()"
    
    Call Me.BeginTest(funcName)
		
    'Write your test code here
    
    Call Me.EndTest(funcName)
		
    GoTo endh
ErrorHandler:
    Error Err, "(" & DESIGN & ") " & FuncName & ", line " & Erl & Chr(10) & Error$
endh:
```

### Testing exceptions (errors)
Surround your test code with
```
On Error GoTo ErrorHandler
    Const FuncName = "DemoTest.TestAssertErrorExample ()"
		
    Call Me.BeginTest(funcName)
		
    'You may write some code here
    
    On Error ERROR_CODE_TO_TEST GoTo AssertErrorHandler
    'Write code, that throws defined error, here
		
    GoTo endh
AssertErrorHandler:
    Call Me.EndTest(funcName)
    Resume endh
ErrorHandler:
    Error Err, "(" & DESIGN & ") " & FuncName & ", line " & Erl & Chr(10) & Error$
endh:
```

## Running tests
To run tests, copy template agent TestRunner from DUnit project database.