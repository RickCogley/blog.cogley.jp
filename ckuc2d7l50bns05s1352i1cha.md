## Deploy Hugo on Vercel

A question on the Hugo support forum prompted me to try deploying the Hugo [quickstart](https://gohugo.io/getting-started/quick-start/) site on [Vercel](https://vercel.com). It was super simple. Here's what I did. 

### Hugo Quickstart

First, just run through the quickstart steps in a local folder to get it basically working. I put my projects in `$HOME/dev`. 

### Connect to Vercel using their CLI command

Assuming you have installed the `vercel` [CLI](https://vercel.com/docs/cli) command locally and have authenticated, you can connect your new Hugo project to your Vercel account by running `vercel` in the project folder. It prompts you for the basic settings you want for the project, and for a standard Hugo site, `./`  is correct for the code directory:  

```
vercel
Setup and deploy? Y
Which scope? Rick Cogley
(pick user or org, and I picked "Rick Cogley" my account)
Link to existing project? N
Project name: hugo-quickstart
In which directory is your code located? ./
Override settings? N
Deploying...
```

_N.b.: Vercel private / free accounts require non-commercial sites_

It will start deploying, and return some info about the deployed site. 

```
Want to override the settings? [y/N] N
🔗  Linked to rickcogley/hugo-quickstart (created .vercel and added it to .gitignore)
🔍  Inspect: https://vercel.com/rickcogley/hugo-quickstart/APeDa4... [3s]
✅  Production: https://hugo-quickstart-lilac.vercel.app [copied to clipboard] [28s]
📝  Deployed to production. Run `vercel --prod` to overwrite later (https://vercel.link/2F).
💡  To change the domain or build command, go to https://vercel.com/rickcogley/hugo-quickstart/settings
user=1.07s system=0.25s cpu=0% total=2:39.28
```

You'll see that it creates a `.vercel` folder in your project folder, which contains account and project information in a `project.json`. This folder is added to `.gitignore` so if you `git clone` to another system at a later date, you'll need to link it again using `vercel`. 

The site should now be available where Vercel deployed it (it's on the clipboard, so just paste into your browser to check). 

So, it's deployed, and you could simply work from your local folder, and use the `vercel` CLI command to re-deploy when you need to. However, it's cooler to deploy on git push, so let's get that working next. 

### Minor Tweaks Needed

Now you can edit your Hugo `config.toml` adding the URL that Vercel provided as a `baseURL`, although, it appears that Vercel is smart enough to feed Hugo the production URL anyway. 

Also, since Vercel's default Hugo version is really old, copy the `vercel.json` from my [test repo](https://github.com/RickCogley/hugo-quickstart/) for this post, and add it to the base of your project. This will tell Vercel to use that version of Hugo and also set some security headers for you. 

### Create a GitHub Repository and Link It

Next, create a repository in your Github, but _do not_ add a README or anything. Then execute these commands from your local project folder, to add your new GH repository as a remote, add and commit the changed / added files, and push to main. 

```
git remote add origin https://github.com/YourGithubUser/hugo-quickstart.git
git add .
git commit -m "added baseurl to config, added vercel.json"
git branch -M main
git push origin main
```

Now in your Vercel project, settings, Git menu, connect Vercel to your Github repo using the button. 

### Test by Editing and Pushing

Then to test, make an edit in the site files (e.g. `content/my-first-post.md`), push to main, then check the URL that Vercel deployed on. You can watch it deploy in your Vercel project. 

And that is it. A very simply process to get a Hugo project linked up to and deployed to Vercel. 

![Vercel](https://therealsujitk-vercel-badge.vercel.app/?app=hugo-quickstart&style=for-the-badge)

%[https://github.com/RickCogley/hugo-quickstart/]


* * * 
Cover Photo by <a href="https://unsplash.com/@virussinside?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Artiom Vallat</a> on <a href="https://unsplash.com/s/photos/victor-hugo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  