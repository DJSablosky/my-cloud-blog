---
title: "Python Upgrade for AWS Lambda"
date: 2021-06-16T12:51:52-04:00
draft: false

categories: [Compute]
tags: [Lambda]
toc: false
author: "Daniel Sablosky"
---
Amazon Web Services (AWS) has ended their support of Python 2.7, requiring many AWS Lambda functions to be upgraded from Python 2 to 3.  The Runtime settings can be updated in the AWS console or with the update-function-configuration command in the AWS CLI, and then the changes can be tested and deployed.  The Python community provides guidance for porting Python 2 code to Python 3 as well as a library to translate this code called lib2to3 at: 

[Automated Python 2 to 3 code translation](https://docs.python.org/2/library/2to3.html)

To install the module:

```
$ pip install 2to3
```

The Python library includes the creation of a diff:

```
$ 2to3 lambda_function.py
```

In order to write the changes back to the source file:

```
$ 2to3 -w lambda_function.py
```

This also produces a backup file should further testing fail.

AWS provides further support for upgrading Lambda functions from Python 2 to Python 3 at:

[Announcing end of support for Python 2.7 in AWS Lambda](https://aws.amazon.com/blogs/compute/announcing-end-of-support-for-python-2-7-in-aws-lambda/)