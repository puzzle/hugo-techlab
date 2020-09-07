# Lab 9: Deployment

Now we will deploy our small website to Netlify.

## Version Control

Netlify works by connecting with a Git repository. Create a Git repository on github.com (may be private) and push your files:
```
cd mysite
git init
git remote add origin [git clone url]
git add .
git commit -m "Initial Commit"
git push
```

## Register Netlify Account

You will have to create an account on netlify.com.

## Create a new site on Netlify

Login to netlify.com and click "New site from Git".

Follow the instructions to create a Github App.

Edit `config.toml` and add your Netlify URL:
```
baseURL = "https://eager-cray-50c194.netlify.app"
```

---

**Ende Lab 9**

<p width="100px" align="right"><a href="10_cms.md">Netlify CMS →</a></p>

[← back to the overview](../README.md)
