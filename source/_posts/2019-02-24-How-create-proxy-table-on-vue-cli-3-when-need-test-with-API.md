---
title: Post title
date: 2019-02-24- 16:32:17
updated: 2019-02-24- 16:32:17
tags: [vue]
---

if you use vue cli 3 to build a project,
then when you need access api from other domain,
how use proxy table local mode ?

on this case
i will demo a local proxy api
that will redirect all my
`http://localhost/api` request
to
`https://api.somewhere.com/v2/api` this really api server
&nbsp;
&nbsp;
<!--more-->
####1. set your variable into .env file
.env.development.local
```
VUE_APP_API_URL=/api
```
&nbsp;
####2. set proxy config
vue.config.js
```
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'https://api.somewhere.com',
        secure: true,
        pathRewrite: {
          '^/api': '/v2/api',
        },
      }
    },
  },
}
```
&nbsp;
####3. use axios call api
api/index.js
```
import axios from 'axios'

export const getResult = (payload) => {
  let token = 'your auth token'
  let headers = {
    'Authorization': `Bearer ${token}`,
    'Cache-Control': 'no-cache'
  }

  const searchResult = axios.create({
    baseURL: process.env.VUE_APP_API_URL,
    headers: headers
  })

  return searchResult.get(`/search`, { params: payload })
}
```
&nbsp;
&nbsp;

ref:
https://webpack.js.org/configuration/dev-server/#devserverproxy
https://github.com/chimurai/http-proxy-middleware#options


