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

# What's Happening?
## Reflections on chosen article

For this week I've chosen to read the article "Preparing Tomorrow's Faculty to Address Challenges in Teaching Computer Science" in Communications of the ACM, vol 60. The article is about the increased demand in computer science related skills and how school faculty are handling the higher enrollment. The article explores the belief that if there are more students than the faculty can effectively teach, then they be more inclined to believe that success is dependent on a students innate skill, or "brilliance", and that there is little the faculty can do to change the students' outcome in the class. The reality is that there are teaching practices that create student-responsive classrooms, broader participation, and reduced failure rates, even in large classes. The authors explained how they implemented a "boot camp" for new computer science faculty members that better prepare them to teach computer science courses. The objective is to teach new faculty evidence-based teaching practices, and to change how CS faculty view education. 

The article goes on to explain how a handful of universities produce most of the Ph.D.'s who go on to be computer science faculty, and by targeting them for the CD teaching boot camp, they can change how CS faculty view education and teaching. Good teachers are not born, they're made. 

From my own experience as a student I can say that I did initially believe that, with regards to programming, some people either just "got it" or they didn't. After spending a semester as a teaching assistant for an introductory programming course, I'd like to revise that statement. Some students do have a knack for programming, that much is true, but I also found that every student that put forth the effort to learn was able to succeed in the course. All it took most of time was rephrasing something in a way the student could understand in order for them to grasp the concepts the course was trying to teach. I'm glad that there is an effort by the researchers in the article to create better CS faculty by teaching them how to apply these evidence-based best practices. The way we educate people in computer science should constantly be improved upon to keep up with the changes and advancements made in the field.


# Stupid or Solid?
### Reflections on [S.O.L.I.D.](https://williamdurand.fr/2013/07/30/from-stupid-to-solid-code/)

This article brings some important points on the differences between good (SOLID) and bad (STUPID) code using acronyms to highlight important concepts. 
<ul>
  <li><a href="https://en.wikipedia.org/wiki/Singleton_pattern"><strong>S</strong>ingleton</a></li>
  <li><strong>T</strong>ight Coupling</a></li>
  <li><strong>U</strong>ntestability</a></li>
  <li><strong>P</strong>remature Optimization</a></li>
  <li><strong>I</strong>ndescriptive Naming</a></li>
  <li><strong>D</strong>uplication</a></li>
</ul>

I didn't know what the Singleton pattern was prior to reading this. The Singleton pattern restricts the instantiation of a class to one "single" instance. It makes the instance of a class global, and the problem with using this is that it's difficult to test and often a better solution can be made. The author suggests avoiding reliance on singleton classes because they lead to tight coupling. Coupling is the degree to which each program module relies on another. So if you can't change one module without having to change another, or several others, you've got tight coupling. 

These two problems contribute to untestable code. The author goes over how testing code should not be difficult, and if it is then there may be bigger problems. The author then warns about Premature Optimization. When to optimize? 
"A friend of mine often says that there are two rules to optimize an application:"
<ul>
  <li>don’t do it;</li>
  <li>(for experts only!) don’t do it yet.</li>
</ul>
This made sense to me after reading it. I've run into issues on past assignments where I have working code, but realize there are a few improvements that could be made. After the improvements, the code didn't work as expected anymore. So rather than making more efficient code I'd end up troubleshooting the "improved" code and make the assignment take longer to complete than necessary. Lesson learned. 
Indescriptive naming is another part of our STUPID acronym, and it's exactly what you think it is. I'm pretty sure everyone has been guilty of this, especially starting out. For example, Variable names: num1, num2, var... what are these variables? What's the number for? Rather than writing code that requires too many comments to make sense of it, just rename the variables and functions to more descriptive names to make it readable. Duplicated code is where you end up writing the same code in more than one place. The better thing to do would be to write that code in a function and call it where needed. It's usually pretty easy to catch yourself writing the same code, and even easier to throw that code in a function instead. 

<ul>
  <li><strong>S</strong>ingle Responsibility Principle</a></li>
  <li><strong>O</strong>pen/Closed Principle</a></li>
  <li><strong>L</strong>iskov Substitution Principle</a></li>
  <li><strong>I</strong>nterface Segregation Principle</a></li>
  <li><strong>D</strong>ependency Inversion Principle</a></li>
</ul>

SOLID code goes over how each of these key points in how to improve the way you write code. Single Responsibility Principle is about making each part of the code do the one thing it's meant to, and avoid a "god" class that has all the functions rolled into it. Open/Closed Principle means that "software entities should be open for extension, but closed for modification." Easy to expand on, closed to modification. Liskov Substitution Principle means that "objects in a program should be replaceable with instances of their subtypes without altering the correctness of the program." So a subtype could add things, but not lose any functionality of its parent type. Sounds like a good idea to me. Interface Segregation Principle states that "many client-specific interfaces are better than one general-purpose interface." It makes sense to start with a general purpose interface and modify it into a client-specific one. The author says this produces low coupling and high cohesion. High cohesion keeps similar elements together, and low coupling means that each module isn't needlessly tangled with another. The Dependency Inversion Principle is about coding to the interface, which reduces dependency and makes code more reusable. All of these things together make code easier to understand, by having more descriptive names and having each function/module be single-use. Solid advice for programmers. 


# Release early and often
#### Reflections on [TOS Chapter 8 and 9](https://quaid.fedorapeople.org/TOS/Practical_Open_Source_Software_Exploration/html/ch-Explaining_the_Code.html) and Chapter 8: Preparing to Deploy, from the textbook.

This textbook chapter goes over how to do technical writing and documentation. It goes over a few things I did not think about, like using [Simplified English](https://simple.wikipedia.org/wiki/Simplified_English), which is roughly 1,000 English words that have only one meaning. The point is to avoid confusion. Not everyone who uses the software or reads the documentation is a native English speaker. This would also make localization easier, if the documentation were to be written in another language. 

The key points for good technical documentation are: Organization, Illustration, Style, and Tone.
Planning the layout is important for keeping everything organized so the points flow logically from one to the next. Illustration can be use of an image or video to explain something. Some things are easier to convey via imagery, and it's good to know when to use an illustration to better explain something. Style is about word order, grammar, sentence length, etc. Like, for example, how I tend write run on sentences, or overuse a comma to create a pause, because it just looks right to me, and because I would put a pause there if I were speaking the same words I am writing. Tone involves the attitude of the writer towards the reader. It can be peer-to-peer, where the same language used and knowledge level is implied, or mentor-student, where the writer has to adapt to the language used. 

Good documentation is meant to answer any questions the reader of the documentation has. It should directly answer a question a user may ask, and cover all situations users may encounter while using the software. If a user runs into a problem or something unexpected and cannot find an answer in the documentation, then that's bad documentation.

The Teaching Open Source examples also covered documentation, and had a few exercises to do with peers. Coming from working on our open source project, I can say that the community will let you know when something requires documentation. If a user asks a question about something within the code, then the answer should generally be added to the documentation and commented in the code. 

# Chapter 5
#### Domain Class Development

This chapter covered a lot of useful information pertaining to testing. The chapter mentions three significant areas when developing new code: coding, unit testing, and system testing. Coding involves not just writing new code from scratch, but also reusing code, or picking a code base to build off of to customize to meet your project's needs. Unit testing is the testing of an individual module, to ensure the setters and getters return the proper values, and that they work as intended. Tests should be done on individual modules during unit testing before starting system testing. 

System testing involves merging the results of each team member's coding & testing efforts, and testing them together under an "integration test." Ensures combined work of individual developers has no conflicting overlaps or inconsistencies.

This reminds me of what was covered in CSCI-362, where the team I was working with had to develop a testing framework for a FOSS project. We made a bunch of unit tests to test the projects functions, where the test output was checked against the oracle, or expected output. The tests would fail if the software encountered an unexpected error, or if the unit test was improperly formatted.  

Unit tests are typically written to construct an object and check the function of its getters and setters to be sure they return the proper value, and work how they are supposed to. 

The chapter mentions that unit testing each module individually should lead to integration testing, where the interactions between modules that depend on other modules are tested. Debugging - removing defects or flaws in code that contribute to a failure when the software is running. A failure is unacceptable behavior in software as observed by the user.
Before adding new features, make sure software is receptive to them. Remove "bad smells," like duplicate code, poorly named variables, or update some unreadable code with comments. There are some parallels between "STUPID" code and the "bad smells" the author covered. Remove "bad smells," like duplicate code, poorly named variables, or update some unreadable code with comments. Towards the end of the chapter there's a list of these common bad smells. Pretty much all of them were covered in the "From STUPID to SOLID code" article by William Durand, although they may be called something different. Poorly named variables seem to be a universal problem. As does too few or too many comments. The problem with too many comments is that if the code requires many comments to describe its function, then it could probably be rewritten to be more readable. 

The chapter goes over a bit about the Issues tab on GitHub for the Homeplate software project, mostly just the terminology used. It's a good platform for receiving some client feedback, and a good place to interact or suggest things to a projects developers. 
