---
layout:     post
title:      "Wechat Login Test"
subtitle:   "Login Test"
date:       2018-12-22 01:00:00
author:     "affe"
header-style : text
header-img: "img/post-bg-2015.jpg"
tags:
    - kfs
---

##  Wechat Login Test

####  case 1 : Client send valid authcode of a new user, no record of previous user, empty openId field
**expected performance**
- [ ] server register a new user, all fields correct in all tables correct.
- [ ] server keeps headimg in the S3 bucket
- [ ] client keep a record of the user, including openId.
- [ ] client do all other function

#### case 2 : Client send valid openId, refresh token not expired.
**expected performance**
- [ ] client send openId only
- [ ] server checks validity and return
- [ ] server refreshed refresh_token of this user
- [ ] server check if headimg changed, and then post to user basics

#### case 3 : Client send valid openId, refresh token expired, same user accept.
**expected performance**
- [ ] client send openId only
- [ ] server found refresh token invalid, return to client
- [ ] client go to "get authcode" phase, and user grant permission
- [ ] server found previous record, refresh token
- [ ] server check if heading changed and then post to user basics


#### case 4 : Client send invalid openId
**expected performance**
- [ ] server found openId invalid, return error to client 
- [ ] client handle server error properly
- [ ] 
#### case 5 : Client exit wechat login and re-login with same user
**expected performance**
- [ ] client go to login phase, clear all info about wechat login including openId
- [ ] repeat case 1
#### case 6 : Client exit wechat login and re-login with another user
**expected performance**
- [ ] client should see empty user info locally
- [ ] repeat case 1

#### case 7 : Client send get auth request but user declined.
**expected performance**
- [ ] client should go back to login state
#### case 8 : Client send valid openId, expired refresh token same user, and then ask for code, user declined.
**expected performance**
- [ ] local info about user is not empty
- [ ] client receive 'need code' command
- [ ] client didn't get code and error
- [ ] client should go back to login state
 #### case 9 : Client send valid openId, expired refresh token, not the same user, user accept
 **expected performance**
- [ ] local info about user is not empty
- [ ] client receive 'need code' command
- [ ] client didn't get userinfo but not the same with local user
- [ ] client refresh local user info
#### case 10 : Client send valid openId, expired refresh token, not the same user, user declined.
 **expected performance**
- [ ] local info about user is not empty
- [ ] client receive 'need code' command
- [ ] client didn't get code and error
- [ ] client should go back to login state
