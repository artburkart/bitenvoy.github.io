---
date: 2016-04-23T15:21:22+02:00
title: BitEnvoy
type: homepage
menu: main
weight: 0
---

## What could BitEnvoy be?

[BitEnvoy](https://github.com/artburkart/bitenvoy) will be an open
source, cross-platform, cross-provider, pull-based deployment tool
designed for flexible delivery of code, static files, and other
artifacts.

## What does BitEnvoy solve?

BitEnvoy is a solution for the deployment/delivery piece of your
software development pipeline. Let's say your pipeline looks like the
following:

![VCS to CI to Unknown to Live Servers](https://s32.postimg.org/z89g8e54l/typical_deployment.png "VCS to CI to Unknown to Live Servers")

A common approach to deploying artifacts is to lock a branch of your
software's VCS system to a set of target servers. For example, if git is
the VCS of choice, a repository's `staging` branch might be locked to a
set of servers responsible for serving a webpage at
`https://staging.example.com`. Once code is pushed to that branch, a CI
system like Jenkins is typically triggered to exercise a series of tests
on the latest code revision for the staging branch. Once all the tests
pass, Jenkins is usually responsible for delivering the code to the
staging servers. This is typically performed using `scp`, `rsync`,
`sftp`, or by some other means that requires your CI tool to have direct
access to the target servers.

Often the CI tool is used to update the code revision with sensitive
information like database secrets. Unless a CI tool is installed for
each target deployment environment, this strategy establishes a single
point of failure where all of a company's sensitive database and API
information can be accessed freely if the CI tool is ever compromised.

Even if no secrets are passed through the CI tool, and even if some
intermediate deployer server is used for deployments, the intermediate
deployer server is often hand-rolled as a simple stopgap that provides
minimal flexibility around deployment strategies and unsatisfactory
feedback for success and failure status of deployments.

These are the problems BitEnvoy will solve.

## How will BitEnvoy solve these problems?

The initial idea is BitEnvoy will be split into two distinct parts:

- deployment agent
- deployer hub

The deployment agent will be designed such that it can be installed with
minimal effort on as many operating systems as possible. Agents will
poll the deployer hub for deployment jobs to execute. When a deployment
agent is assigned a deployment job, the agent will download an
instruction set indicated within the deployment job's payload and begin
executing instructions contained therein. During the attempted
deployment, the agent continuously updates the deployer hub with the
state of the deployment. Since the agents live on the target servers,
they only know the sensitive information they need to know and nothing
more.

The deployer hub will initiate and coordinate deployments for the
agents. It can be given read-only access to your various cloud provider
APIs to collect metadata about servers where you have a deployment agent
installed. This information will be used to group agents together for
various artifact deployments. The deployer hub will also be used to
design deployment strategies for each agent grouping. A deployment
strategy could be "deploy to all agents at the same time" or "deploy to
agents in this specific order." In addition to deployment grouping and
strategy execution, the deployer hub will serve as the dashboard for
deployment statuses and as a mechanism for one-off deployments of
previously tested code revisions.

With these two pieces BitEnvoy will serve as an integral tool for
monitoring and actuating the deployment of software to your cloud
ecosystem.

## That's the idea

In its full glory, BitEnvoy could be an enormous project that results in
months of active development before it ever sees the light of day. We
don't want it to be this way. Instead, we're asking you what you want to
see first.

Below is a list of what we think are the most exciting features BitEnvoy
could offer. If you're interested in this project, please [give it a star on GitHub](https://github.com/artburkart/bitenvoy)
and take a look at the issues we've created. If you're interested in one
of the issues, give it a thumbs up and we'll prioritize its implementation
accordingly!

- [Cloud-provider metadata discovery]()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()
- []()

Thanks for your support!

[Arthur Burkart](https://github.com/artburkart), Cara Pacifico, Tadashi Kamitaki

