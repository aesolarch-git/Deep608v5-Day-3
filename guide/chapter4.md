# Chapter 4: Testing & Verification
### Overview
In this chapter you will finally test out the micro-services based app you have been building the last 3 days!

### Create a Request

 - [ ] Browse to https://block.edl.000.deep608lab.com/ (replace 000 with your lab id)
 - [ ] You should see our simulated block page.
 - [ ] Notice that SSL has been automatically configured for us... Ambassador used LetsEncrypt to request and install a valid SSL certificate!
 - [ ] Go ahead and click the link on that page to submit an unblock request, it should take you to https://request.edl.000.deep608lab.com/
 - [ ] You may be prompted to authenticate by Okta (if not, you were already signed in to Okta -- Okta supports single-sign-on, so you don't get prompted every time!).
 - [ ] Fill in a URL and a reason, then submit your request!

### Approve the Request
Let's approve the request you just submitted!

 - [ ] Browse to https://admin.edl.000.deep608lab.com/ (replace 000 with your lab id)
 - [ ] Note the request you just submitting in the approval queue.
 - [ ] Approve the request!

You can create more requests and approve or reject them if you like!

### View the EDL
To make this URL whitelist useful, we need to serve it out in text format so that our firewalls or URL filters can consume the list and use it in policy.

 - [ ] Browse to https://list.edl.000.deep608lab.com/ (replace 000 with your lab id)
 - [ ] You should see the list of URLs that you have approved, in plain text format.

That's it! You've completed the DEEP608v5 Lab!

# Thank You
Thank you for participating in our DEEP608v5 Hackathon, we hope you enjoyed the lab!

Would would greatly appreciate it if you would take a moment to answer our quick 4-question survey!
https://forms.office.com/r/tsakxfY9HA