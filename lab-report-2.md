# Lab Report 2 - Week 3

## Part 1
1. Code for `ChatServer`
   [!img]
2. First usage of `/add-message`
   [!img]
   * The method in my code that was called was the `handleRequest` method that takes in a
     URI reference and checks the path of the URI. Because the path in this case was equal
     to `/add-message`, it split the query around the ‘&’ sign to isolate the message and
     the username which are then added to the message string.
   * The argument to this method is the URI reference (`url`) of the web server. The relevant
     fields of this class are the String `message` and the String arrays `firstSplit`,
     `sAndMessage`, and `userName`. The `message` String initially starts empty before the
     first method call and the arrays `firstSplit`, `sAndMessage`, and `userAndName` are not
     declared before the `handleRequest` method is called, so their initial value is null.
   * The values of the `message` String and the arrays `firstSplit`, `sAndMessage`, and
     `userAndName` all change. The value of `message` changes from an empty String, “”,
     to “Karen: Hello\n” and the value of `firstSplit` becomes `[“s=Hello”, “user=Karen”]`.
     The value of `sAndMessage` becomes `[“s”, “Hello”]` and the value of `userAndName`
     becomes `[“user”, “Karen”]`.
3. Second usage of `/add-message`
   [!img]
   * The method in my code that was called was the `handleRequest` method that takes in a
     URI reference and checks the path of the URI. Because the path in this case was equal
     to `/add-message`, it split the query around the ‘&’ sign to isolate the message and
     the username which are then added to the message string.
   * The argument to this method is the url of the web server. The relevant fields of this
     class are the String message and the String arrays `firstSplit`, `sAndMessage`, and `userName`.
     The `message` String before the second message is added is “Karen: Hello\n” and the values
     in the array `firstSplit` are [`“s=Hello”, “user=Karen”]`. The values of `sAndMessage` are
     `[“s”, “Hello”]` and the values of `userAndName` are `[“user”, “Karen”]`.
   * The values of the message String and the arrays `firstSplit`, `sAndMessage`, and `userAndName` 
     are all changed. The value of `message` is updated from “Karen: Hello\n” to
     “Karen: Hello\nLucyGoose: Hi!+How+are+you+doing?+\n”. The value of `firstSplit` becomes
     `[“s=Hi!+How+are+you+doing?+”, “user=LucyGoose”]`. The value of `sAndMessage` becomes
     `[“s”, “Hi!+How+are+you+doing?+”]` and the value of `userAndName` becomes `[“user”, “LucyGoose”]`.
     The argument URI `url` that is passed in also has changed its query to
     `/add-message?s=Hi!+How+are+you+doing?+&user=LucyGoose`.



  
     


   
