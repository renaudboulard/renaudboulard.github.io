---
layout: post
title: "Improve your Pull Request description"
description: "How can you improve the quality of your Pull Request description to better describe and explain your work to the person who is going to review your PR and what are the benefits?"
tag:
- software-development
date: 2020-04-24 22:48
image: images/pr_review.png
headerImage: false
category: blog
---

How can you improve the quality of your Pull Request description to better describe and explain your work to the person who is going to review your PR and what are the benefits? 
<!--more-->

A Pull Request is mainly composed of a **title**, a **description**, some **labels**, and a few **commits** that contain **code**. You should pay attention to each of these elements when creating a PR.

A PR without description it’s like throwing away a sheet of paper to your colleague without telling him a word on why you write this paper and what is the purpose of your work. Therefore, he has to figure out by himself without a clue. 
It will be time consuming for him and it will require him extra effort that should have been done by you.

![gif](/assets/images/pr_papers.gif)

Is it the image of you that you want to give to your colleagues? I suppose not.

In this article, we will focus on how improve the quality of your title, description, and labels and what are the benefits to improve these elements. But we will not see how to improve your commits and pull request code/size, which is also quite important for a good PR.

## 1.Meaningful title
The PR title must be explicit, some examples:

* Add one-click booking in the booking flow
* Refactor of user sign-up with Google
* Fix error 500 on the payment page

If you can’t have a simple title, it’s probably because your PR is too large and you should split your work into smaller PRs. Avoid the word "and" in the title, because it means you have two distinct part in your PR that can be split into two different PR.


## 2.Explain why

**Why** did you do this pull request? What is the purpose of your pull request?

Each pull request has an original reason and a purpose.
Link your PR to the original issue, and write a small summary to help the reviewer to quickly understand the reason of the PR and avoid him the need to read a full feature description or bug description. Make it short 1~3 lines, and it should add an extra value compare to the title, if you think the title is enough to understand the why of the PR you can skip the summary.

If you have no issue to link, add the extra necessary information to understand the `why` of your PR.

> With github you can use several [keywords such as Resolves](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue) or the `Linked issues` feature on the right collum of your PR. It will automatically close the issue when the PR will be merge.

## 3.Explain how 

**How** did you resolve the bug? / **how** did you implemente the feature? / **how** did you do the refactoring?

Your commit message and the code itself can explain a lot on how you tackle the issue, but some point like the architectural decision, external lib choice, the reason you implemented an API in a specific way, and a lot of other points can’t be explained only with code.

You have to describe your work to your reviewer to give him the full context and help him to better understand your choices. You can make simple bullets points with the noticeable information, or provide a more detailed explanations. You can also point out some part of the code in your description to guide your reviewer through the changes.

Be careful, avoid repeating what the code does, well-written and named code should explain itself, but instead explain why you wrote the code the way you did it.

## 4.Make it visual

If your PR includes a visual update in your application or website you can add a before / after screenshot, to help the reviewer understand the update, using a simple array:

```
|     Before     |      After     |
| -------------- | -------------- |
| old_screenshot | new_screenshot |
```

You can also add schemas to explain the new or updated architectural element of your codebase or DB. Or if your PR includes a new animation you can add a gif/video of this animation.

Having a visual element make it instantly super clear to your reviewer what are the result of your PR.
> As the adage says `A picture is worth a thousand words` it applies to PR too.

## 5. Use a template
With [github](https://help.github.com/en/github/building-a-strong-community/creating-a-pull-request-template-for-your-repository), [gitlab](https://docs.gitlab.com/ee/user/project/description_templates.html), or [bitbucket](https://bitbucket.org/blog/save-time-with-default-pull-request-descriptions?_ga=2.3591863.664000138.1590590343-427180527.1590590343) you can add PR templates to have the same template every time you create a new PR. 

I see several benefits of using a template :
* Avoid rethinking the way you should describe your PR 
* It gives you an incentive to describe your PR when you create it
* Having a common way to describe your pull request within your team helps your colleagues and you to know what to expect for a description when you start reviewing a PR.

Example of PR templates on popular open source repository:
 * [Gitlab (.gitlab/[...]_templates/Documentation.md)](https://gitlab.com/gitlab-org/gitlab/-/blob/master/.gitlab/merge_request_templates/Documentation.md)
 * [Kubernetes (.github/PULL_REQUEST_TEMPLATE.md)](https://github.com/kubernetes/kubernetes/blob/master/.github/PULL_REQUEST_TEMPLATE.md)
 * [React Native (.github/PULL_REQUEST_TEMPLATE.md)](https://github.com/facebook/react-native/blob/master/.github/PULL_REQUEST_TEMPLATE.md)

Start simple, no need to have a huge template that will never be filled by anyone. In my team, we started with a template containing 2 titles `Why` and `How` no more. Find a template that works for your need and your team.

## 6.Use labels

A label is a meta-data that add extra information to your PR, it must help your reviewer to better understand your PR.

Labels can be used in various ways, for example:
 * To define the type of PR (New feature, Bug fix, Refactoring, Docs, Bump version, etc..)
 * To define the product scope of the PR (Payment, Booking, Admin, User assistance, etc...)
 * To define the stack scope (Front-End, Back-end, Mobile, API, etc...)
 * To define the status of the PR (WIP, Don't merge, Ready for Prod, ect...)

There are lots of other ways to use labels, I will not recommend a specific way to use them, but when you add a label ask yourself: 
> What are the benefits for my reviewer to have this information? Will it help him understand the PR faster and better?

Benefits examples : 

{:.table}
|Info|Benefits|
|---|---|---|
|Product scope (Payment, Booking, etc..)| Help to project himself into a part of the product and therefore the codebase |
|Stack scope (Front-End, Back-end, API, etc..) | Help to project himself into a part of the code base, and a type of coding|
|PR status (WIP, Review Needed, etc..) |Estimate the amount of effort and time required for the review|

Concrete examples:

|Info|Example|
|---|---|---|---|
|Product scope (Payment, Booking, etc..)| If your reviewer has a good knowledge of the code base, seeing a `Payment` label will instantly make it think about your payment systems/services, and we will expect your PR to update this part of the code |
|Stack scope (Front-End, Back-end, API, etc..) | With a `Front-end` label, the reviewer will instantly think about a visual update and project himself in the view/template/js part of your code (whatever your stack is)|
|PR status (WIP, Review Needed, etc..) |A `WIP` PR will require more a macro review no need to ding in all small details, and it will probably require less time to be reviewed|

> With a meaningful title and label, the reviewer can already learn a lot on your PR from the PR list without reading the description or the code. He will be able to project himself on some part of the product and the codebase. This will also help him to prioritize and schedule his PR review more easily.

## Benefits of a good PR description

Improving the way you describe your pull request has several benefits:

**For you**
* Taking the time to think about how to describe your work will give you the chance to see your PR from another point of view and it could lead to improvements before you send the PR.
* If you can't simply describe the work done, it probably means there is a way of improving it or rethinks/split your PR

**For the reviewer**
* The more time you take to write a good PR description, the more time you will save your reviewer to understand the context, and the work done on your PR.
* A meaningful description will help your reviewer to quickly switch context from is current work with less effort.
* He will most likely enjoy reviewing your PRs if there are more attractive, which will surely lead to better and faster code review.

**For the other team members**
* New developer joining your team will be able to learn a lot from what has been done in the past and the reason of some choice, just by looking at previous PR.
* Junior dev or another team member that aren't the PR reviewer, but who are curious of what's going on in the code base, will be able to quickly read a PR description and more easily understand the update, without the need to read complex part of the code where they haven't work on yet. It's a good way to widen their knowledge and onboard on a new part of the product annd code base.

A good PR description is a win-win for everyone.

## PR description is underrated

The value of a good PR description is underrated, we tend to think that meaningful code and well-named commit is enough. And yes it's important, it should be the priority in your PR because, in the end, you will only keep the commits and the code in your codebase, not the PR description.

But a meaningful PR description and a meaningful title and labels will make your PR much more attractive and clear for your reviewer. It will improve the communication between you and the other developers of your team. In the long term, I'm convinced it boosts the review process and the productivity of your team and company.

