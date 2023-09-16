# Ultimate OpenCart Profiler

<!---
[Українською](README_uk.md)
-->

This is the description/presentation and the issue tracker for the Ultimate OpenCart Profiler module by nekto.

The module itself is not free and is not open-source, and can be bought elsewhere. This is only a place to report and track its bugs.

## What is this module for and what it accomplishes

Profile and debug OpenCart code and SQL requests like never before, in a new unprecedented way.

![image](https://opencart-profiler.nekto.com.ua/image/public/profiler-screen-1.png)

Warning: This is a module for developers, which provides a very detailed profiling/debugging of the code and SQL queries execution in OpenCart, displayed in multiple ways and perspectives, separately and grouped together.

**Important information before you buy:**\
This is a strictly programmers-only hardcore utility, which has no use for non-developers.\
This module DOES NOT improve performance, it DOES NOT provide any hints, recommendations or advice. It is a diagnostics tool to find/reveal all the slow places and irregularities precisely, fast and easy.

## Features

Visiting the demo is highly recommended: https://opencart-profiler.nekto.com.ua/

Out of the box, the module is basically showing the logic of the code execution on any page:
- the sequence of controllers run on the page,
- which models were called by which controller, and how many times,
- which SQL queries are related to the controllers and models,
- everything is timed, measured (duration and place inside TTFB) and, of course, traced.

![image](https://opencart-profiler.nekto.com.ua/image/public/code-seq-steps-example.png)

The module essentially displays the detailed sequence of code and it's relation to SQL queries, with duration of execution and full trace for each profiling point.\
And even the most basic list allows to spot anomalies instantly (in SQL or in the code).\
You are able to (and are supposed to) add your own profiling points anywhere in the code wherever you need it, which is done with one simple command (found in the module's built-in Manual).

A typical scenario to find and fix the reason of why an OpenCart website or page is slow:\
1\. Look at the overall code and SQL durations at the bottom left: what takes the most time?\
2a. If code takes the most time:\
3a. Look into Code Seq, find the biggest time gaps between the steps.\
4a. Add your own new steps between those, until you find the slowest piece of code.\
5a. Improve the code performance.\
2b. If SQL takes the most time:\
3b. Look at SQL Time, fix the slowest queries, if possible.\
4b. Look at Same SQL, eliminate high-volume duplicates.\
5b. Look at Similar SQL, rewrite the code to run less queries (consider using some CPU to read bigger data sets from the database to the PHP variables).

You must account for SQL duration between the measured points. If one step is at 100 ms TTFB, and the next step is at 150 ms TTFB, but there are 30 ms of SQL duration between them, the code execution actually took 20 ms, not the whole 50 ms (second step TTFB _minus_ first step TTFB _minus_ SQL duration, or 150 - 100 - 30 = 20).

The module has five different perspectives:
- Code Seq (explained above)
- SQL queries in order of execution
- SQL queries from slowest to fastest
- Same SQL queries
- Similar SQL queries

![image](https://opencart-profiler.nekto.com.ua/image/public/the-modes.png?2)

Bottom left of the module displays the overall time SQL requests and code execution took (separately).

![image](https://opencart-profiler.nekto.com.ua/image/public/code-sql-numbers-and-durations.png)

**SQL Seq** and **SQL Time** allow leaving only queries containing a desired arbitrary substring visible and display instant summary: how many queries contain that substring and their combined duration.

![image](https://opencart-profiler.nekto.com.ua/image/public/sql-filtering-example.png)

**Same SQL** lists exactly the same queries, which were run multiple times. It's my personal favourite and an often very surprising list.\
A recommended starting place when looking for performance improvement opportunities.

![image](https://opencart-profiler.nekto.com.ua/image/public/same-sql-examples.png)

**Similar SQL** list contains the same queries run in some loops with different values in WHERE (making those not literally exactly the same queries, because the parameters are different).\
Every query is measured and their whole duration is also calculated.\
More queries aren't always slower, it all depends on the queries, indexes, server settings and server resources available at the time of requests!\
Don't improve what isn't slow!

![image](https://opencart-profiler.nekto.com.ua/image/public/similar-sql-example-many-but-fast.png)

![image](https://opencart-profiler.nekto.com.ua/image/public/similar-sql-example-few-but-slow.png)

The profiler panel doesn't block website navigation in any way, it can be maximized to full screen height, half-screen (default), or minimized to only occupy a tiny footprint in the corner.

![image](https://opencart-profiler.nekto.com.ua/image/public/size-arrows-smallest-size.png)

I believe every serious OpenCart developer and website development studio must have this module, as it displays everything clearly and comprehensively.

It opens new perspectives, laying out detailed internal OpenCart logic in general and for every custom project in particular.\
I've been writing OpenCart code for years, but this module still shows me things I haven't known or understood in full before.

Side note: please, do not buy this module with intention to profile websites running on single-core servers - the measurements will be screwed and not informative, it won't help realistically improve performance.

# Translations

The module comes with English and Ukrainian translations.

# License

The licensee is allowed to use and modify the code in any way they want.\
The licensee cannot sublicense the use of the code.\
The licensee is prohibited to redistribute the original or modified code.\
The licensee gets lifetime support and upgrades.\
The license is per-owner, NOT per-domain. The licensee can use the module on any amount of domains and websites.\
All executables, icons, source code, modules, design of forms, and all other aspects of this software is copyright Misha Grafski (The Author). All rights are reserved.\
All responsibility of The Author and distributors of the software is waived. The Author is not responsible for any loss, injury, damage, death, or charges incurred, due to the use, misuse, abuse, installation, or uninstallation of this software.\
All aspects of this software are entirely at The User's risk.

# Installation and use

Warning: Install the module on a copy of a project first, don't immediately install on the production website and always have fresh backups at hand.\
Warning: This module conflicts with other SQL profiling/timing modules!

- Install the zip via Extensions/Installer in the admin side
- Go to Extensions/Modifications, click the Refresh modifications button
- Go to Extensions/Extensions, choose Modules, locate the "Ultimate OpenCart Profiler" module
- Click [+] to install the module
- Click "Edit" the "Ultimate OpenCart Profiler" module, click "Enable"
- Profiling information will now be displayed on all front side pages ONLY FOR YOU, while you are in the same browser, until you administration session lasts
- When the administrator session expires, you need to enable the module again ("Edit" the module and click "Enable" inside again)

![image](https://opencart-profiler.nekto.com.ua/image/public/module-looks.png)
