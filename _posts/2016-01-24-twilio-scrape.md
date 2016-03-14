---
layout: post
title: Hands-off Scraping with the Twilio REST API
excerpt: Recently, I've been working on a project that involves scraping data for over 16,100 movies. Rather than sit and watch the terminal output of the script, I set up a text alert to let me know when it's done.
---

For the past week, I've been working on a project to predict the success of low-budget movies using regression. Since budget data isn't as readily available for movies as say, gross revenues and ticket sales, my goal has been to maximize my sample size to increase the effectiveness of my model. To that end, I've been using [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/bs4/doc/) to scrape every morsel of data from [Box Office Mojo](www.boxofficemojo.com), which has pretty comprehensive data on almost every movie released since 1925.

Scraping data for over 16,100 movies is no small feat--it took about an hour for the script to finish running. As fascinating as it is to watch the terminal output of my movie log for an hour and chuckle at funny movie names ([I Want Someone to Eat Cheese With](http://www.boxofficemojo.com/movies/?id=iwantsomeonetoeatcheesewith.htm), anyone?), I wanted to be able to step away from the computer and get notified when the script was done running.

Enter the [Twilio](https://www.twilio.com/) REST API, which lets you seamlessly send SMS messages. After a bit of research and script tinkering, I had the text alert set up within 10 minutes. All you need is the [twilio-python library](http://twilio.com/docs/libraries) and API credentials (if you're a trial user, you'll also need to verify the phone number to which you're sending the text message).

I added the following function, which gets called once the scraping script is done:

```python
def text_me(number):
	"""Send a text message when done scraping if env variables
	TWILIO_SID and TWILIO_TOKEN are set.
	Args:
	number (string) -- your phone number, formatted as +1<number>
	"""
	try:
		account_sid = os.environ["TWILIO_SID"]
		auth_token = os.environ["TWILIO_TOKEN"]
		client = TwilioRestClient(account_sid, auth_token)
		message = client.messages.create(to=number,
										 from_="+13476258954",
										 body="done scraping movies!")
		print 'Sending text message!'
	except:
		print 'No twilio credentials configured.'
```

`TWILIO_SID` and `TWILIO_TOKEN` refer to the Account SID and Auth Token credentials, and need to be passed as environment variables when running the script, e.g.:

```bash
$ TWILIO_SID = <my-account-sid> TWILIO_TOKEN = <my-auth-token> python scraper.py
```

And voila! My script texts me when it's done running.

![text msg]({{ site.url }}/assets/twilio-text.jpg)
