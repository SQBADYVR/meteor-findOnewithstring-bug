meteor-findOnewithstring-bug
============================

Bug report for trying to findOne with a string argument

Log in as admin@test.com with password "admin".

The intent of the project is to allow the user to invite other users to be colleagues (invited) and once they accept, they are listed as colleagues. 

When the template goes to list colleagues (manageAccount.html line 20), it properly gets the list of the current users colleagues from Meteor.users and passes each colleague id string to the helper.  

The helper function 'nameOrEamil' in manageAccount.js line 56 receives the string properly and passes it on line 62 to Meteor.users.findOne({_id:self})

This line results in an exception being thrown by Deps recompute--TypeError:  Object 0 has no method 'substr'.

I have walked through the code to collection.js line 229 and all the variables appear okay until this call executes.  Then the console throws the exceptions shown below.

I am able to execute the identical transaction from the console with no problem.


THe console shows the following:

into function nameorEmail manageAccount.js?55e3f3c485bf010bd05bd80708685586e7640a69:58
String {0: "g", 1: "S", 2: "Z", 3: "u", 4: "3", 5: "Q", 6: "h", 7: "E", 8: "v", 9: "u", 10: "S", 11: "v", 12: "c", 13: "D", 14: "t", 15: "j", 16: "F", length: 17} manageAccount.js?55e3f3c485bf010bd05bd80708685586e7640a69:59
Exception from Deps recompute function: TypeError: Object 0 has no method 'substr'
    at http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1211:33
    at Function._.each._.forEach (http://localhost:3000/packages/underscore.js?0a80a8623e1b40b5df5a05582f288ddd586eaa18:159:22)
    at isOperatorObject (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1210:5)
    at compileValueSelector (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1406:14)
    at http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1386:9
    at Function._.each._.forEach (http://localhost:3000/packages/underscore.js?0a80a8623e1b40b5df5a05582f288ddd586eaa18:164:22)
    at compileDocumentSelector (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1369:5)
    at _.extend._compileSelector (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1346:12)
    at new Minimongo.Matcher (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:1289:27)
    at new LocalCollection.Cursor (http://localhost:3000/packages/minimongo.js?4ee0ab879b747ffce53b84d2eb80d456d2dcca6d:142:20) debug.js:41
Resource interpreted as Font but transferred with MIME type text/html: "http://localhost:3000/fonts/glyphicons-halflings-regular.woff". domrange.js:24
Resource interpreted as Font but transferred with MIME type text/html: "http://localhost:3000/fonts/glyphicons-halflings-regular.ttf".
Resource interpreted as Font but transferred with MIME type text/html: "http://localhost:3000/fonts/glyphicons-halflings-regular.svg".
