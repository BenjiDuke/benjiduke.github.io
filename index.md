# CSCI 462 Blog Introduction

I'm  Benji Duke, a computer science major at CofC. I've been here for 2 years now, and my projected graduation date is December, 2020. I  completed an Associate's degree in Computer Technology in 2010 at  Midlands Technical College in West Columbia, then took a left turn and  joined the Navy in 2011 to become a nuclear electrician's mate. I left the Navy in 2017 to go back to school and pursue a Bachelor's in Computer Science. I've always had an interest in computers and programming. Hoping to use my degree to get a start on a new career, either in security or development. 

# Reflections on FOSS

First I want to cover reflections on reading [The Cathedral and the Bazaar](http://stono.cs.cofc.edu/~bowring/docs/cathedral-bazaar.pdf), written by Eric S. Raymond. The article covers the development of an open source project, Fetchmail, and how it compares to proprietary software development.

The cathedral is meant to represent proprietary software development, while the bazaar represents open source development. Both models have their pros and cons. The biggest stand out difference to me was the way that debugging is handled in open source development. Open source development is much more fluid by design, in that the people who contribute to the software are often the users themselves. The author has a saying, that "Given enough eyeballs, all bugs are shallow." This is true for open source software development because by having a wide array of users, bugs in the software are much easier to find and catalog. A user that finds a bug and is knowledgeable about how the program works can implement a fix and contribute their fix to the code base with the open source software development model. This contrasts with the way that proprietary software development works. Instead of having a core team working on testing and implementing fixes prior to release, with open source development, the users can contribute their own fixes to the code base, helping the development of the product not only for their own benefit, but for all the other users. By having a lot of different users with different backgrounds, the bug fixes and feature implementations for an open source project can happen much more organically and efficiently than in a "cathedral" style development model. In proprietary development, bug fixes and feature implementations could take months of research and scruity by the core team before scheduling a release, by which time the users of the software may have moved on to a competitor. With open source development, there may be a new build every day with fixes and features that users have contributed to by their own desire to create a better product.

I believe the difference comes from the users of open source software. They are eager to try out each new build and to contribute their own improvements to the source. The same has been true for my team in our efforts to find an open source project to contribute to. Our first choice for a project turned out to not be very "beginner friendly", and we were dissuaded from trying to work on the project. However our next choice, Zulip, an open source group chat program, seems much more welcoming to newcomers. We could attempt to solve an open issue, discover a bug and create a bug report, contribute to the documentation, or attempt to implement a new feature to the project. The only requirement is that we only work on one issue at a time as first time contributors. I'm hopeful that my team will find a worthwhile issue within our capabilities to fix, or a feature worthy enough to spend time implementing that will make the software better for the users. 



# Reflections on Open Source in Today's World

[Use Wireshark at the Linux Command Line with Tshark](https://opensource.com/article/20/1/wireshark-linux-tshark)

This article is by Gaurav Kamathe (Red Hat) and is about how to use the terminal utility for Wireshark, called Tshark.

Wireshark is an open source graphical user interface (GUI) tool for analyzing network traffic. With Tshark, you can use the Linux command line rather than a GUI to look at network traffic. This article shows how to use Tshark, starting by looking at all the network devices connected with the command:
`sudo tshark -D`

The guide then covers how to capture packets for a specific device found with the previous command:
`sudo tshark -i deviceName`

The output for each packet will show two IP addresses, which are the hosts exchanging the packet. An arrow shows the direction the packet is going. Next is the protocol being used by the packet (DNS, TCP, NTP, etc). To limit the amount of packets captured, use the option -c followed by a number. The guide also explains how to use nslookup (or the dig command) to find a domain name's IP address. Opensource.com is used in the example. Using
nslookup opensource.com, I can resolve the IP address for the website. I get 54.204.39.132. Using that, I can capture packets transferred from them to my computer using:
`sudo tshark -i myDevice host 54.204.39.132`

From another terminal, if I were to ping that IP address with
`ping -c 2 54.204.39.132`

Then I'll see that Tshark has captured 4 packets from those 2 pings. 2 requests, and 2 replies.

The article continues on to show how to use other options with Tshark, and explains the TCP handshake, and how encrypted traffic using TLS for HTTPS addresses uses more packets to set up a secure connection. This article was a nice first look at Wireshark, which I'm sure will become useful later for my network security course. 


[How Internet Security Works: TLS, SSL, and CA](https://opensource.com/article/19/11/internet-security-tls-ssl-certificate-authority)

This article is by Bryant Son (Red Hat, Correspondent) and deals with how internet security works by explaining the differences between HTTP and HTTPS, and explains the concept of Transport Layer Security(TLS), certificate authorities (CAs), and how they secure a website. From the artcle: The internet as we know it today is made up of six layers: physical, data, network, transport, security, and application. Security is considered a part of the application layer. This contains TLS and SSL, the cryptographic protocols which ensure secure comminication between the application and the end user.

From what I could gather, the CAs are the vendors that issue the TLS/SSL certificates to websites in order to secure those websites. There is a way to self sign a certificate, and a number of open source tools to generate a certificate, but it is emphasized that this should be used as an option for developing and testing, not for the production stage. The article contained links to more in-depth discussions of how TLS works through a set of public and private keys, which may be worth reading later.

# This Bugs Me

### [TOS 6.4 :](https://quaid.fedorapeople.org/TOS/Practical_Open_Source_Software_Exploration/html/sn-Debugging_the_Code-Exercise_-_Find_the_Oldest_Bug.html)

**Find the oldest bug that's still open in your chosen project. Write a blog entry describing the problem, with a theory about why the bug hasn't been resolved yet. (Bonus points if you can actually resolve the bug.)**

My chosen project is Zulip, an open source group chat program. The oldest open bug in my chosen project is [notification tracebacks with Chrome on Android](https://github.com/zulip/zulip/issues/213). From reading the thread, it sounds like desktop notifications aren't working for Chrome on Android. I think it hasn't been closed yet because it's complicated. The Zulip app itself is available for Android, so it still works on the platform, but this issue is dealing specifically with Zulip in Chrome on Android. So when using Zulip in Chrome, notifications aren't pushed to desktop (or mobile/tablet/Android device). I think since this has gone unsolved so long since it's a niche issue. Or it's just complicated, since it appears this issue has been claimed and abandoned before now.

### [TOS 6.5:](https://quaid.fedorapeople.org/TOS/Practical_Open_Source_Software_Exploration/html/sn-Debugging_the_Code-Exercise_-_Create_Your_Bug_Tracker_Account.html) Create Your Bug Tracker Account
**Figure out how to create a new account on the bug tracker of your chosen project. You'll need that account very soon.**

To track new bugs for this project, I would have to watch the "Issues" tab on the project GitHub. This would notify me by email whenever any new issue is made. 

### [TOS 6.6:](https://quaid.fedorapeople.org/TOS/Practical_Open_Source_Software_Exploration/html/sn-Debugging_the_Code-The_Anatomy_of_a_Good_Bug_Report.html) Reproducing a bug.

Good bug reports will include a way to reproduce the bug. I found a recent one from my chosen project, where the user profile's [full name does not update after editing.](https://github.com/zulip/zulip/issues/13820). The name does reflect the change after closing and reopening the user settings window, but the change for the Full Name field is not immediately reflected after changing. I was able to reproduce the bug in the Zulip for Windows app as well, and it appears someone is already working on it as of yesterday.

### [TOS 6.7:](https://quaid.fedorapeople.org/TOS/Practical_Open_Source_Software_Exploration/html/sn-Debugging_the_Code-Bug_Triage.html) Bug Triage

**Find five bug reports in the new state, and attempt to triage them according to the rules above. Your goal is to do as much as you possibly can, in a short period of time, to make those bug reports as useful as possible to the developer to whom they are assigned.**

I was able to find bugs from looking at the open issues with the "bug" tag on Zulip's GitHub page. They are assigned tags based on what type of issue it is, and are given a priority tag by other developers after they've looked at the issue. The rules for bug reporting are found on [Zulip's reporting guide.](https://zulip.readthedocs.io/en/latest/overview/contributing.html#reporting-issues). The rules say that if you're experienced in bug reports, just open an issue on the Zulip GitHub. If not, then go to the Zulip community server and make a post in the #issues channel describing the problem. Others will determine if this bug has been addressed previously, as in maybe it's already an open issue, and can direct people from there. The only caveat is for security related issues, which are not to be discussed in a public channel. Security issues are reported directly to the security team at their specified email address found in the above link.

### Reflections

Doing these exercises with this project was very informative. From what it looks like, the developers here are on top of their issues. All of the open issues I've looked at were tagged and prioritized by the project lead. Other community members would put in their two cents on replicating the issue, the likely cause of the problem, or where to look to start fixing it. There are a few issues I think our team could contribute to fixing over the course of the semester.
