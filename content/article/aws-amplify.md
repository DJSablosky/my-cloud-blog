---
title: "Aws Amplify App"
date: 2021-05-27T11:04:53-04:00
draft: false

categories: [Web]
tags: [Amplify, Hugo]
toc: false
author: "Daniel Sablosky"
---
This site is a Hugo generated site hosted as an application by Amazon Web Services (AWS) Amplify.  There is a workshop for AWS Amplify at:

[Developing and Hosting Professional Online Content in AWS](https://hosting-hugo-content.workshop.aws/)

AWS Amplify is really two things.  It is a framework for building cloud-powered apps as well as a service for hosting them.  The workshop focuses more on the framework, but the following video provides clarification for the nuances of hosting apps:

[Building a static Website on AWS with Hugo and AWS Amplify](https://www.youtube.com/watch?v=50xVrCv2OB4)

I started out simple, but I chose a Hugo theme called Bilberry that I could gradually add more features. The Bilberry Hugo Theme includes a Python script for uploading indexes to an Algolia search service:

[Bilberry Hugo Theme](https://themes.gohugo.io/bilberry-hugo-theme/)

AWS Amplify works off of a Github (or AWS CodeCommit) hook for continous deployment and offers feature branches for continous integration as well as a Secure Sockets Layer (SSL) certificate for encryption in transit.  A YAML file provides build specifications, and environment variables are available for such things as API keys (which should not be pushed to Github or AWS CodeCommit repos as they would become vulnerable to compromise.)

In the config.toml file, there is a variable for base url that needs to be a value (like http://www.example.com) in order to test the site:

```
$ hugo server -D
```

However, the base url in the config.toml needs to be "/" when pushed to a repo in order for it to work with the custom domain in AWS Amplify.  In addition, the static pages need to be built in order to produce the index file for the Algolia search service:

```
$ hugo -D
```

After the index is uploaded to the Algolia search service, the compiled files in the public folder should be deleted in order to always produce a fresh index in the future and avoid pushing them to any repos:

```
$ rm -r public
```

Also, one of the indices in Algolia must be "language" in order for the search service to work.  Algolia is free as long as their logo appears in the search box, but Algolia offers more features with a subscription.

[Algolia](https://www.algolia.com/)