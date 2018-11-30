---
date: '2018-11-30'
title: 'Developer Journal: Week 3'
category: 'Journal'
---

## Individual Accomplishments

[@VeraSimon](https://github.com/VeraSimon)

![Contribution Graph](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-30/contribution_graph.png 'Github Repository Contribution Graph')

<!-- Provide a paragraph (5-8 sentences) summarizing the work you did this week, the challenges you faced, the tools you used, and your accomplishments. -->

The last week saw me doing some major refactoring for the web frontend of the app, including getting OAuth2 set up for the client, and also saw me attempting to get OAuth2 integration working for the backend server as well. On top of all this, there was the usual large swaths of time I spent helping others in my group troubleshoot and work through code and infrastructure issues they were experiencing. Some of this help included getting end-to-end Strip API integration working both in development and in production, and trying to mentor others on React/Redux best practices and conducting a meeting in which I explained some methods to break down work into manageable pieces that wouldn't drive your code reviewers away.

## Tasks Pulled

### Front End

- Redux Store Refactor
  - https://trello.com/c/R8wiVpSx/103-refactor-redux-actions-into-separate-files
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/57
- Navigation Refactor
  - https://trello.com/c/56QS2pQT/120-refactor-navigation-into-its-own-component
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/63
- Stripe frontend bug
  - https://trello.com/c/5JWLs6Rr/143-stripe-public-key-bug
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/70
- Google OAuth2 frontend
  - https://trello.com/c/sw0I9lOk/107-integrate-google-oauth-into-frontend
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/78

### Back End

- Stripe backend
  - https://trello.com/c/F0ETpiH1/78-strip-aip
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/64

### Miscellaneous

- Stripe production bug fix
  - https://trello.com/c/lKzYA2sc/149-stripe-heroku
  - https://github.com/Lambda-School-Labs/Labs8-OfflineReader/pull/84

## Detailed Analysis

<!-- Pick one of your tickets and provide a detailed analysis of the work you did. This should be approximately 1/4 page of text, and at least three screenshots. -->

So over the break I took some time and refactored our Redux store implementation. As it existed at the time, the Redux store was pulling in all kinds of dev tools and the configs for them were getting deployed to production, much to my chagrin. In addition to this, all of our store actions had been clobbered together into one file, despite covering actions from multiple reducers. The first thing I undertook in this refactor was to separate out the actions into files representing their individual reducers, so that they were easier to manage and track down, which also made the odds of confusing actions for the wrong reducer much lower. Once they were separated and confirmed still working, I moved on to refactoring the associated reducers a bit to remove cross-reducer reducing. Once I had the actions and reducers in a reasonable state, I moved on to refactor the way in which we were generating the store overall, with a bit of help from the Redux documentation. The resulting refactor there produced a function that purpose-built a store depending on whether the frontend was running in development or production, keeping those pesky dev tools from surfacing on the production servers any more.

![Store Builder](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-30/store_builder.png 'Store Builder')

![Store Implementation](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-30/store_implementation.png 'Store Implementation')

![Store code layout](https://raw.githubusercontent.com/VeraSimon/portfolio/master/blog/2018-11-30/store_layout.png 'Store code layout')

## Bringing The App Together

<!-- As a part of your journal entry, write ¼ to ½ a page reflecting on your experiences working with a team to convert a disparate set of components into a single, cohesive, and complete product. Describe the challenges you faced and the steps you took to overcome them. -->

It's been a rough week trying to pull all the pieces of the application together into a coherent whole. There's a bit of stepping on each others toes while working on the frontend, but the real pain comes when more than one of us is working on backend code. The way that Django lays things out is not overly conducive to trying to integrate multiple Django applications together under a single project. Despite all this, we all manged to keep relatively level heads, and some of us spent way more time than we probably should have trying to get the backend into a cohesive whole, with at least one overnight hackathon that happened, and more than a few where we were up pretty late trying to get stuff done as well.

## Whiteboarding Session

- [Whiteboarding playlist](https://www.youtube.com/playlist?list=PLw5W0SfMYtxWUrDu0Y0jDRIiNv3et_TZz)

<!-- Add a link to the weeks whiteboarding session -->

- [Rotate Image](https://youtu.be/xbtjR_FxTi4)

## Weekly Milestones

<!-- insert stuff here -->

[Splash Page, Stripe Integration, Scraper, and Authentication](https://anywhere-reader-test.netlify.com/)

[Settings (WIP)](https://anywhere-reader-test.netlify.com/settings/)
