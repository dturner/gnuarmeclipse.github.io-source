---
layout: page
permalink: /developer/publish-procedure/
title: How to publish the plug-ins?
author: Liviu Ionescu

date: 2015-09-10 21:07:00 +0300

---

The plug-ins are published both as update sites (on SourceForge, as an Eclipse update site, with multiple mirrors) and as archives (on GitHub as [Releases](https://github.com/gnuarmeclipse/plug-ins/releases)).

The reason SourceForge is still used is that GitHub does not provide a convenient way to publish an Eclipse update site.

## Publish on the SourceForge test site

After each new build, to allow testing on various platforms, the plug-ins are published on the test site.

For this, run the `scripts/publish-updates-test.command` (this is a script that can be executed directly in the macOS Finder).

A typical session looks like:

```
$ /Users/ilg/My\ Files/MacBookPro\ Projects/GNU\ ARM\ Eclipse/plug-ins.git/scripts/publish-updates-test.command ; exit;
Updating Eclipse/updates-test

User: ilg-ul
API key: XXXXXXXXXXXX
Owner: gnuarmeclipse
Create version 'updates-test/p2/3.4.1.201704251808'
######################################################################## 100.0%
Created.

Upload 'artifacts.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'artifacts.xml.xz' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'content.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'content.xml.xz' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'p2.index' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.codered_1.1.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.doc.user_1.1.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.packs_2.2.2.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.templates.ad_1.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'features/ilg.gnuarmeclipse.templates.stm_2.6.2.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.codered_1.1.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.core_3.4.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.core_1.2.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag.restart_1.3.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.gdbjtag_3.2.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.debug.packs_1.1.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.doc.user_1.1.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.managedbuild.packs_1.3.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.packs.core_1.1.3.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.packs.data_1.3.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.packs.ui_1.2.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.packs_1.2.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.ad_1.1.4.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.core_2.5.6.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.freescale.pe_1.2.1.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Upload 'plugins/ilg.gnuarmeclipse.templates.stm_2.6.2.201704251808.jar' to '/updates-test/p2/3.4.1.201704251808/'
######################################################################## 100.0%
Uploaded.
Publish 'updates-test/p2/3.4.1.201704251808'
{"files":35}

Rsync-ing SourceForge Eclipse/updates-test site (-vrCt --exclude=scripts --exclude=.* --delete --checksum)
Password: 
building file list ... done
deleting features/ilg.gnuarmeclipse.templates.stm_2.6.2.201704242117.jar
deleting features/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704242117.jar
deleting features/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704242117.jar
deleting features/ilg.gnuarmeclipse.templates.ad_1.1.4.201704242117.jar
deleting features/ilg.gnuarmeclipse.packs_2.2.2.201704242117.jar
deleting features/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704242117.jar
deleting features/ilg.gnuarmeclipse.doc.user_1.1.1.201704242117.jar
deleting features/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704242117.jar
deleting features/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704242117.jar
deleting features/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704242117.jar
deleting features/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704242117.jar
deleting features/ilg.gnuarmeclipse.codered_1.1.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.stm_2.6.2.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.freescale.pe_1.2.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.core_2.5.6.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.templates.ad_1.1.4.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.packs_1.2.3.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.packs.ui_1.2.3.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.packs.data_1.3.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.packs.core_1.1.3.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.managedbuild.packs_1.3.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.doc.user_1.1.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.packs_1.1.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag_3.1.2.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.restart_1.3.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.debug.core_1.2.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.core_3.4.1.201704242117.jar
deleting plugins/ilg.gnuarmeclipse.codered_1.1.1.201704242117.jar
./
artifacts.jar
artifacts.xml.xz
content.jar
content.xml.xz
p2.index
features/
features/ilg.gnuarmeclipse.codered_1.1.1.201704251808.jar
features/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704251808.jar
features/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704251808.jar
features/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704251808.jar
features/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704251808.jar
features/ilg.gnuarmeclipse.doc.user_1.1.1.201704251808.jar
features/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704251808.jar
features/ilg.gnuarmeclipse.packs_2.2.2.201704251808.jar
features/ilg.gnuarmeclipse.templates.ad_1.1.4.201704251808.jar
features/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704251808.jar
features/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704251808.jar
features/ilg.gnuarmeclipse.templates.stm_2.6.2.201704251808.jar
plugins/
plugins/ilg.gnuarmeclipse.codered_1.1.1.201704251808.jar
plugins/ilg.gnuarmeclipse.core_3.4.1.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.core_1.2.1.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag.jlink_4.1.4.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag.openocd_4.1.4.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag.pyocd_1.1.3.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag.qemu_3.1.4.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag.restart_1.3.1.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.gdbjtag_3.2.1.201704251808.jar
plugins/ilg.gnuarmeclipse.debug.packs_1.1.1.201704251808.jar
plugins/ilg.gnuarmeclipse.doc.user_1.1.1.201704251808.jar
plugins/ilg.gnuarmeclipse.managedbuild.cross_2.4.1.201704251808.jar
plugins/ilg.gnuarmeclipse.managedbuild.packs_1.3.1.201704251808.jar
plugins/ilg.gnuarmeclipse.packs.core_1.1.3.201704251808.jar
plugins/ilg.gnuarmeclipse.packs.data_1.3.1.201704251808.jar
plugins/ilg.gnuarmeclipse.packs.ui_1.2.4.201704251808.jar
plugins/ilg.gnuarmeclipse.packs_1.2.4.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.ad_1.1.4.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.core_2.5.6.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.cortexm_1.4.2.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.freescale.pe_1.2.1.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.freescale_2.2.8.201704251808.jar
plugins/ilg.gnuarmeclipse.templates.stm_2.6.2.201704251808.jar

sent 8222123 bytes  received 1158 bytes  213591.71 bytes/sec
total size is 8216700  speedup is 1.00
Published on the test site.
Archive available from "/Users/ilg/My Files/MacBookPro Projects/GNU ARM Eclipse/archive/internal/ilg.gnuarmeclipse.repository-3.4.1-201704251808.zip"
When final, don't forget to publish the archive too!
Install new software from http://gnuarmeclipse.sourceforge.net/updates-test
logout
```

## Install on a separate Eclipse

Test if the new build can be used as an update site, by installing from updates-test on a separate Eclipse (not the one used for development).

## Create a new milestone

In the [plug-ins issues](https://github.com/gnuarmeclipse/plug-ins/issues) page, click the [Milestones](https://github.com/gnuarmeclipse/plug-ins/milestones) button and add a [new](https://github.com/gnuarmeclipse/plug-ins/milestones/new) milestone. As title, use the current version, like _v3.2.1_.

## Update the Change log

Scan the Git log and add new entries to the [Change log]({{ site.baseurl }}/developer/change-log/) (pages/developer/change-log.md), grouped by days.

```
$ git log --pretty='%cd * %s' --since 2015-06-24 \
--reverse --date=short >~/Desktop/ChangeLog.txt
```

Add an entry with the latest feature & plug-in versions, copied from the publish script output.

## Prepare a new blog post to announce the release

Add a new file to the `_drafts` and later moved to `_posts/plugins/releases`.

Name the post like: *Release v2.9.3 201508190739*, title: *Version 2.2.1-201404120702 released*.

The structure of the post should contain:

* date, as _Aug 1, 2015_ (italics)
* one intro paragraph with the summary of the changes
* a link to `[Binary files »]()`, currently empty, to be filled with the release URL
* headers like:

```
## New features
## Addressed bugs
## Template issues
## Other changes
## Known problems
```

An example would be the [2.9.1](https://github.com/gnuarmeclipse/plug-ins/wiki/Release-v2.9.1-201508011813) announcement.

Scan the [GitHub Issues](https://github.com/gnuarmeclipse/plug-ins/issues) and the [SourceForge trackers](https://sourceforge.net/p/gnuarmeclipse/_list/tickets) and add references to all tracked issues.

Mark all these issues as part of the current version milestone. Refer to them as **[Issue:#22]**. For SourceForge, refer to them as **[bugs:#98]**, **[feature-requests:#60]**, **[support-requests:#81]**.

## Test local version of the Web

* build the local Jekyll **gnuarmeclipse.github.io-source** project
* test it using the localhost:4000 address
* Git Push & Sync the **gnuarmeclipse.github.io-source** project; use something like `v3.2.1-201701141320 released` as message
* Git Push & Sync the **gnuarmeclipse.github.io** project; use something like `v3.2.1-201701141320 released` as message

## Publish on the main SourceForge updates site

When all ready, run the `scripts/publish-updates.command`:

    ilg-mbp:~ ilg$ /Users/ilg/My\ Files/MacBookPro\ Projects/GNU\ ARM\ Eclipse/gnuarmeclipse-se-git/scripts/publish-updates.command ; exit;
    Do you really want to publish? (Yes)? Yes
    Updating Eclipse/updates
    Rsync-ing SourceForge Eclipse/updates site
    Password:
    building file list ... done
    deleting features/ilg.gnuarmeclipse.templates.stm_1.6.1.201401111229.jar
    deleting features/ilg.gnuarmeclipse.managedbuild.cross_1.7.1.201401111229.jar
    deleting features/ilg.gnuarmeclipse.debug.gdbjtag.jlink_1.2.1.201401111229.jar
    deleting plugins/ilg.gnuarmeclipse.templates.stm_1.6.1.201401111229.jar
    deleting plugins/ilg.gnuarmeclipse.templates.core_1.1.1.201401111229.jar
    deleting plugins/ilg.gnuarmeclipse.managedbuild.cross_1.7.1.201401111229.jar
    deleting plugins/ilg.gnuarmeclipse.debug.gdbjtag.jlink_1.2.1.201401111229.jar
    ./
    artifacts.jar
    content.jar
    features/
    features/ilg.gnuarmeclipse.debug.gdbjtag.jlink_1.4.1.201402140758.jar
    features/ilg.gnuarmeclipse.debug.gdbjtag.openocd_1.1.1.201402140758.jar
    features/ilg.gnuarmeclipse.managedbuild.cross_1.8.1.201402140758.jar
    features/ilg.gnuarmeclipse.templates.freescale_1.2.1.201402140758.jar
    features/ilg.gnuarmeclipse.templates.stm_1.7.1.201402140758.jar
    features/org.eclipse.cdt.cross.arm.gnu_0.5.5.201310221100.jar
    plugins/
    plugins/ilg.gnuarmeclipse.debug.gdbjtag.jlink_1.4.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.debug.gdbjtag.openocd_1.1.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.debug.gdbjtag.restart_1.1.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.managedbuild.cross_1.8.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.templates.core_1.2.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.templates.freescale.pe_1.1.2.201402140758.jar
    plugins/ilg.gnuarmeclipse.templates.freescale_1.2.1.201402140758.jar
    plugins/ilg.gnuarmeclipse.templates.stm_1.7.1.201402140758.jar
    plugins/org.eclipse.cdt.cross.arm.gnu_0.5.5.201310221100.jar

    sent 3926827 bytes  received 1714 bytes  270933.86 bytes/sec
    total size is 3999834  speedup is 1.02
    Published on the main site.
    logout

    [Process completed]

Do not close the terminal before copy/paste the list to the ChangeLog page!.

## Clean the mess in the local archive folder

-   go to **.../GNU ARM Eclipse/archive**
-   move the latest archive to **releases/plug-ins**
-   move the other archives to **internal**

## Merge develop into master

* in SourceTree, switch to the **develop** branch
* push the **develop** branch to GitHub
* in SourceTree, switch to the **master** branch
* merge the **develop** branch into **master**
* push the **master** branch to GitHub
* switch to **develop**

## Create a new GitHub release

* be sure the **develop** branch is up to date and set as default
* go to the [GitHub Releases](https://github.com/gnuarmeclipse/plug-ins/releases) page
* click **Draft a new release**
* name the tag like **v2.9.3-201508190739** (mind the `-` in the middle!)
* select the **develop** branch
* name the release like **GNU ARM Eclipse plug-ins v2.9.3-201508190739**  (mind the `-` in the middle!)
* as description, copy the first paragraph from the Web release page
* **attach binaries** (drag and drop from the archives folder will do it)
* click the **Publish Release** button

Note: at this moment the system should send a notification to all clients watching this project.

## Publish the Web

* Git Push & Sync the **gnuarmeclipse.github.io-source** project; use something like `v3.2.1-201701141320 released` as message
* wait for the Travis build to complete; occasionally links to not work, and might need to restart the build

Note: the release must exist, otherwise Travis will complain and do not publish the site to **gnuarmeclipse.github.io**.

## Update the release link

In the [GitHub Releases](https://github.com/gnuarmeclipse/plug-ins/releases) page:

* add a link to the Web page `[Continue reading »]()`
* get URL from web [Releases](http://gnuarmeclipse.github.io/developer/releases/) and update the above link

## Add the release downloads badge

The code looks like this:

```
[![Github Releases (by Release)](https://img.shields.io/github/downloads/gnuarmeclipse/plug-ins/v3.4.1-201704251808/total.svg)](http://gnuarmeclipse.github.io/blog/2017/02/25/plugins-v3.4.1-201704251808-released/)
```

## Close issues

For all [GitHub issues](https://github.com/gnuarmeclipse/plug-ins/issues) marked with the current version, close them with a message like _fixed since v3.2.1-201701141320_.

## Publish on SourceForge ()

* go to [SourceForge Files](http://sourceforge.net/projects/gnuarmeclipse/files/Current%20Releases/)
* select the folder corresponding to the latest version (currently **3.x**); create a new one if necessary
* click the **Add File** button
* drag and drop the file (for example ilg.gnuarmeclipse.repository-3.1.1-201606210758.zip) in the upload window and click the **Upload** button
* click the **Done** button
* check it the new file was published; click the info icon
* enable the **Windows**, **macOS** and **Linux** buttons
* after a while the new upload will be marked as latest version

## Share on Facebook

* go to the new post and follow the Share link.
* DO NOT select **On your own Timeline**, but **On a Page you manage**
* select GNU ARM Eclipse
* posting as GNU ARM Eclipse
* click **Share link**
* check the post in the [Facebook page](https://www.facebook.com/gnumcueclipse)

## Update the Eclipse Marketplace records

* go to [Eclipse Marketplace](https://marketplace.eclipse.org/content/gnu-arm-eclipse)
* log in
* click **Edit**
* update version number, minimum Eclipse versions.

