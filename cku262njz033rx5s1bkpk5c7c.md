## Email Services for your Apps

If you are hosting your app on a service like the recently-closed Webfaction, you might be getting shared space for your web pages or app, databases and email addresses that can be used for sending or receiving. However, many modern hosting environments such as  [Vercel](https://vercel.com) , Netlify or others, don't come with email capability and assume you'll setup some service to handle the emails that are issued from your app, such as welcome messages, password resets and the like, or, inbound emails. 

There are plenty of email services out there, and I've used many of them. There are two I started using recently, which have good UX, and hit the spot in terms of features. 

There's a bit of setup in either case, and you need to be able to set up your DNS, but both services I mention below have good documentation and support. 

## Inbound Email via ImprovMX

[ImprovMX](https://improvmx.com/) is about forwarding inbound email in a flexible way. You could use it if your client wants to enable their website domain for email, say for a `hello@theirsite.com` address, forwarding to a distribution list at their usual corporate email system. 

It also lets you forward json generated from the parts of an inbound email message, to a webhook, so that you could handle that programmatically. 

We use it to forward the emails on our contracts. For example, if we have our support desk ticketing email setup so that an email address looks like `acme-support@ourco.net`, and we want to forward to `ticket-acme@mail2db.ourco.jp` and `support-acme@ourco.co.jp`, we can set up a rule that forwards:

```
([a-z]+)-support@ourco.net
```

...to:

```
ticket-$1@mail2db.ourco.jp, support-$1@ourco.co.jp
```

The regex in the parenthesis gets captured, and substituted into the `$1` variable. Easy. 

Also, you may have situations where the client wants to send out as `hello@ourco.net`, and ImprovMX makes it trivial to set up an SMTP login to use for this. There should be a way to make it work in most modern email client software. 

## Outbound Email via Postmark

For outbound email, consider [Postmark](https://postmarkapp.com). It supports the usual *transactional* emails (emails to a single To: address) such as welcome messages, password resets or invoices, as well as what they call *broadcast* emails such as announcements or ToS updates. 

What I really like about Postmark is how easy it is to craft an HTML email template to use. There's a UI for this, and if you've ever struggled with assembling HTML email, you will know the value of something that just works. It's simply not like your standard web page development. Email clients are finicky, and writing emails that will work in most places is hard. The Postmark API documentation makes it easy to test, too. You just paste in your API token, and click. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632716508858/t50yUB2oD.png)

Postmark lets you set up an SMTP address, like ImprovMX, and so your app could take advantage of this to send, as well. 

Postmark are conservative with who they let on their service. You have to fill out a short questionnaire about how you're intending to use their service, and someone will review your application. I think this posture is reasonable and good, because they can guarantee better deliverability that way. 

You may have heard of DMARC, which lets you cut down on scammers spoofing emails from your domain? It prevents people from sending an email from `you@yourco.com` even though they don't have access to your email client. If a recipient or their system marks such an email as spam, it hurts the reputation of all the *other* emails being sent from your domain. DMARC is meant to help with this. 

The problem with DMARC is, the reports are rather technical, and come in as a zip file that contains an XML file with all the details of all the problems with email on your domain. In my opinion, it's a non-starter for business users. 

Postmark has a for-pay service called [DMARC Digests](https://dmarcdigests.com), which gets you a dashboard and action items to improve deliverability for your domain. They also provide a free version, which seems great for a personal domain. In either case you need to set up or cause to be set up SPF, DKIM and DMARC entries in your DNS. 

ImprovMX and Postmark make my life easier, and maybe they'll help you too. 

* * * 

Cover photo by <a href="https://unsplash.com/@jstrippa?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">James Harrison</a> on <a href="https://unsplash.com/s/photos/programming?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  