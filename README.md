# FAQ API's

This repository  Contains custom Rest FAQ API's which will be used by web components on SE.COM. The FAQ details are retrieved from bFO based on the path param values. The API's used are

| API Name | Path Params | Method | Comments |
| ------ | ------ | ------ | ------ |
| /faq/popular/ | /articleType/repo/language | GET |  |
| /faq/details/ | /articleId/repo/language | GET |  |
| /faq/products | /articleId/repo/language | GET |  |
| /faq/ratings/ | /articleId/language | GET |  |
| /faq/feedback/| /articleId/language | POST |Body :  {"Yes__c" : false,"No__c" : true,"Comment_if_No__c" : "","g-recaptcha-response":"" } |
## Path Parms:

**articleType** - Type of Articles retrieved based on an algorithm, Possible values are
- pv - Popular videos 
- pa - Popular Articles
- gk - General Knowledge

**repo** - country code to which the article is tagged.

**Language** - Language of the Article.

**articleId** - FAQ Number

## Installation

The API's are been hosted  on Heroku and written in NodeJs

**Test API Locally** (Ensure Environment Variable are configure locally)

```bash
- git clone https://github.com/bFO-dev/faq-api.git 
- NPM Install
- node index.js
- Navigate to the API Method which needs to be tested with
```
**Hosting on Heroku**

```bash
$ heroku login
$ heroku git:clone -a ckm-api-staging
$ cd ckm-api-staging
$ git add .
$ git commit -am "Push code"
$ git push heroku master
Navigate to heroku URL with the API method to test it
```
## Environmental Variables setup (Used in Heroku and Local )
- Configure ENV vars in apps heroku dashboard Click [here](https://devcenter.heroku.com/articles/config-vars)

**BFO configs**:

- process.env.COMMUNITY_URL

- process.env.BFO_FEEDBACKOBJ_RECORDTYPEID

- process.env.BFO_LOGIN_URL

- process.env.BFO_USERNAME

- process.env.BFO_PASSWORD

- process.env.BFO_CLIENT_ID 

- process.env.BFO_CLIENT_SECRET

- process.env.BFO_ACCESS_TOKEN  //configure some dummy token node js code will pick up the token from login API automatically. 

- process.env.BFO_INSTANCE_URL // currently using static instance URL also node.js code picks the instance url from login API  if it is changed for any reason.

**Google CAPTCHA configs:**

- process.env.GCAPTCHA_SECRET

- process.env.GCAPTCHA_URL

**Memcache credentials:**

- process.env.MEMCACHE_SERVERS

- process.env.MEMCACHE_USERNAME    

- process.env.MEMCACHE_PASSWORD   

**Cors allowed domains:**
- process.env.ALLOWED_ORIGNS

## Heroku commands reference
| Command | Description |
| --------------- | ------ |
| heroku login |This command opens your web browser to the Heroku login page. This authentication is required for both the heroku and git commands to work correctly. |
| heroku create | When you create an app, a git remote (called heroku) is also created and associated with your local git repository.|


## Heroku logs:
- heroku logs  or heroku logs -n 200 //fetch your app’s most recent logs
- heroku logs –tail  //real-time tail displays recent logs

**[Filtering](https://devcenter.heroku.com/articles/logging#filtering) logs:**
- heroku logs --dyno router  //route logs
- heroku logs --source app //web app logs


## Tech
- NodeJS
- Express
