# Introduction to Releases and Importing 

---

Jargon lets you reuse the domains from others, but also helps to protect you when changes happen to the domains that you're using. Read on to learn more.

## About Releases

---

A **Release** is an unchangable version of your domain that is made available to other people to use. Domains in Jargon are [Semantically Versioned](/pages/intro_to_releases_and_importing?id=versioning-releases) to help consumers understand when to use a new version, and which version to choose.

When you create a Release, you can change the Domain's Description and create Release Notes to describe what this release contains, and any help or informaiton that you think is important for other people to know before Importing your Domain.

#### Unchangable?

Once a release is published, it cannot change. We do this to make sure that anyone who imports and depends on your domain won't be impacted by ongoing development to the Domain.

When you've developed your Domain further, you can create additional Releases to make those changes available to others.

### Versioning Releases

To help consumers of your Domain know which Release they should choose, or when they should update to a later Release, Jargon uses a concept from releasing software that is called Semantic Versioning, or semver.

A Semantic Version number conveys a lot of information about the nature of this release, including if it's safe for you to import or not.

Here's an example:

> v2.12.5

There are three main parts to a Semantic Version, explained here from least important to most important:

 - the **Patch** number is last, and is '5' in this example. Increasing the Patch version means that you have made a small and inconsequential update to something, like correcting a spelling mistake. Anyone who was using the previous Release can safely use this one, knowing that nothing really important has changed.
 - the **Minor** number is in the middle, and is '12' in this example. Increasing the Minor version number means that you have added something new but otherwise the Release is still compatible with the previous one. An example would be adding a new column to a Code Table, or adding a new optional Property to a Class.
 - the **Major** number comes first, and is '2' in this example. The Major number is used whenever a breaking change is made. If you've removed or renamed something, that will break everyone who was using it, and is a good reason to increment the Major number.
 
For more information, you can read the official documentation on [Semantic Versioning](https://semver.org) 

## About Importing

---
