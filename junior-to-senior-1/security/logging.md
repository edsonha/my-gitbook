# Logging

Logging is about getting information from your system as to what is happening. You want to gather information about how users are using your service, your web site or perhaps your rest API, so that if something goes wrong or suspicious, you're able to use whatever we've logged to find the issue and fix the bug.

And one of the biggest security issues is something called insufficient logging or missing or ineffective logging that allow attackers to attack systems while not being detected so that they can tamper or extract or destroy data.

Logging tools examples: Winston and Morgan.

Logging is really up to you on what information you want to keep and what information you want to save. The idea is that you want to have good information, but you're not storing any personal / sensitive information in your logs and most definitely you're not returning any logging input to the client. Because if we send something of "user already exists" instead of general error, the attacker know this information \(user exists in database\) and try to log in and can use SQL injection to get the information.

Major issues with logging:

* It does not prevent attack because it is only only going to tell us of a malicious event once it's already happened.
* Need to pair with good monitoring because at usual, hacker can go undetected on average 200 days.
* Issue of how much data do we want to actually record if we have a really busy service. And the more information we have the harder it is to find data that we might be looking for anyway.

