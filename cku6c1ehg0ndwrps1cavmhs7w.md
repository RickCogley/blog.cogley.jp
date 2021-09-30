## Backup your @postmarkapp Templates

The other day I [wrote about](https://blog.cogley.jp/email-services-for-your-apps) using Postmark for sending out HTML emails. We wanted to have a way to backup our [Postmark](https://postmarkapp.com/) email templates automatically, so we coded a simple Github Actions workflow. 

There is about 10 minutes of setup for you to do, and it works well enough to backup your Postmark templates and server information on a schedule. 

Basically, you need to: 

* Visit our [postmark-backup](https://github.com/eSolia/postmark-backup) repo on Github.
* Click "Use this template" to copy the repo to your own account where you can set your repo's visibility. 
* Make a couple of adjustments to the workflow yaml file. 
* Add some repository secrets to reference your Postmark account and server tokens as appropriate. 

Once it's setup, it's basically set and forget, and will backup on a schedule, or when you push. 

%[https://github.com/eSolia/postmark-backup]

* * * 
Post Cover Photo by <a href="https://unsplash.com/@markusspiske?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Markus Spiske</a> on <a href="https://unsplash.com/s/photos/backup?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>. Git repo photo by Rick Cogley. 
  