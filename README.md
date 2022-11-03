## Improved Reddit Mass Account Generator/Upvoting


***UPDATE 11/22*** https://forum.torproject.net/t/reddit-onion-service-launch/5305
Reddit now has it's own hidden service available below
https://old.reddittorjg6rue252oqsxryoxengawnmo46qy4kyii5wtqnwfj4ooad.onion/

Prerequisites
Firefox browser.
You must have the Tor service installed and running for this to properly work. Reddit limits account creation from individual IP addresses and Tor allows you to get around this.

sudo apt-get install tor
Selenium
You must also have Selenium installed.

pip install selenium
This may or may not be an issue for you, but Seleinum would not run properly with Firefox on my system. I had to update my geckowebdriver by moving the most recent version into /usr/local/bin/.

Instructions
randomUsernames.py
This file will generate a text file will 100 random usernames and passwords in the format of username:password.

creator.py
This file will create your accounts. When run it will open firefox using tor and enter the first username:password combo from 'redditNameList.txt' into Reddits's account creator. The program will now pause and wait for you to solve the captcha and Press 'sign up'. After you have done this, press enter and that username:password combo will be removed from 'redditNameList.txt' and moved to 'createdNames.txt'. Tor will restart to bypass Reddit's IP limiting. You can repeat this process until you have as many accounts as you want or need.

Note: Ocassionally the Captcha will not appear. I'm not sure why this happens, but if you move to a new IP it seems to resolve itself. If you press 'r' then 'enter' instead of just 'enter', it will skip the current username:password combo leaving it in 'redditNameList.txt' and not moving it to 'createdNames.txt'.

upvoter.py
This file allows you to upvote posts or comments. You must enter the link to the post or comment at the top of the file in 'postLink' or 'commentPermaLink' variable. You must also comment out the function call you are not preforming in main. When ran, this will iterate through 'createdNames.txt' signing in each account, upvoting, then moving to the next account. Tor is not used in this file as I didn't notice any vote limiting.


Original Script:
https://github.com/ahaggard2013/Reddit-Account-Generator-and-Mass-Upvoter


By Default the port numbers set to 9051 for configuration with the tor browser
