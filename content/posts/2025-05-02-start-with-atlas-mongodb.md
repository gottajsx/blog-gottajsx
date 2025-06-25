+++
authors = ["Lone Coder"]
title = "tart with Atlas MongoDB"
date = "2025-05-02"
description = "Start with Atlas MongoDB"
tags = [
    "Atlas", "MongoDB"
]
+++

MongoDB Atlas provides an easy way to host and manage your data in the cloud. This tutorial guides you through creating an Atlas cluster, connecting to it, and loading sample data.

## Create an Atlas Account

To register with and log in to Atlas, you can use one -- and only one -- of the following options:

* Your email account

* Your GitHub account

* Your Google account

## Deploy a Free Cluster

Atlas Free clusters provide a small-scale development environment to host your data. Free clusters never expire, and provide access to a subset of Atlas features and functionality.

Paid clusters provide full access to Atlas features, configuration options, and operational capabilities. For more information on paid clusters, including deployment instructions, see Create a Cluster.


## Manage the Database Users for Your Cluster

You must create a database user to access your cluster. For security purposes, Atlas requires clients to authenticate as MongoDB database users to access clusters.

## Manage the IP Access List

An IP is a unique numeric identifier for a device connecting to a network. In Atlas, you can only connect to a cluster from a trusted IP address. Within Atlas, you can create a list of trusted IP addresses, referred to as a IP access list, that can be used to connect to your cluster and access your data.

## Connect to Your Cluster

You can connect to your cluster in a variety of ways. In this tutorial, you use one of the following methods:

* The MongoDB Shell, an interactive command line interface to MongoDB. You can use mongosh to insert and interact with data on your Atlas cluster.

* MongoDB Compass, a GUI for your MongoDB data. You can use Compass to explore, modify, and visualize your data.

* A MongoDB driver to communicate with your MongoDB database programmatically. To see all supported languages, refer to the MongoDB Driver documentation.