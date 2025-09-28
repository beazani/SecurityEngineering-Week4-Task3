## SecurityEngineering - Week4 - Task3

### Subtask 1: Intercepting
The screenshots needed for the subtask 1 can be found in the Subtask1 folder inside the images folder.

### Subtask 2: Repeater

First I went to the DVWA Security Tab and raised the security level from Low to Medium, then generated a cookie called dvwaSession.Then I selected Send to Repeater to repeat the request as many times as I want.

![Vulnerability POST](Images/Subtask2/vulnerabilityPost.png)

When clicking Generate on the Weak Session IDs page, the server sets a cookie named dvwaSession with a numeric value. The application generates dvwaSession by using the current Unix timestamp as the session identifier.<br>
The Unix epoch treats time as a single running count of seconds measured from a fixed origin, which is 00:00:00 UTC on 1 January 1970. The cookie is how many whole seconds have elapsed since that origin, this value is the epoch time (or Unix timestamp).<br><br>

In my two repeats example, in DVWA I saw two cookies:

- dvwaSession=1759050336 (Sun, 28 Sep 2025 09:05:36 UTC)

![First repeat](Images/Subtask2/firstRepeat.png)

- dvwaSession=1759050638 (Sun, 28 Sep 2025 09:10:38 UTC)

![Second repeat](Images/Subtask2/secondRepeat.png)

Even though epoch timestamps are convenient, they are very predictable since they increase by exactly one every second. Using them directly as session IDs is not secure at all, since an attacker could guess session cookies simply by knowing the approximate server time.