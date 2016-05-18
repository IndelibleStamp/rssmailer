# RSS Mailer
## Convert RSS feeds to a digest email

This application is written in Python. It reads a list of feeds from a
config file, iterates through them, finds all posts in the last 24
hours, and sends one email per feed to a preconfigured address.

## Requirements
- python (feedparser, twisted, requests and a few more)
- a [mailgun](https:/mailgun.com) api key. I use their free version and it is more than
  enough for this kind of use case.

## Installation

Install using pip:

`pip install rssmailer`

## Usage

Create a file called `.rssmailer.json` in your home folder and fill it
with these contents:


     {
         "api_key": "<your-key-here>",
         "mailgun_url": "https://api.mailgun.net/v3/<your-domain-here>/messages",
         "mail_to": "foo@bar.baz",
         "mail_from": "postmaster@somedomain.invalid",
         "feeds": [
             "https://soylentnews.org/index.atom",
             "http://feeds2.feedburner.com/3quarksdaily"
         ]
     }


Run the script now to get the digest emails.

`rss_mailer.py`

Set up a daily cronjob to run the script. Something like this:

`0 6 * * * rss_mailer.py`

This will make it run every morning at 6 AM. 

Sit back and wait for the emails.

