# Allegro Common Lisp FAQ

\[Last updated on: 2019-08-08.\]

<div>

This is a list of frequently asked questions on the use of Allegro
Common Lisp. Each question applies to all currently supported Allegro
Common Lisp versions unless otherwise noted with version specific
information. Likewise with Architecture specific information.

Please read this document before sending mail reporting problems to
<support@franz.com>. Periodically, also, some items from this list will
be incorporated into our documentation (and dropped from here). Other
items stay in the FAQ more or less permanently.

</div>

<div class="top-questions">

<div>

## The most popular FAQ entries

* [\[Express\] Does the Express Edition expire?](#expresslicense)
* [\[Express\] What is the best way to update the Express Edition?](#updatingexpress)
* [\[Express\] and 32-bit Edition does not work on Ubuntu](#ubuntu32bit)
* [How do I install patches?](#s-patches)
* [Why on Linux does Allegro CL die on startup?](#selinux)
* [My memory gobbling loop causes the gc to perform badly. Why?](#memgobble)
* [How can I specify very large heap sizes for 64-bit versions of Lisp?](#largeheaps)

## Most recent FAQ entries

* [Why is equal hash table access slow when the keys are structure objects?](#structureht)
* [Which versions and platforms have symmetric multiprocessing (SMP) extensions?](#smpversions)
* [\[Express\] What is the best way to update the Express Edition?](#updatingexpress)
* [What issues must I be aware of when using excl.osi:fork](#fork) 
* [\[Express\] and 32-bit Edition does not work on Ubuntu](#ubuntu32bit)

</div>

</div>

<div class="top-questions">

## [Administrative Issues](#s-admin)

* [What is the current version of Allegro CL?](#s1q1) 
* [How should I report bugs?](#howtoreportbugs)
* [Sometimes CL output is not logged in the dribble-bug file. What do I do about this?](#s1q3)
* [Is there a mailing list for Allegro CL? How do I sign up?](#s1q4) 
* [Is the ACL documentation available on-line?](#s1q5)
* [Are documentation updates available after Allegro CL is released?](#s1q6)
* [Does Allegro CL run on operating system *X*?](#s1q7) 
* [What is the best question to ask us as to my particular operating
system and Allegro CL?](#s1q8)

## [Patches](#s-patches)

* [How do I install patches?](#s2q1)
* [Is there a list of available patches?](#patch-list)
* [How do I manually download patches if I am unable to use (sys:update-allegro)?](#s2q3)
* [Why can't I get update.exe to run on Windows?](#pvista)

## [Express Edition installation and license file issues](#s-express)

* [\[Express\] What is the best way to update the Express Edition?](#updatingexpress)
* [\[Express\] \[Windows\] Can I install the Express Edition if I do not have access to the internet?](#s3q3)
* [\[Express\] \[Windows\] Is my antivirus software correct that the Express Edition is a virus?](#s3q4)
* [\[Express\] How long can I use the Express Edition?](#s3q5)
* [\[Express\] Does the Express Edition expire?](#expresslicense)
* [\[Express\] The date in the license file (devel.lic) is in the future, but when I run Allegro CL it says my license has expired. Why might this happen?](#s3q6)
* [\[Express\] How do I build mlisp, alisp, or allegro images?](#s3q7)

## [Professional/Enterprise Edition installation and license file issues](#s-proent)

* [How do I install the license file?](#howtolicensefile)
* [I have misplaced the email telling me the URL from which I can download
your license?](#lfmissingemail)
* [I can not access the URL for retrieving my license. What should I
do?](#lfcannotaccessurl)
* [I still have problems with my license file. Can I contact you for
assistance?](#s4q4)

## [Using Allegro Common Lisp](#s-usingacl)

* [\[Express\] and 32-bit Edition does not work on Ubuntu](#ubuntu32bit)
* [\[Express Edition\] Can I use the SSL interface in Allegro CL Express
Edition?](#s5q2)
* [Why doesn't make-pathname merge the given :directory component with the
directory component in :defaults argument?](#s5q3)
* [I am getting stack overflows and occasional Lisp failure when I sort on
large arrays. Why and what can I do?](#s5q4)
* [I have set the stack cushion (see sys:set-stack-cushion and
sys:stack-cushion) to a reasonable value, but the soft stack limit is
not being detected, and I get a lisp death instead. Why is that?](#s5q5)
* [Why does it take so long to load a file that interns several thousand
symbols in a package?](#s5q6)
* [Why is equal hash table access slow when the keys are structure
objects?](#structureht)
* [Why doesn't tracing a self-calling function trace the inner calls?](#tracerecurse)

## [Heap placement issues](#s-heap)

* [How can I specify very large heap sizes for 64-bit versions of
Lisp?](#largeheaps)
* [Sometimes Allegro CL, particularly with large images, fail totally with
a bus error or a segv. Why might this be happening?](#s6q2)
* [Sometimes Allegro CL, particularly with large images, run out of memory
with a storage-condition. Why might this be happening?](#s6q3)
* [How is heap placement determined and what can go wrong?](#s6q4)
* [How does Lisp start up, in terms of shared-library linking and
loading?](#s6q5)
* [How can I tell where my image's heaps are located, and what size they
are?](#heaplocations)
* [How can I tell what addresses are being used in my process
space?](#addressspace)
* [\[Windows only\] How do I move DLL in memory so that it doesn't
conflict with the Lisp heap?](#rebasedll)
* [What does the "Temporarily scaling back lisp reserved region from XXX
to YYY bytes." mean?](#s6q9)
* [What should I know when choosing non-default heap locations?](#s6q10)
* [How do I build an image with non-default heap sizes and/or
locations?](#s6q11)
* [How do I build default images provided by Franz with non-default heap
sizes and/or locations?](#s6q12)
* [Can I specify heap locations and/or sizes when starting lisp?](#s6q13)

## [Garbage Collection](#s-gc)

* [My memory gobbling loop causes the gc to perform badly.
Why?](#memgobble)

## [Foreign Functions Interface](#s-ffi)

* [How do I pass and return 64-bit integers through the FFI?](#s8q1)

## [CLIM](#s-clim)

* [How can I replace the lesstif installed with RedHat Linux 7.2 with
openmotif (required for CLIM)?](#s9q1)

## [Composer](#s-composer)

* [When starting Composer I get the error `'Error: "Connection refused"
(errno 111) occurred while creating a local socket and connecting to a
remote host ... on port 6000.'`](#s10q1)

## [Compatibility between 32 and 64-bit versions of Allegro CL](#32-64-compat)

* [What changes are needed to move from a 32-bit to 64-bit Allegro
CL?](#s11q1)
* [Why does my 64-bit foreign call cause a SIGSEGV?](#s11q2)

## [Misc](#s-misc)

* [What issues must I be aware of when using excl.osi:fork](#fork)
* [Do you have an interface to Python?](#python)
* [Sometimes TIME results produce negative values. Why?](#s12q3)

## [Multiprocessing](#smpversions)

* [Which versions and platforms have symmetric multiprocessing (SMP)
extensions?](#s13q1)

## [Windows (architecture specific)](#s-windows)

* [My lisp immediately crashes a few seconds after startup. What's causing
this?](#dep)
* [Why can't I use \`dir' with run-shell-command?](#s14q3)
* [How do I control the stack size on Windows?](#s14q4)
* [How do I get ANSI ACL (rather than Modern ACL) to start when I
double-click on an lpr file?](#s14q5)
* [Why is the compiler complaining about a missing in-package form when I
am certain that my **offline file** starts with one?](#s14q6)
* [Why does the right Alt key not work the same as the left Alt key?](#rightAlt)

## [Linux (architecture specific)](#s-linux86)

* [Why on Linux does Allegro CL die on startup?](#selinux)
* [On which x86 (i.e., Intel Pentium and friends) Linux versions do the
currently supported versions of Allegro CL run?](#s15q2)
* [How can I replace the lesstif installed with RedHat Linux 7.2 with
openmotif (required for CLIM)?](#clim-lesstif-linux86)

## [Mac OS X (architecture specific)](#s-macosx)

* [Why do I get crash reports when running 32-bit PPC Allegro CL?](#s16q3)

## [Using Common Lisp (non-Allegro specific)](#s-using-cl)

* [Why does read-from-string ignore my first keyword argument (unless I
also specify both optional arguments)?](#s17q1)
* [Why does read-from-string signal an end-of-file error even when I pass
the eof-error-p argument as nil?](#s17q2)

</div>

## <span id="s-admin">Administrative Issues</span>

<span id="s1q1"></span>

### Q. What is the current version of Allegro CL?

The current version of Allegro CL is shown on [this
page](https://franz.com/products/allegro-common-lisp/index.lhtml). This
FAQ applies to Allegro CL 9.0 and any version with
major version number 10 (e.g. 10.0 or 10.1). It is noted where the
version number is relevant to a FAQ answer.

<span id="s1q2"></span>

### <span id="howtoreportbugs" style="color:red">Q. How should I report bugs?</span>

What should be included in a bug report is described in the section
[Reporting
Bugs](https://franz.com/support/documentation/current/doc/introduction.htm#reporting-bugs-1) in
[\<Allegro
directory\>/doc/introduction.htm](https://franz.com/support/documentation/current/doc/introduction.htm).

In short, you should include a transcript that demonstrates the failure
and error/result seen. Transcripts can be made in a number of ways, such
as from an emacs buffer. A logging facility in Allegro CL is also
available. Use the function
[dribble-bug](https://franz.com/support/documentation/current/doc/operators/excl/dribble-bug.htm),

To start a session transcript evaluate `(dribble-bug "dribble.txt")`.
This will open the file dribble.txt and write a header containing
information about the current lisp environment, which is of help to us
when debugging problems. Upon return from this function call, your lisp
session is now being logged.

Once finished, evaluate `(dribble-bug)` (no arguments) to close the
dribble bug stream.

The header information is generated by a call to the function
[print-system-state](https://franz.com/support/documentation/current/doc/operators/excl/print-system-state.htm).

We prefer not to receive screen shots unless there is no other way to
transmit info.

<span id="s1q3"></span>

### Q. Sometimes CL output is not logged in the dribble-bug file. What do I do about this?

If you are using
[dribble-bug](https://franz.com/support/documentation/current/doc/operators/excl/dribble-bug.htm)
to record output note that
[dribble-bug](https://franz.com/support/documentation/current/doc/operators/excl/dribble-bug.htm)
should only miss output produced when using the foreign-function
interface or running a shell function with
[run-shell-command](https://franz.com/support/documentation/current/doc/operators/excl/run-shell-command.htm)
and friends, or (because it is produced by C code) information printed
by the garbage collector during a garbage collection. Some messages from
foreign code may be written directly to Unix stdout or stderr, bypassing
Lisp entirely. To circumvent this problem, you can either use an Emacs
buffer or the Unix utility "script" to save the entire transaction
record.

<span id="s1q4"></span>

### Q. Is there a mailing list for Allegro CL? How do I sign up?

There is not. Please send mail to <support@franz.com> for technical
inquiries or <info@franz.com> for all other questions or comments.

<span id="s1q5"></span>

### Q. Is the ACL documentation available on-line?

Yes, at
[http://franz.com/support/documentation/](https://franz.com/support/documentation/). It
is updated from time to time and the instructions for downloading the
updated documentation are included in the above link.

<span id="s1q6"></span>

### Q. Are documentation updates available after Allegro CL is released?

Our documentation is frequently updated online after a major release.
The updated documentation is [available for
downloading](https://franz.com/support/documentation/).

<span id="s1q7"></span>

### Q. Does Allegro CL run on operating system *X*?

Our policy of support of Allegro CL on specific operating system
versions is as follows:

For each released version of Allegro CL, we compose a list of [current
operating system levels](https://franz.com/products/allegrocl/#osinfo) on which we have
tested and on which we know our product will work. This list is also
located in [installation.htm in the section Installation sizes and
supported Operating System
versions](https://franz.com/support/documentation/current/doc/installation.htm).

Because Allegro CL runs on so many different operating systems, and
because some of these operating systems have almost infinite
combinatorial possibilities, including patches and/or user-modification,
we do not attempt to certify Allegro CL on specific operating system
versions. Instead, we rely on the tendency of the operating system
vendors to maintain upward compatibility, and we usually build on the
lowest operating system version for which we have listed support. As
long as the operating system is truly upward compatible, Allegro CL
should work on the newer versions, and our advice is to try it out. But
we also recommend strongly that you run such tests on a machine that is
not part of your production process, in case things don't go well.

<span id="s1q8"></span>

### Q. What is the best question to ask us as to my particular operating system and Allegro CL?

If the operating system you are interested in running Allegro CL on is
the same lineage and the underlying architecture is the same as one
which we have already listed as supported, the best question to ask us
is

  - Have you had any compatibility issues with running Allegro CL on
    Operating system XYZ?

We can answer this question "yes" or "no", which will tell you as the
customer whether we have any negative experiences with the operating
system version. (The information [here](https://franz.com/products/allegrocl/#osinfo) may
also provide the answer.) If the operating system is very new, the
answer to this question might more likely be "no", because the
assumption is that the new version is compatible, unless and until it
proves otherwise. Other questions that you might ask, if you know that
your operating system is very new, are

  - Do you know of customers who are successfully running Allegro CL on
    Operating system XYZ?
  - Do you have plans to support Allegro CL on Operating System XYZ?

The fundamental issue with Allegro CL working on a new operating system
versions is whether the operating system has any fundamental issues that
break Allegro CL. Typically, when the operating system is a natural
progression from one which we currently support, we will take specific
steps to resolve incompatibilities. Incompatibilities most often occur
when an operating system vendor changes the signal-handling interface,
usually to be more Posix compliant. The change can break Allegro CL.
This has happened in the last several years to Linux, LinuxPPC, FreeBSD,
and macOS, in that time order.

## <span id="s-patches">Patches</span>

<span id="s2q1"></span>

### Q. How do I install patches?

The various processes for installing patches are described at
[http://franz.com/support/patches/](https://franz.com/support/patches/)

<span id="s2q2"></span>

### <span id="patch-list">Q. Is there a list of available patches?</span>

Yes. In fact, even if you are using
[sys:update-allegro](https://franz.com/support/documentation/current/doc/operators/system/update-allegro.htm)
to download patches, we highly recommend viewing this file periodically
so that you are aware of what each patch being downloaded is affecting.

There are LOG files for each supported version of Allegro CL. The LOG
file for the current (i.e. latest) version is always at

  - [http://franz.com/support/patches/log/current/index.lhtml](https://franz.com/support/patches/log/current/index.lhtml)

LOG files can also be accessed with the version number, so for 10.1 (the
current version) use the link above or

  - [http://franz.com/support/patches/log/10.1/index.lhtml](https://franz.com/support/patches/log/10.1/index.lhtml)

For 10.0 and 9.0 use:

  - [http://franz.com/support/patches/log/10.0/index.lhtml](https://franz.com/support/patches/log/10.0/index.lhtml)
  - [http://franz.com/support/patches/log/9.0/index.lhtml](https://franz.com/support/patches/log/9.0/index.lhtml)

We also provide [RSS Feeds](https://franz.com/rss.lhtml) to Patch releases for current
Allegro CL Versions, and both technical and general announcements. You
can check the patch LOG page above periodically or subscribe to one of
the RSS feeds to be informed automatically.

<span id="s2q3"></span>

### Q. How do I manually download patches if I am unable to use (sys:update-allegro)?

We maintain a publically accessible FTP site from which users can
download all available patches. Please visit:
<ftp://ftp.franz.com/pub/patches/current/>. From the parent directory,
one can also access patches for past versions of Allegro CL.

This directory contains a
[README](ftp://ftp.franz.com/pub/patches/current/README) file with
instructions for manually downloading patches toward the bottom of the
file.

As patches become available, the files in this directory will be
updated, so it is a good idea to be aware of when patches are released.
The FAQ item [here](#patch-list) provides information on how you might
do so.

For a general explanation on how to find and load the patches for your
version of Allegro CL see
[http://franz.com/support/patches/](https://franz.com/support/patches/).

<span id="s2q4"></span>

### <span id="pvista">Q. Why can't I get update.exe to run on Windows?</span>

Updating patches is a two-step process: first patches are downloaded,
perhaps with the function
[sys:update-allegro](https://franz.com/support/documentation/current/doc/operators/system/update-allegro.htm)
or with another method as described in the [Patches
section](https://franz.com/support/documentation/current/doc/introduction.htm#patches-2);
then all running Lisps are exited and the **update.exe** program (in
the Allegro CL installation directory and also invoked by one of the
Allegro CL menu items) is run. If you are having trouble running
**update.exe**, it may be because you must run it as Administrator. To do
so, right click on the **update.exe** menu item in
the Allegro CL menu group and choose *Run as Administrator*.

## <span id="s-express">Express Edition installation and license file issues</span>

<span id="s3q1"></span>

### <span id="updatingexpress">Q. \[Express\] What is the best way to update the Express Edition?</span>

See [this](https://franz.com/products/express/) for current information.

<span id="s3q3"></span>

### Q. \[Express\] \[Windows\] Can I install the Express Edition if I do not have access to the internet?

Yes. Much earlier versions of Allegro CL did require internet access for
installation but current versions do not.

<span id="s3q4"></span>

### Q. \[Express\] \[Windows\] Is my antivirus software correct that the Express Edition is a virus?

No. If you downloaded the software from our web site, we believe your
antivirus software is giving you what is called a *false positive*.
OfficeScan from Trend Micro, and other Trend Micro antivirus products
have been known at various times to give false positives on Allegro
products (not just our Express Edition). Each time this happens we
contact them and they fix the problem in an update of their software.

<span id="s3q5"></span>

### \[Express\] How long can I use the Express Edition?

You can use it until the next release of the Express Edition has been
out for some time. We usually give Express users 6 months or more to
migrate to the new version.

<span id="expresslicense"></span>
### Q. \[Express\] Does the Express Edition expire?

Yes, we install a license file along with all the other
files for the release. This built-in license file will typically last 2
years. Should a new version of the Express not come out before this
expiration, we will post a new license file [here](https://franz.com/products/express/).
Usually, however, we will either come out with a new major version or an
updated release with a new license file.

<span id="s3q6"></span>

### Q. \[Express\] The date in the license file (devel.lic) is in the future, but when I run Allegro CL it says my license has expired. Why might this happen?

This can happen when the date on your computer is incorrectly set to a
date in the future later than the license expiration date. Allegro CL
will not start because it thinks the license has expired. You can
check the date on your computer by looking at the Date/Time entry on
the Control Panel.  Please consult your Windows documentation for
information on resetting the date on your computer.

<span id="s3q7"></span>

### Q. \[Express\] How do I build mlisp, alisp, or allegro images?

**Windows**: paste this into the Debug window to build one of
**mlisp.exe** or **alisp.exe**:

``` 
;; mlisp:
(progn
  (build-lisp-image "sys:mlisp.dxl" :case-mode :case-sensitive-lower
            :include-ide nil :restart-app-function nil
            :restart-init-function nil)
  (when (probe-file "sys:mlisp.exe") (delete-file "sys:mlisp.exe"))
  (sys:copy-file "sys:allegro-express.exe" "sys:mlisp.exe"))

;; alisp:
(progn
  (build-lisp-image "sys:alisp.dxl" :case-mode :case-insensitive-upper
            :include-ide nil :restart-app-function nil
            :restart-init-function nil)
  (when (probe-file "sys:alisp.exe") (delete-file "sys:alisp.exe"))
  (sys:copy-file "sys:allegro-express.exe" "sys:alisp.exe"))

;; allegro:
(progn
  (build-lisp-image "sys:allegro.dxl" :case-mode :case-sensitive-lower)
  (when (probe-file "sys:allegro.exe") (delete-file "sys:allegro.exe"))
  (sys:copy-file "sys:allegro-express.exe" "sys:allegro.exe"))
    
```
> Evaluating any of the above forms does not add a menu item to the
> Start Menu. To run the resulting image, you will need to run the
> executable created in each form.


**UNIX**: evaluate the following form to build **mlisp** image from a
running **alisp**:

``` 
(progn
  (build-lisp-image "sys:mlisp.dxl" :case-mode :case-sensitive-lower
            :include-ide nil :restart-app-function nil)
  (when (probe-file "sys:mlisp") (delete-file "sys:mlisp"))
  (sys:copy-file "sys:alisp" "sys:mlisp"))
    
```


## <span id="s-proent">Professional/Enterprise Edition installation and license file issues</span>

<span id="s4q1"></span>

### <span id="howtolicensefile">Q. How do I install the license file?</span>

You should have received an email containing a URL from which you can
download your license file. ([Click here if you haven't received that
email or if you have mislaid it.](#lfmissingemail) [Click here if you
cannot access the URL.](#lfcannotaccessurl))

1.  The email we sent you in response to your download order contains a
    customized URL to your license file. Click on that URL or copy it
    into a browser to retrieve your license file.

2.  Save the text to a file called *devel.lic*. (the name is "devel" and
    the file type or extension is "lic".) On Linux, this is usually not
    a problem, but because Windows usually hides file extensions some
    users have problems getting Windows to save the file correctly. When
    you view this in the Windows Explorer, its file type must show as
    lic, not txt or text or anything else. Therefore, you must be
    careful to save this file so that its type is lic and its contents
    are plain text. Each version of Windows has a slightly different
    method of identifying and listing file types. Please refer to the
    "Windows Users" section to identify how to do this on your
    individual machine. In some instances, Windows will automatically
    save the file as an HTML file (devel.lic.htm), adding an HTML header
    and footer. These headers will prevent the license file from
    working.

3.  If you used the "lost license" URL to obtain your license file, be
    sure that you save only the license file portion of the email into
    devel.lic. If you save the entire email message, MIME headers and
    all, it will prevent the license file from working.

4.  Put the devel.lic file into the Allegro directory.

<span id="s4q2"></span>

### <span id="lfmissingemail">Q. I have misplaced the email telling me the URL from which I can download your license?</span>

**NOTE: Express licenses are part of the download so this item does
  not apply to Express.**

We can send the license to you by email. (The link is to
<http://franz.com/lfs/lostlicense> and on that page, you are asked for
the email address you entered when you requested the license; entering
the email address and clicking the Submit button will cause your license
file(s) to be emailed to you. Please wait after clicking Submit for the
message saying the request was successful. If no license associated with
the email address is in the database, the message \`No licenses found'
is displayed. If that happens, send a message to <support@franz.com>. Be
sure to tell us the email address you used in the body of the message.)

<span id="s4q3"></span>

### <span id="lfcannotaccessurl">Q. I can not access the URL for retrieving my license. What should I do?</span>

Typically, this problem occurs because your system is behind a firewall
or you must use a proxy server. Our license file server rarely
experiences any significant downtime.

You should make sure that you should not be using a proxy server to
access sites outside of your network and that your browser is configured
appropriately. If you do not know if you should be using a proxy server,
or don't know what one is, you should check with your Network
Administrator for assistance. If your system does not require a proxy
server, then perhaps you are behind a firewall that does not give access
to certain ports.

If the proxy server is not the problem, please email Franz Inc. at
<support@franz.com> stating that you are unable to access the URL for
retrieving your license (include the URL), and we will have the
license(s) sent to the email under which you have registered.

<span id="s4q4"></span>

### Q. I still have problems with my license file. Can I contact you for assistance?

Yes. Questions or problems should be sent to <support@franz.com>. Please
be sure to include the following information:

  - what happened, and what steps you took;
  - a copy of your current license (devel.lic) file;
  - a copy of any error messages that you received; and
  - your current email address and daytime telephone number

## <span id="s-usingacl">Using Allegro Common Lisp</span>

<span id="s5q1"></span>

### <span id="ubuntu32bit">Q. \[Express\] and 32-bit Edition does not work on Ubuntu</span>

Ubuntu no longer provides the 32-bit compatibility module needed to run
a 32-bit Lisp (Allegro CL Express is a 32-bit Lisp). Therefore, Allegro
CL 32-bit including Allegro CL Express will not run on Ubuntu. Other
Linux implementations (such as Centos 6.5) do provide 32-bit support.

<span id="s5q2"></span>

### Q. \[Express Edition\] Can I use the SSL interface in Allegro CL Express Edition?

No. While the SSL module *fasl* file was included in the Express, it was
not intended that the SSL interface be available in the Express Edition.
If you have the need for an SSL interface, we gladly urge you to contact
us at <info@franz.com> for an evaluation of our Professional or
Enterprise Editions.

<span id="s5q3"></span>

### Q. Why doesn't make-pathname merge the given :directory component with the directory component in :defaults argument?

Section 19.4.4 of the ANSI spec says:

> After the components supplied explicitly by host, device, directory,
> name, type, and version are filled in, the merging rules used by
> merge-pathnames are used to fill in any unsupplied components from the
> defaults supplied by defaults.

unsupplied is the crucial word here. By specifying a :directory argument
you have supplied the directory component, and the directory component
of the :defaults argument is not used. Even specifying :directory nil
explicitly supplies a directory component of nil, and this will be
treated differently from unsupplied.

<span id="s5q4"></span>

### Q. I am getting stack overflows and occasional Lisp failure when I sort on large arrays. Why and what can I do?

Here is a transcript showing a stack overflow. Note that the array has
one million (10^6) elements.

``` 

USER(1): (setq pippo (make-array 1000000 :initial-element 0)) 
#(0 0 0 0 0 0 0 0 0 0 ...)
USER(2): (sort pippo #'<)
Error: Stack overflow (signal 1000)
[condition type: SYNCHRONOUS-OPERATING-SYSTEM-SIGNAL]

Restart actions (select using :continue):
 0: continue computation
 1: Return to Top Level (an "abort" restart)
[1c] USER(3): :pop
=================^^^^
USER(4): (sort pippo #'<)
#(0 0 0 0 0 0 0 0 0 0 ...)
USER(5): 
    
```

Here the computation continues and Lisp exits with a segmentation
violation:

``` 

USER(1): (setq pippo (make-array 1000000 :initial-element 0))
#(0 0 0 0 0 0 0 0 0 0 ...)
USER(2): (sort pippo #'<)
Error: Stack overflow (signal 1000)
 [condition type: SYNCHRONOUS-OPERATING-SYSTEM-SIGNAL]

 Restart actions (select using :continue):
 0: continue computation
 1: Return to Top Level (an "abort" restart)
[1c] USER(3): (sort pippo #'<)
Segmentation fault (core dumped)
%
    
```

The stack overflow occurs because a large array is being stack-allocated
to perform the sort. The size of the array is architecture dependent;
Windows platforms only allocate up to 4 Kbyte arrays on the stack, and
normally heap allocate any larger arrays needed, while Unix platforms
attempt to allocate 4 Mbyte arrays on the stack. On any architecture,
the strategy is programmable; as described below.

When the above error occurs, there are several things that can be done.

1.  Instead of popping out of the break loop as in the example above,
    just continue. The stack overflow automatically reduces the stack
    cushion (see documentation for sys:stack-cushion and
    sys:set-stack-cushion), so continuing should allow further
    execution.

2.  On Unix platforms only, a csh can be run and the limit command used
    to set the stack limit to something larger than it currently is. We
    recommend at least 8192 Kbytes (8 megabytes), but if that is not
    enough, more can be allocated.

3.  Change the sort strategy (documented below). The Allegro CL
    implementation of the sort function tries to allocate a temporary
    array on the stack if possible, so that it does not need to do so on
    the heap. If this strategy is not acceptable or convenient, change
    the strategy to either allocate from the heap or to use a
    pre-existing user supplied array.

Just continuing usually works as does, usually, clearing stack with a
:reset and retrying. Note, as the second example above shows, trying to
redo the sort command in the error prompt (that is, without clearing the
error) can result in an abnormal exit from the lisp (Segmentation fault
(core dumped) ).

This is an unfortunate hole in our stack-overflow detection strategy;
Stack overflow is normally detected for every function call, and enough
"slop" is allowed for so that functions that allocate an average amount
of stack will not cause a hard stack overflow. But if the function
allocates large stack objects (such as large temporary vectors) then the
jump in stack usage is too much to detect by either the stack cushion or
the hardware overflow detection, and stack-overflow death occurs. We
hope to guard against such overflow death in some future version of
Allegro CL.

Sort Strategy:

You can tell the system whether to try to stack-allocate things to be
sorted. From the documentation in the source code:

``` 

;; excl::*simple-vector-sort-strategy*:
;;
;; The sort strategy can be one of three types:
;; :stack - try to allocate stack space for the temp sort; this
;; works easily for 1k elements (4 kbytes), and (on
;; Unix platforms only) for up to 1m elements (4 mbytes)
;; if there is enough stack allocated by the os; more
;; than 1 m elements cause a new svector to be allocated.
;; :alloc - Allocate an svector of size equal to the vector to sort.
;; a new one is allocated each time.
;; <vector> - must be a simple-vector of type t of at least as many
;; elements as are being sorted. During the sort, the global
;; is reset to :alloc so that sort is re-entrant.

(defvar excl::*simple-vector-sort-strategy* :stack)
    
```

<span id="s5q5"></span>

### Q. I have set the stack cushion (see sys:set-stack-cushion and sys:stack-cushion) to a reasonable value, but the soft stack limit is not being detected, and I get a lisp death instead. Why is that?

The stack-cushion (see
[sys:set-stack-cushion](https://franz.com/support/documentation/current/doc/operators/system/set-stack-cushion.htm)
and
[sys:stack-cushion](https://franz.com/support/documentation/current/doc/operators/system/stack-cushion.htm))
is detected in "symbol trampoline", a short piece of code that is used
when one Lisp function calls another. It is meant to flag normal
situations where stack is growing too quickly, and to signal a condition
before a hard stack-size limit is reached.

There are several possible situations where the stack-overflow is not
detected by this mechanism, and careful thought must be given as to how
to handle it:

1.  A lisp function may allocate a very large stack size, due to either
    a large number of variables or due to large stack-allocated arrays
    or lists. If the amount that the function allocates is larger than
    the difference between the hard stack limit and the soft stack limit
    set up by the stack cushion, then there will be no chance for the
    Lisp to signal the condition before the hard limit is reached. The
    only way to work around this problem is to be sure that there is
    sufficient stack-cushion for the worst-case function to allocate its
    needed stack.

2.  A Lisp function might call itself recursively, which on some
    architectures generates a fast call to location 0 of the same
    function. The fast call causes the symbol trampoline to be bypassed,
    thus causing the stack overflow detection to also be bypassed. The
    workaround is to declare the function calling itself as notinline
    within its own body. This will result in slightly slower code
    generation, but overflows would then be detected. Example:

<!-- end list -->

``` 

    (defun call-me ( ... )
      (declare (notinline call-me))
      ...
      (call-me ...) ... )
    
```

3.  A non-lisp thread may be called, at which time there is no way to
    limit the stack on some machines. There is no workaround for this
    problem, other than to reduce one's dependence on non-lisp code.

<span id="s5q6"></span>

### Q. Why does it take so long to load a file that interns several thousand symbols in a package?

A package has an associated hashtable for the names of symbols in the
package. When the size of a package is not specified at creation time, a
default hashtable is used. Its initial size is small, allowing for 10
entries, and it tends to grow slowly, growing about 20% each time growth
is necessary. Those values are reasonable for most uses, but if you know
that a package will have many more symbols, particularly if they will be
all created at roughly the same time (as when reading a file that
interns thousands of symbols), you should specify the :size keyword
argument to defpackage appropriately when creating the package. Thus, if
you know the package will eventually have about 4000 symbols, define it
with a form like this:

``` 
(defpackage :foo (:size 4000) (:use :cl :excl))
    
```

<span id="s5q7"></span>

### <span id="structureht">Q. Why is equal hash table access slow when the keys are structure objects?</span>

The function cl:sxhash always returns the same value for structure
objects. The reason for this is because it has no extra space to store a
unique hash code within it. As a result, using structures as keys is
very inefficient. The (unexported) excl::hash-table-stats function
demonstrates this when given a hash-table with structs used as keys; the
histogram becomes the worst case, because every key wants the same
index.

The decision was made to keep the same behavior for structure objects,
because the automatic inclusion of a hashing slot in all structure
objects would have made all structs an average of one word longer. For
small structs this is unacceptable for many of our users.

Instead, a user may define a struct with an extra slot, and the
constructor for that struct type could store a unique value into that
slot (either a random value or a value gotten by incrementing a counter
each time the constructor is run). Also, create a hash generating
function which accesses this hash-slot to generate its value. If the
structs to be hashed are buried inside a list, then this hash function
would need to know how to traverse these keys to obtain a unique value.
Finally, then, build your hash-table using the documented :hash-function
argument to
[make-hash-table](https://franz.com/support/documentation/current/doc/implementation.htm#cl-make-hash-table-2)
(still using the equal test argument), to create a hash-table which will
be well-distributed.

Alternatively, and if you can guarantee that none of the slots in your
structures will be changed after they are used as keys in the
hash-table, you can use the equalp test function in your make-hash-table
call, rather than equal. If you do, however, make sure that these struct
objects don't change, because then they may not be found in the
hash-table.

### <span id="tracerecurse">Q. Why doesn't tracing a self-calling function trace the inner calls?</span>

This [trace
example](https://franz.com/support/documentation/current/doc/debugging.htm#trace-example-2)
provides the following code:

```
(defun fact (n)
  (cond ((= n 1) 1)
  (t (* n (fact (1- n))))))

```

which works interpreted, but on some architectures produces a
truncated result when the function is compiled, e.g.:

```
cl-user(4): (fact 5)
 0[2]: (fact 5)
 0[2]: returned 120
120
cl-user(5): 

```

Different architectures produce different output, depending on details
of their instruction set, number or registers, and so on. 32-bit x86
architectures, for example, tend to produce the full trace output,
while 64-bit Lisps on 64-bit x36 architectures tend to produce the
above truncated output, bypassing the trace output.

The issue is that a self-call can be made very efficient in
architectures that take on the x86-64 style compilation, and as such
they bypass the central call site which performs the Lisp function
call. This call site is very efficient for calls to other functions,
but is normally bypassed for an extra bit of efficiency when calling
the same function (since the function register doesn't need to be
loaded, because it is already in the right place, and the correct
instruction is trivial to locate - it is the pc-relative 0 location in
the current code vector). This bypassing of the call site is performed
regardless of any tail-call merge settings, but can be thwarted by
declaring the function notinline:

```
(defun fact (n)
  (declare (notinline fact))
  (cond ((= n 1) 1)
  (t (* n (fact (1- n))))))

```

This declaration removes the special handling of the self-call, and
thus self-recursive calls are made through the central call site,
where the trace mechanism will see the call.

## <span id="s-heap">Heap placement issues</span>

<span id="s6q1"></span>

### <span id="largeheaps">Q. How can I specify very large heap sizes for 64-bit versions of Lisp?</span>

Something like this will not work of some platforms (64-bit Windows, for
example):

``` 

(build-lisp-image "new.dxl" :lisp-heap-size (* 1024 1024 1025 15))
    
```

Instead of allocating a 15 GB heap, it will allocate something
significantly smaller. This is caused because the integer resulting from
the multiplication (16,121,856,000) requires more than 32-bits to
represent and the *ascii to integer* conversions on some operating
systems do not handle more than 32-bits.

Instead, do this:

``` 

(build-lisp-image "new.dxl" :lisp-heap-size "15375m")
    
```

<span id="s6q2"></span>

### Q. Sometimes Allegro CL, particularly with large images, fail totally with a bus error or a segv. Why might this be happening?

In large images, this is occasionally a sign that your system has run
out of virtual memory. This can occur on platforms that perform lazy
swap allocation, which makes possible the overcommitting of virtual
memory. Heap relocation or resizing will not help resolve this issue.
Instead, you should:

  - Have your system administrator increase the available system
    resources.
  - Use the Runtime Analyzer to determine what is causing the large
    allocations and resultant heap growth.
  - Tune the Garbage Collector to better meet the needs of your
    application.

<span id="s6q3"></span>

### Q. Sometimes Allegro CL, particularly with large images, run out of memory with a storage-condition. Why might this be happening?

The most common cause of this problem is that you've run out of address
space for the lisp heap. The first question to ask yourself, as a
developer, is: Do I expect my application to consume as much memory at
is it?

If the question is no, you should determine the cause of the unexpected
allocations and resultant heap growth. The [Space
Analyzer](https://franz.com/support/documentation/current/doc/runtime-analyzer.htm#spaceprofiler-2)
can help you do so.

If the answer is yes, then it may be that you need to adjust the
locations of the heaps used by Allegro CL. Choosing an adequate location
in which to map the Lisp and foreign (Aclmalloc) heaps in a running Lisp image
is complex. We refer to these problems collectively as the heap
placement problem. While these problems are not in fact new, they are
only triggered when the Lisp image is large (typically greater than 500
Mbytes).

Continue reading the questions below for advice on how to proceed.

<span id="s6q4"></span>

### Q. How is heap placement determined and what can go wrong?

When Allegro CL starts up, space must be found for the following:

  - The Lisp heap. This is where Lisp data is stored. This heap may be
    moved or shrunk in order to fit into available memory at startup.
  - The `Aclmalloc` heap. This is where space allocated by aclmalloc is located,
    along with the value of certain C variables. Note that `Aclmalloc` heap is an
    unfortunate name because it is not directly related to C and is, in
    fact, directly managed by lisp. The `Aclmalloc` heap must always be allocated
    at an address higher than the Lisp heap. This heap is static and
    will not be relocated if necessary at startup. This is due to a
    requirement to maintain the accuracy of pointers into the `Aclmalloc` heap
    across calls to
    [dumplisp](https://franz.com/support/documentation/current/doc/operators/excl/dumplisp.htm).
  - Shared libraries. These are the .so (on most UNIX machines),
    .dylib (on Mac OS X), and .dll (on Windows) files
    built with the system.
  - pll file: the \`pure lisp library' file contains constant data (such
    as strings and code vectors) to be used by Allegro CL when running.
    The name refers to the file type. Images can be built to use a pll
    file or not. See [Creating and using pll
    files](https://franz.com/support/documentation/current/doc/miscellaneous.htm#pll-file-1)
    in
    [miscellaneous.htm.](https://franz.com/support/documentation/current/doc/miscellaneous.htm)
  - The stack.

If you use 32 bit addressing (as Allegro CL does on most platforms),
there are potentially 4 GB of address space. However, most operating
systems only allow 31 bit addresses, so only 2 GB are really available.
Locations near address 0 (the bottom) are usually reserved by the
operating system. Therefore, Allegro CL usually tries to start at some
[OS-dependent
location](https://franz.com/support/documentation/current/doc/release-notes.htm#heap-start-2),
typically around 0x20000000, so there is potentially a 1.6 GB block
above that. This is plenty for an application that uses less than, say,
0.5 GB, but as the application grows to, say, 1.5 GB, finding enough
space becomes problematic. Assuming no intervening shared libraries or
other allocated regions in the process address space, you can determine
your maximum lisp heap in an image by subtracting the lisp-heap-start
(lisp base) from the aclmalloc-heap-start (aclmalloc base).

Lisp is given an idea of how much heap space it will need to operate via
the lisp-heap-size argument to
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm).
This value does not describe the extent of the heap in use, rather it
indicates a guaranteed size to which the heap should be able to grow.
When building large images on 32-bit platforms, process address space is
at a premium and will typically be exhausted long before physical RAM or
Virtual Memory is consumed. It is important, therefore, to find and
claim a suitable block of address space for application needs.

The claiming--via mmap(), specifically--of reserved growth space for the
heap has differing behavior under different operating systems. For
systems that support the MAP\_NORESERVE flag or perform lazy allocation,
a lisp-heap-size'd block of address space will be claimed without any
resultant mapping to virtual memory (until it is actually used). For
other platforms a request for address space will also claim an
equivalent amount of virtual memory.

So, what might go wrong when Allegro CL starts up? The following might
be problems:

  - On platforms that do not support a reserve/commit distinction 
    (this is rare), there may not be sufficient swap space
    to accommodate the requested Lisp heap size.}
  - Shared libraries may not be mapped at their desired locations. The
    worst offender in this regard are apps run under the Windows
    operating systems. In some cases when a .dll cannot be mapped where
    it wants to be it will not work properly.
  - Even if there is space to map everything, the first try at mapping
    may fail and everything may need to be remapped. If the relocation
    is not done properly, this can cause Lisp to fail.

Even though this problem may affect any user of Allegro CL or an Allegro
CL application, it is mostly a problem with developers of programs which
will be distributed to a user base. Users who have an Allegro CL
distribution and use a particular machine can, perhaps with trial and
error (and perhaps with assistance from Franz Inc.), figure out how to
build an image that will work on that machine. But VAR's, say, who are
preparing a distribution requiring large images which will be sent to
many customers, each of whom may have a different machine configuration
and different programs running, may find it difficult to produce a
single image suitable for all potential users on a particular platform.

Programmers can affect heap placements using these arguments to
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm):

  - :lisp-heap-start
  - :lisp-heap-size
  - :aclmalloc-heap-start
  - :aclmalloc-heap-size

Improvements in heap location management made available starting in
release 5.0.1 make the successful mapping of large images more likely,
and make the providing of one image for all users on a particular
platform easier to solve. But, any application that uses most of the
available address space is in danger of running into machine constraints
which make the application fail.

<span id="s6q5"></span>

### Q. How does Lisp start up, in terms of shared-library linking and loading?

This is a complicated answer. We start with some terminology:

  - **Shared-library**: A program unit that can be linked or loaded
    into a program, which usually has a .dll extension for Windows,
    a .dylib extension for macOS,
    and an .so extension for all other UNIX systems. Shared libraries
    come in three flavors:
    
    1.  The ACL shared library: This shared-library holds the base ACL
        system, and is sometimes known by the term "acldll". On Windows
        it is known as aclxxx.dll, and on UNIX it is called
        libaclxxx.ext where xxx is a version number and .ext is either
        .dylib or .so.
    
    2.  System libraries: shared-libraries that are pre-linked into
        either the ACL shared-library or the executable that loads the
        ACL library, or any shared-library on which a system library is
        dependent. This is a broad definition of system library, and can
        include any user-supplied library that has been linked into the
        executable.
    
    3.  User loaded libraries: These are libraries that are loaded with
        the Common Lisp LOAD function, but not pre-linked as are system
        libraries.

  - **Executable**: a program that either links or loads and invokes the
    ACL shared library. We supply several executables in the
    distribution, one called mlisp.exe on Windows and mlisp on unix.
    However, any program can be built that does the equivalent (see on
    Windows, for example, dll.htm). The executable loads the ACL shared
    library, and invokes it by getting and executing the lisp\_init()
    function. (You can provide your own main() that calls lisp\_init(),
    see [main.htm](https://franz.com/support/documentation/current/doc/main.htm)).
  - **Heap file**: a file with a .dxl extension (also called an image
    file) that holds the two Lisps heaps. One is the `Aclmalloc` heap, which 
    holds non-Lisp data including C
    variable values and data allocated by aclmalloc. The other heap is
    the Lisp heap, which holds all mutable Lisp data.
  - **Pure Lisp library**: A file with a .pll extension, which may be
    optionally loaded into a Lisp process and which contains read-only
    Lisp data.
  - **Link**: A process of attaching shared-libraries by name to an
    executable, usually by a linker program or by a compiler that
    automatically invokes a linker. Shared libraries and their symbols
    are not usually actually included into a program when linked, but
    references by name are made and the linked library is required to be
    available before the executable can start.
  - **Load**: A process by which a shared-library is dynamically
    mapped into the memory space of an already-running executable. The
    functions to call to load a shared-library are LoadLibrary() on
    Windows and dlopen() on Unix systems including macOS. The **load**
    Common Lisp function of Allegro CL calls one of these functions
    when it sees that the file being loaded is a shared-library.
  - **Bind**: Attaching functions within a shared-library to allow those
    functions to be called. The ff:def-foreign-call function in Allegro
    CL creates a binding location that is automatically updated when
    shared-libraries are loaded that supply the functions. The
    executable must bind the symbol lisp\_init in the ACL shared library
    in order to call it. Binding is done by getting the address of the
    function's code, by GetProcAddress() in Windows and dlsym() on 
    Unix systems including macOS.
  - **Invoke**: The process of calling a function which has been bound.
    C invokes a function that has been bound by using a
    "pointer-to-function" construct. Lisp uses ff:def-foreign-call to
    bind a C function in such a way that it looks like a Lisp function.
  - **Committed area**: An area of memory that is mapped in and which
    consumes virtual memory, one page of virtual memory for each page of
    address space. The memory might be physical memory (RAM), or it can
    be swap memory on disk, or it might even be a specific file, also on
    disk. The Committed area of the Lisp heap is usually the area
    bounded by the lisp-heap-start and the "Top" address in the room
    display.
  - **Reserved area**: An address range of memory is reserved when no
    other program unit has the right to map anything into that range,
    but the address range is not committed by actual swap space. This is
    the area requested by the :lisp-heap-size argument to
    [build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm)
    (see
    [building-images.htm](https://franz.com/support/documentation/current/doc/building-images.htm)).
    It is carried through all
    [dumplisp](https://franz.com/support/documentation/current/doc/operators/excl/dumplisp.htm)s.
    Although the committed area may eventually grown beyond this value,
    the space for the reserved area is only allocated if there is enough
    space for it. The reason for having a reserved area, instead of
    simply allocating memory that the operating system will give, is
    because as the Lisp heap grows, its addresses must grow
    monotonically increasing; new spaces must be always at higher
    addresses. 

**The Startup Process:**

1.  The operating system starts up the executable. Before the executable
    is able to start running, all system libraries must be loaded into
    memory and available. Various operating systems do this in various
    ways, using implementation dependent algorithms to place the
    libraries into memory. Also, whether all symbols are bound at the
    time of the library placement or whether the symbols are bound
    lazily (i.e., when needed only) is OS dependent; some systems may
    provide both.

2.  The executable begins to run. It may perform any operations it wants
    to do, including loading shared-libraries.

3.  The ACL shared-library is loaded if necessary and lisp\_init is
    invoked. The operating system ensures that all shared-libraries that
    were linked into the ACL shared-library are loaded before lisp\_init
    is allowed to start. If the ACL shared-library was linked in,
    lisp\_init can be called immediately. Step 1 above assured that all
    proper links are done. See
    [main.htm](https://franz.com/support/documentation/current/doc/main.htm) for further
    details.

4.  lisp-init determines a heap (image) file, with extension typically
    .dxl. The heap file contains state information about the image,
    including whether a Pure Lisp Library will be used. The .dxl and
    .pll are loaded into memory in the following manner:

5.  The `Aclmalloc` heap is mapped in, and C variables are set. If a .pll file is
    to be used this fact becomes known at this time. The `Aclmalloc` heap can not
    be relocated from where it was first built.

6.  The .pll file, if present, is mapped in read-only. If it can't be
    mapped into the location it had been in a previous incarnation of
    Lisp, it is moved to another location. (Except when an image is
    built with
    [build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm),
    there is always a previous incarnation of Lisp, perhaps the one that
    ran when the image was built).

7.  The Lisp heap is mapped in. The best case is if the heap can be
    placed at the address and size that were specified by the build
    parameters. If those can't be satisfied, decreasing sizes are tried
    until either one is successful or the current commit level is passed
    (at the same address), followed by an operating-system-selected
    space of the built size, followed by decreasing sizes tried at OS
    selected locations until one is successful or the current commit
    level is passed (at which time Lisp startup fails). If the
    lisp-heap-size happens to be larger than the available swap, then
    only as much as can be actually allocated is used, as long as it is
    at least as large as the commit requirement.

8.  Pointers are adjusted if the Lisp heap or the .pll file had to be
    moved. (The Lisp heap file might have to be moved because the Lisp
    heap start address is not available, e.g. The .pll file might have
    to be moved if the address in the previous Lisp invocation is
    unavailable.) All pointers to the expected locations of the Lisp
    heap file and the pll file are moved to the new locations. This step
    is performed all at once, to ensure proper pointer movement.

9.  The Lisp starts. The process by which the Lisp starts is documented
    by the source file, \<allegro directory\>/src/aclstart.cl, which is
    provided in your distribution, and described in [Section 12.0 of
    startup.htm](https://franz.com/support/documentation/current/doc/startup.htm#start-up-description-1).
    As one of the items in aclstart.cl, excl::reload-fix-entry-points
    (this function is not further documented) is called, which ensures
    that all system and user libraries are loaded if they are not
    already. This may involve performing a load on any libraries that
    were not loaded.

Now, there is a potential problem with the last step. If

  - there are user libraries that are to be loaded, and
  - the lisp-heap-size is specified as larger than the available swap
    space, and
  - a contiguous address space is found for the Lisp heap that is also
    larger than the available swap,

then it is conceivable that there will be no swap left for the loading
of the user libraries.

In this situation, it would be best for the executable to be programmed
to pre-load the user librar(y/ies) so that the space is pre-allocated.
(You do this by writing a customized main() that loads the needed
libraries, see [main.htm](https://franz.com/support/documentation/current/doc/main.htm)) But
this presents the possibility that the user library might break up the
contiguous address space for the Lisp heap, especially on Windows. The
problem in intractable in general, but solvable in individual cases.

<span id="s6q6"></span>

### <span id="heaplocations">Q. How can I tell where my image's heaps are located, and what size they are?</span>

The ansi standard function
[room](https://franz.com/support/documentation/current/ansicl/dictentr/room.htm) can be
used for this. A description of the output generated by this function is
described in [section 2.4 Getting information on memory management using
cl:room](https://franz.com/support/documentation/current/doc/gc.htm#getting-gc-info-2) of
[gc.htm](https://franz.com/support/documentation/current/doc/gc.htm).

Knowledge of your heap locations is necessary to make use of the below
suggestions for finding room for larger heaps or for relocating DLLs so
they don't interfere with your heap growth. Likewise, if you are
interested in increasing your heap size, you should have an idea of how
much space you want based on your application requirements.

<span id="s6q7"></span>

### <span id="addressspace">Q. How can I tell what addresses are being used in my process space?</span>

There is a C function in the Lisp called **memory\_status\_dump**, with
this prototype:

``` 

void memory_status_dump(char *file);
    
```

You can bind a Lisp function to this by evaluating this

``` 

(ff:def-foreign-call memory_status_dump () :strings-convert t)
    
```

and you can execute it like this:

``` 

(memory_status_dump "mem.out")
    
```

It will give you a dump of every address in the process, and its status.
A string argument will dump the input to the given file. An argument of
0 will send the output to the console on Windows or the tty in which you
are running Lisp on UNIX.

For example, on Solaris the output would look something like this:

``` 

Mappings: 52, from struct prmap_t in sys/procfs.h:
0x00000000 - 0x0000ffff      65536  free
0x00010000 - 0x00017fff      32768  ---r-x offset = 0
0x00018000 - 0x00025fff      57344  free
0x00026000 - 0x00029fff      16384  ---rwx offset = 24576
0x0002a000 - 0x00033fff      40960  -b-rwx offset = 0
0x00034000 - 0x03ffffff   66895872  free
0x04000000 - 0x04705fff    7364608  ---rwx offset = 24576
0x04706000 - 0x04771fff     442368  ---rwx offset = 0
0x04772000 - 0x04899fff    1212416  ---rwx offset = 7389184
0x0489a000 - 0x04a49fff    1769472  ---rwx offset = 0
0x04a4a000 - 0x53ffffff 1331388416  free
0x54000000 - 0x54005fff      24576  ---rwx offset = 9093120
0x54006000 - 0xfe6fffff 2859442176  free
0xfe700000 - 0xfe7a7fff     688128  ---r-x offset = 0
0xfe7a8000 - 0xfe7b5fff      57344  free
0xfe7b6000 - 0xfe7bffff      40960  ---rwx offset = 679936
0xfe7c0000 - 0xfe7d7fff      98304  ---rwx offset = 0
0xfe7d8000 - 0xfe801fff     172032  free
0xfe802000 - 0xfe803fff       8192  ---rwx offset = 0
0xfe804000 - 0xfe903fff    1048576  free
0xfe904000 - 0xfe905fff       8192  ---rwx offset = 0
0xfe906000 - 0xfea05fff    1048576  free
0xfea06000 - 0xfea07fff       8192  ---rwx offset = 0
0xfea08000 - 0xfeb07fff    1048576  free
0xfeb08000 - 0xfeb09fff       8192  ---rwx offset = 0
0xfeb0a000 - 0xfec09fff    1048576  free
0xfec0a000 - 0xfec0bfff       8192  ---rwx offset = 0
0xfec0c000 - 0xfed0bfff    1048576  free
0xfed0c000 - 0xfed0dfff       8192  ---rwx offset = 0
0xfed0e000 - 0xfee0dfff    1048576  free
0xfee0e000 - 0xfee0ffff       8192  ---rwx offset = 0
0xfee10000 - 0xfef0bfff    1032192  free
0xfef0c000 - 0xfef0dfff       8192  ---rwx offset = 0
0xfef0e000 - 0xfef0ffff       8192  free
0xfef10000 - 0xfef11fff       8192  ---rwx offset = 0
0xfef12000 - 0xff00dfff    1032192  free
0xff00e000 - 0xff00ffff       8192  ---rwx offset = 0
0xff010000 - 0xff0bffff     720896  free
0xff0c0000 - 0xff0ddfff     122880  ---r-x offset = 0
0xff0de000 - 0xff0ebfff      57344  free
0xff0ec000 - 0xff0effff      16384  ---rwx offset = 114688
0xff0f0000 - 0xff0f9fff      40960  ---rwx offset = 0
0xff0fa000 - 0xff0fffff      24576  free
0xff100000 - 0xff1a3fff     671744  ---r-x offset = 0
0xff1a4000 - 0xff1b1fff      57344  free
0xff1b2000 - 0xff1b9fff      32768  ---rwx offset = 663552
0xff1ba000 - 0xff1bbfff       8192  ---rwx offset = 0
0xff1bc000 - 0xff1e3fff     163840  free
0xff1e4000 - 0xff1e5fff       8192  ---rwx offset = 0
0xff1e6000 - 0xff1effff      40960  free
0xff1f0000 - 0xff1f3fff      16384  ---r-x offset = 0
0xff1f4000 - 0xff1fffff      49152  free
0xff200000 - 0xff27ffff     524288  ---r-x offset = 0
0xff280000 - 0xff28dfff      57344  free
0xff28e000 - 0xff297fff      40960  ---rwx offset = 516096
0xff298000 - 0xff29ffff      32768  ---rwx offset = 0
0xff2a0000 - 0xff2affff      65536  free
0xff2b0000 - 0xff2b1fff       8192  ---rwx offset = 0
0xff2b2000 - 0xff2bffff      57344  free
0xff2c0000 - 0xff2c3fff      16384  ---r-x offset = 0
0xff2c4000 - 0xff2d1fff      57344  free
0xff2d2000 - 0xff2d3fff       8192  ---rwx offset = 8192
0xff2d4000 - 0xff2dffff      49152  free
0xff2e0000 - 0xff2e7fff      32768  ---r-x offset = 0
0xff2e8000 - 0xff2f5fff      57344  free
0xff2f6000 - 0xff2f7fff       8192  ---rwx offset = 24576
0xff2f8000 - 0xff2fffff      32768  free
0xff300000 - 0xff307fff      32768  ---r-x offset = 0
0xff308000 - 0xff315fff      57344  free
0xff316000 - 0xff319fff      16384  ---rwx offset = 24576
0xff31a000 - 0xff31ffff      24576  free
0xff320000 - 0xff321fff       8192  --srwx offset = 0
0xff322000 - 0xff32ffff      57344  free
0xff330000 - 0xff345fff      90112  ---r-x offset = 0
0xff346000 - 0xff353fff      57344  free
0xff354000 - 0xff355fff       8192  ---rwx offset = 81920
0xff356000 - 0xff35ffff      40960  free
0xff360000 - 0xff365fff      24576  ---r-x offset = 0
0xff366000 - 0xff373fff      57344  free
0xff374000 - 0xff375fff       8192  ---rwx offset = 16384
0xff376000 - 0xff37ffff      40960  free
0xff380000 - 0xff387fff      32768  ---r-x offset = 0
0xff388000 - 0xff395fff      57344  free
0xff396000 - 0xff397fff       8192  ---rwx offset = 24576
0xff398000 - 0xff39ffff      32768  free
0xff3a0000 - 0xff3a1fff       8192  ---r-x offset = 0
0xff3a2000 - 0xff3affff      57344  free
0xff3b0000 - 0xff3cdfff     122880  ---r-x offset = 0
0xff3ce000 - 0xff3dbfff      57344  free
0xff3dc000 - 0xff3ddfff       8192  ---rwx offset = 114688
0xff3de000 - 0xff3dffff       8192  ---rwx offset = 0
0xff3e0000 - 0xff443fff     409600  free
0xff444000 - 0xff445fff       8192  ---rwx offset = 0
0xff446000 - 0xffbe5fff    7995392  free
0xffbe6000 - 0xffbeffff      40960  s--rwx offset = 4294942720
    
```

Note that each section of memory is grouped by how it is currently
mapped; the four characters at the end are flags, with a dash
representing not available, and one of r, w, x, and c for read, write,
execute and copy-on-write (shared until written, when it will get a
private copy).

The problem with memory\_status\_dump is that it doesn't always identify
what object is being mapped into any particular address area (such
information depends on what's available on a per platform basis). It
seems reasonably intuitive what an "object" is by all of the maps on all
architectures; each address range constitutes one mapping. However, it
is impossible to tell what the objects actually are, and sometimes when
two address ranges are exactly adjacent to each other, the higher
address range is likely an extension of the lower address range. This is
important in deciding what objects to try to identify when deciding how
to move things around. For example, if the `Aclmalloc` heap starts at 0x54000000
and the map has two ranges next to each other, one from 0x54000000 to
0x54007fff and one from 0x54008000 (i.e 0x54007fff + 1) to 0x5401dfff,
then it is likely that the `Aclmalloc` heap was extended once, and thus that if
the `Aclmalloc` heap is moved it will take care of both address ranges.

For x86 windows, we recommend the use of Process Explorer (previously
hosted by www.sysinternals.com, but now distributed by Microsoft) and a
VMMap tool. These utilities provide a lot of information and have good
user interfaces.

The Process Explorer is available for download
[here](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer).
and the VMMap tool
[here](https://docs.microsoft.com/en-us/sysinternals/downloads/vmmap).

Here are some more notes on the Process Explorer: you first download and
install this program. Then, start Allegro CL and run Process Explorer.
This will bring up a dual-paned window, the top half of which will show
a list of running processes. Click on \`allegro.exe' (or \`mlisp.exe' or
\`alisp.exe'), and in the lower pane you will be shown what objects have
been allocated in the processes address space.

Some Process Explorer configuration tips:

  - make sure that there is a lower pane showing (menu: View -\> Show
    Lower Pane has check mark)
  - make sure that the lower pane shows DLL info (menu: View -\> Lower
    Pane View -\> DLL has check mark)
  - in the lower pane, right click on the column headers and pick
    SelectColumns. Check at least Name, Path, Base address, Mapped size,
    Mapping type
  - make sure that mlisp.exe is selected in the upper pane
  - make sure that the lower pane is sorted by ascending Base address
  - then, finally, save to a file.

For other platforms, the situation is more complicated, but there are
usually operating system tools for interpreting the data.

<span id="s6q8"></span>

### <span id="rebasedll">Q. \[Windows only\] How do I move DLL in memory so that it doesn't conflict with the Lisp heap?</span>

The preferred Lisp heap starting address is 0x20000000 on x86 Windows
(the heap grows to higher memory addresses). If, using the Process
Explorer program (discussed above, an x86 Windows application), you find
that the Lisp heap cannot grow to the size that you desire because of a
DLL that is in the way, you can use the \`editbin' program from
Microsoft Visual C++ to move the default base address of the DLL. For
example, if foo.dll is in a bad location, according to Process Explorer,
and you found foo.dll to live in the c:\\winnt\\system32 directory, then
at a DOS prompt type (assuming 0x65000000 is the beginning of a free
address range large enough to accomodate the DLL):

``` 

cd c:\winnt\system32
editbin foo.dll /rebase:base=0x65000000
    
```

and the next time Lisp starts up, Windows will try to locate foo.dll at
0x65000000 instead of the previous inconvenient address that interfered
with the Lisp heap. Note that you may need to disable related programs
or boot into safe mode in order to perform this operation. It is
generally not possible to modify such files when they are active and
loaded into a process address space.

Note that the base address for a DLL is only advisory; if the space is
already used, Windows will locate it to some other location. By
right-clicking on a DLL and selecting "Quick View" (if Quick View
support is installed), you can see (among other things) the base address
currently assigned to the DLL.

<span id="s6q9"></span>

### Q. What does the "Temporarily scaling back lisp reserved region from XXX to YYY bytes." mean?

It means that some other program has grabbed part of the address space
that Lisp intended to use. This message is much more common on Windows,
where various programs can grab predefined address ranges in all running
programs. The Iomega Zip/Jaz tools and PGP are two programs known to do
this. There are four things that you can do to handle this situation:

1.  Ignore the warning. This means that your lisp heap might be
    significantly smaller than intended. You can tell just how big by
    dividing YYY above by 1048576, which will give you the size of the
    heap in MB.
2.  Uninstall the application. Sometimes the application isn't really
    needed. On Windows, the Iomega tools on a SCSI system, for example,
    are not really needed--Windows has native support for these SCSI
    devices.
3.  \[Windows only\] "Rebase" the DLL to use another address. See [How
    do I move DLL in memory so that it doesn't conflict with the Lisp
    heap?](#rebasedll) for more information. Look around address
    0x65000000 for a free slot to which you can rebase the DLL. If
    addresses in that range are taken, find the Windows DLLs (e.g.,
    COMCTL32.dll) and pick a location around them for the DLL to live.
4.  Rebuild your ACL images using a different range of addresses for the
    Lisp heap. On UNIX, see [How can I tell what addresses are being
    used in my process space?](#addressspace) for more information.

The arguments to
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm)
that you will need to specify are :lisp-heap-start, :lisp-heap-size,
:aclmalloc-heap-size and :aclmalloc-heap-start.

<span id="s6q10"></span>

### Q. What should I know when choosing non-default heap locations?

Both the Lisp and `Aclmalloc` heap must remain in one individual contiguous piece.
(i.e a single contiguous lisp heap, and a separate single, contiguous C
heap). You need to find a large enough gap in the address space to cover
all growth expectations of your application. Most 'large' apps need lots
of room for the lisp heap to grow and very little for the `Aclmalloc` heap. Your
mileage may vary.

On Unix platforms, the OS allocates memory in the sbrk region, which
typically resides directly after the mapped location of the lisp
executable. If you restrict this region too much, you run the risk of
causing your application to fail with an "unable to allocate memory"
error that will usually crash the lisp. This malloc region is used by
low level OS system calls and typically by any foreign libraries
included in your application.

Combined with the knowledge of your current heap locations and sizes,
you can use memory-status-dump (see [earlier question](#addressspace))
to find free regions in the process address space.

<span id="s6q11"></span>

### Q. How do I build an image with non-default heap sizes and/or locations?

The typical way to build new images is via the function
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm).
It accepts the following four keyword arguments that are used to
relocate the lisp and `Aclmalloc` heaps from their default locations and sizes:

  - :lisp-heap-start
  - :lisp-heap-size
  - :aclmalloc-heap-start
  - :aclmalloc-heap-size
  - :initial-oldspace
  - :initial-newspace

The following two keyword arguments let you further shape the lisp heap
once it has been allocated.

  - :oldspace
  - :newspace

Once you have chosen values for these parameters (see previous questions
in this section for help doing so), simply include them in your call to
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm).
When starting the new image, a call to
[room](https://franz.com/support/documentation/current/doc/gc.htm#getting-gc-info-2) should
show that the lisp heaps have been relocated.

<span id="s6q12"></span>

### Q. How do I build default images provided by Franz with non-default heap sizes and/or locations?

A common problem with developers of 'large' applications is that default
development images such as alisp.dxl and allegro.dxl are built with
default heap locations. Further, even if developers customize the heap
locations and sizes of these apps, their changes are undone when they
update patches and run update.sh or update.exe.

To this end, we have added the following environment variables that
[build-lisp-image](https://franz.com/support/documentation/current/doc/operators/excl/build-lisp-image.htm)
will check for when creating a new image.

  - ACL\_BUILD\_LISP\_HEAP\_START: :lisp-heap-start argument
  - ACL\_BUILD\_LISP\_HEAP\_SIZE: :lisp-heap-size argument
  - ACL\_BUILD\_ACLMALLOC\_HEAP\_START: :c-heap-start argument
  - ACL\_BUILD\_ACLMALLOC\_HEAP\_SIZE: :c-heap-size argument
  - ACL\_BUILD\_NEWSPACE: :newspace argument
  - ACL\_BUILD\_OLDSPACE: :oldspace argument

Arguments values should use lisp hex notation (\#x).

It is recommended that users not modify their general development
environment when making use of these environment variables as that can
result in undue confusion and unexpected results. Instead, it is
recommended that a new script (or batch) file be created with a name not
used by Allegro CL, such as 'my-update.sh' or 'my-update.bat', which
invokes update.sh or update.exe depending on the platform. This script
file can then set these environment variables as desired before invoking
the Franz provided update script.

The user then need only remember to run their personalized update script
and their heap settings should persist even when patches are updated.

<span id="s6q13"></span>

### Q. Can I specify heap locations and/or sizes when starting lisp?

No. The `Aclmalloc` heap in particular is not relocatable, so this approach is not
feasible. The Lisp heap is relocatable--and occasionally will shrink if
the reserve space is not available--but due to the `Aclmalloc` heap restriction,
the only option would be to lower it in memory. This being only half a
possible solution, we have not opened up this limited functionality.

## <span id="s-gc">Garbage Collection</span>

<span id="s7q1"></span>

### <span id="memgobble">Q. My memory gobbling loop causes the gc to perform badly. Why?</span>

The loop you are running is likely not releasing any bytes of heap for
the amount it is allocating. A loop similar to

``` 

(compile
 (defun gobble ()
   (loop for x from 1 to 1000000000000000000000000
       with k = 0
       do
     (incf k)
     (when (= k 10000000)
           (print ".")
           (setq k 0))
       collect x)))
(gobble)
    
```

is likely generating almost no garbage. Allegro CL's garbage collector
makes decisions about how much space to allocate based on the
gsgc-parameters that are currently set, and the effect of this loop is
to throw the calculations into a non-linear area where the only thing it
can do is to cause the heap to grow at a huge rate of increase.

Most real programs never run this way; either they don't cons at all, or
at least some of the consing done is ephemeral, even if only a few
percent of the total consing. And, of course, any program which
continues to cons permanent space should be considered leaky, unless it
is explicitly a test to gobble up all of memory, and to see how such
gobbling progresses.

To get better gobbling behavior, allocate at least some of the space in
such a way that it becomes garbage. This allows the gc to operate in a
more natural manner, and will cause a smoother transition toward the
inevitable heap-exhaustion:

``` 

(compile
 (defun gobble2 ()
   (loop for x from 1 to 1000000000000000000000000
       with k = 0
       do
     (incf k)
     (when (= k 10000000)
           (print ".")
           (setq k 0))
         (when (zerop (mod k 10))
           (cons x nil)) ; waste a cons
       collect x)))
(gobble2)
    
```

Finally: the reason why heap grows so quickly is because newspace must
hold all of the objects that have been allocated until they are to be
tenured, even though it is known that none of them will die, and so the
newspace must continually grow to hold the new allocations as well as
the objects waiting to be tenured. An explicit gc with tenuring
periodically will serve to flush the newspace out, and will also keep it
to a reasonable size, thus making the march toward heap-exhaustion even
more smooth:

``` 

(compile
 (defun gobble3 ()
   (loop for x from 1 to 1000000000000000000000000
       with k = 0
       do
     (incf k)
     (when (= k 10000000)
           (print ".")
           (setq k 0)
           (gc :tenure)) ; clear newspace
         (when (zerop (mod k 10))
           (cons x nil)) ; waste a cons
       collect x)))
(gobble3)
    
```

## <span id="s-ffi">Foreign Functions Interface</span>

<span id="s8q1"></span>

### Q. How do I pass and return 64-bit integers through the FFI?

Allegro CL does not support 64-bit integers in 32-bit lisps, since we
try to be compatible on all architectures on which we run, and since
there are so many different extensions to C to allow for 64-bit
integers, which are of course longer than a "long" type.

You can work around this by defining a struct containing two 32-bit
values

``` 

(def-foreign-type unsignedlonglong
     (:struct (high :unsigned-int) (low :unsigned-int)))

(defun unsignedlonglong-value (x)
  (+ (ash (fslot-value-typed 'unsignedlonglong nil x 'high) 32)
     (fslot-value-typed 'unsignedlonglong nil x 'low)))
    
```

When you define your foreign function, have it return the struct, rather
than the integer, and have the lisp reconstruct the number using the
function above. You can then have the lisp reconstruct the number using
the function above.

For passing 64-bit values, you can write a routine to pack 64-bit values
into the struct. The struct returned should be passed to the foreign
function call.

``` 

(defun value-unsignedlonglong (x)
  (let ((inst (ff:allocate-fobject 'unsignedlonglong)))
    (setf (ff:fslot-value-typed 'unsignedlonglong nil inst 'high)
      (ash x -32)
      (ff:fslot-value-typed 'unsignedlonglong nil inst 'low)
         
      (logand x #xffffffff))
    inst))
    
```

The above code could be further generalized to allow for multiple
allocation types. Users are cautioned to be careful not to introduce
memory leaks into their application.

## <span id="s-clim">CLIM</span>

<span id="s9q1"></span>

### Q. How can I replace the lesstif installed with RedHat Linux 7.2 with openmotif (required for CLIM)?

This question is answered [here](#clim-lesstif-linux86), in the **Linux
(architecture specific)** section.

## <span id="s-composer">Composer</span>

<span id="s10q1"></span>

### Q. When starting Composer I get the error `'Error: "Connection     refused" (errno 111) occurred while creating a local socket and     connecting to a remote host ... on port 6000.'`

Recent Linux distributions deliver X servers that no longer listen for
tcp/ip connections, even on the local host. Composer accesses X displays
via the CLX (Common Lisp X) module, which until recently only supported
X communication via tcp/ip.

A patch is now available for Allegro CL 8.0 that adds support for unix
domain socket connections to the XCW and CLX modules. The LOG entries
for these patches can be read at:

  - [code/clx.001](https://franz.com/support/patches/log/8.0/index.lhtml#base_clx_001)
  - [update/pdh001.001](https://franz.com/support/patches/log/8.0/index.lhtml#xcw_pdh001_001)

These patches will be automatically downloaded if you run
[sys:update-allegro](https://franz.com/support/documentation/current/doc/operators/system/update-allegro.htm)

An alternative fix is to re-enable tcp/ip connections in your X server.
In SuSE Linux 9.2, for example, set the environment variable
`DISPLAYMANAGER_XSERVER_TCP_PORT_6000_OPEN` in
`/etc/sysconfig/displaymanager` to "yes" to turn tcp/ip connections back
on the next time X is started.

This fix will propagate to future releases of Allegro CL, where a patch
will no longer be needed.

## <span id="32-64-compat">Compatibility between 32 and 64-bit versions of Allegro CL</span>

<span id="s11q1"></span>

### Q. What changes are needed to move from a 32-bit to 64-bit Allegro CL?

[Very
little (click to see the documentation)](https://franz.com/support/documentation/current/doc/implementation.htm#app-64bit-2).

<span id="s11q2"></span>

### Q. Why does my 64-bit foreign call cause a SIGSEGV?

If your code works fine on 32-bit versions of Allegro CL, then it is
most likely because of the difference in size between :int and :long.

The [:returning keyword
argument](https://franz.com/support/documentation/current/doc/foreign-functions.htm#def-foreign-call-returning-3)
to
[def-foreign-call](https://franz.com/support/documentation/current/doc/operators/ff/def-foreign-call.htm)
is a key piece of the solution, where the return value has been declared
as an :int rather than a :long or an :unsigned-long. Passing an :int
into a foreign call is also dangerous, where the expected types might
mismatch.

The real problem is that C defines the default declaration to be *int*
(i.e. if a variable or function return is not declared, it is assumed to
be *int*). But in a 64-bit application, the equivalent integer (an
integer whose size matches that of a pointer) is *long* not an *int*,
and so there is a tendency to underdeclare C functions.

And because our def-foreign-call interface tries to match the interface
for C, the same issue occurs - but because in our def-foreign-call,
where there is no way to check against the C code like a C compiler can
(and can thus issue warnings about possible data loss when assigning a
pointer to an int variable) the defaults become a disadvantage.

## <span id="s-misc">Misc</span>

<span id="s12q1"></span>

### <span id="fork">Q. What issues must I be aware of when using excl.osi:fork</span>

Aside from the items documented in the fork(2) Man page, there are a few
other issues that Allegro CL application writers must be aware of when
using
[excl.osi:fork](https://franz.com/support/documentation/current/doc/os-interface.htm#fork-op-bookmarkxx)

##### Q. All Lisp processes survive in the child process.

The first pitfall is that in a typical C application, only the thread
calling fork() will survive in the child. In a non-os-thread lisp,
however, lisp processes are not tied to os level threads. They will
continue to exist, and possibly share resources, in the child process.
Further, in future, when os-threaded lisps become available, while the
underlying threads will not exist in the child, the process objects in
lisp will, creating an invalid state where lisp continues to believe
these threads are valid. We will update this faq with more information
on how to resolve this issue when \*nix os-thread lisps become
available.

##### Q. Inadvertent shared resources between parent and child. Sockets and Streams.

The second pitfall is that the child process inherits all file
descriptors from the parent. In lisp, it is not common to deal with fd's
directly, but rather the socket and/or file stream objects which overlay
these fds. Any attempts to read or write on sockets or streams, that are
not properly synchronized between parent and child, may result in race
conditions that cause a forked application to unexpectedly hang, or
crash.

Further, there are many add-on modules that start lisp processes that
make use of streams, further obfuscating the existence of potentially
shared resources. An example is the acldns module, which communicates
with local nameservers in order to provide hostname lookup capabilities.

##### Recommendations

  - **Fork sooner rather than later**. The sooner one forks after
    application startup, the less likelihood there will be of
    inadvertent resource sharing. Barring this, be aware of what
    resources you wish to use in the child process that should not be
    shared with the parent, and fork prior to this. It is much easier to
    design your application with this in mind, than try to clean up
    unnecessary processes and objects in the child after the fact.
  - **Know what resources are being used in your application**. This is
    not always easy to know. There are many add-on modules that start
    lisp processes or open sockets without the application developer
    necessarily being aware. Examples of this are AllegroServe, which
    spawns many processes, one of which opens a passive socket, for
    serving HTTP requests; and another is the ACLDNS module, which
    starts a process that opens a socket(s) to your local nameservers
    for performing lookups. If you need to use fork() and are not sure
    if an add-on module spawns any open sockets or streams, please
    contact us at <support@franz.com> to ask.

<span id="s12q2"></span>

### <span id="python">Q. Do you have an interface to Python?</span>

There are two resources which might be helpful to Python users:

  - <http://common-lisp.net/project/clpython/>
  - <http://common-lisp.net/project/python-on-lisp/>

<span id="s12q3"></span>

### Q. Sometimes TIME results produce negative values. Why?

As an example, see the below output

``` 

CL-USER(12): (time (fib 30))
; cpu time (non-gc) 36,784 msec user, 140 msec system
; cpu time (gc)     3,994 msec user, 10 msec system
; cpu time (total)  40,778 msec user, 150 msec system
; real time  51,274 msec
; space allocation:
;  60,582,248 cons cells, -934,589,280 other bytes, 0 static bytes
1346269
CL-USER(13):
    
```

The problem is with the overflow of machine integers. On 32-bit
platforms, the allocator, which resides in low level C code, keeps track
of counts using 32-bit variables. As these allocations occur over time,
these variables can in fact overflow resulting in the negative output
seen above. It would be a simple matter to adjust such values in the
case where an overflow occurs only once (the typical case), by adding
\#x100000000 (4 GB) to the negative value. But because we cannot
determine how many overflows actually occured, we choose not to adjust
in all cases where negative space is reported as that would give wholly
false (but apparently valid) results in some cases. We recommend trying
the adjustment (adding \#x100000000) and seeing if the result looks
reasonable.

## <span id="smpversions">Multiprocessing</span>

<span id="s13q1"></span>

### Q. Which versions and platforms have symmetric multiprocessing (SMP) extensions?

Symmetric multiprocessing is available as part of Allegro Common
Lisp 10.1 on [these platforms](https://franz.com/products/allegro-common-lisp/#osinfo). (SMP may not be available on some platforms in earlier releases.)

For more information see our [SMP
documentation](https://franz.com/support/documentation/current/doc/smp.htm).

## <span id="s-windows">Windows (architecture specific)</span>

<span id="s14q1"></span>

### <span id="vista">Q. Should Allegro CL on Windows be installed in the Program Files directory?</span>

We do not recommend that because the security model on some versions
of Windows requires having Administrator priviledges to modify files
in subdirectories of Program Files. Files are modified when patches
are installed but also many users use subdirectories of the Allegro CL
directories for their own source files, and writing or modifying them
will thus also require Administrator priviledges. The default Allegro
CL installation procedure installs in the C: drive directly. That is
what we recommend.

<span id="s14q2"></span>

### <span id="dep">Q. My lisp immediately crashes a few seconds after startup. What's causing this?</span>

Current versions of Microsoft operating systems come with a security
*feature* enabled called **Data Execution Prevention**. While it helps
protect against a common class of malicious attacks, it also prevents
our lisp from running\! To correct this, firat verify that DEP is
enabled and is what is causing the problem.

  - Right-click on '**My Computer**' and choose **Properties**.
  - In the dialog that appears, select the '**Advanced**' tab, and then
    in the *Performance* section of the dialog, press the '**Settings**
    button.
  - Another dialog will appear. Choose the '**Data Execution
    Prevention**' tab.

There are a couple of options here.

  - Turn on DEP for essential Windows programs and services only.
  - Turn on DEP for all programs and services except those I select.

If DEP is only enabled for essential Windows programs, then DEP is not
causing the problem. Please see the FAQ entry on [How to report
Bugs](#howtoreportbugs) and submit a report to <support@franz.com>. If
DEP is enabled for all programs and there are no lisp exceptions, it is
likely the cause.

Choosing the first option is the simplest, since Allegro CL provides a
number of different executables from which Lisp can be used. Also, the
update process creates a temporary executable called update.exe when
updating images to contain new patches. If you decide to add DEP
exceptions for Allegro CL, you will need to create a temporary file
named update.exe in the Allegro directory and add it using the DEP
dialog.

<span id="s14q3"></span>

### Q. Why can't I use \`dir' with run-shell-command?

On Windows,
[excl:run-shell-command](https://franz.com/support/documentation/current/doc/operators/excl/run-shell-command.htm)
executes programs but does not invoke shell commands. The function is
therefore misnamed for Windows. It is called run-shell-command to
provide cross-platform compatibility between Windows and Unix and back
compatibility for ACL4.3.x users. It does behave differently on Windows
and Unix. The difference is related to differences between UNIX and
Windows. See the documentation page for excl:run-shell-command for
details on this point.

<span id="s14q4"></span>

### Q. How do I control the stack size on Windows?

The default stack reserve size for the lisp process is 16MB.

The stack-size process attribute was supposed to control the stack
allocation for the process. What the Windows documentation did not make
clear, unfortunately, was that the running process can control the
amount of swap space initially committed to the stack, but cannot select
the amount of address space reserved for the stack.

The address space to be reserved for each thread's stack is a property
of the executable image being used. The property is specified at link
time, but it can be altered without relinking, through the EDITBIN
program that is part of the VC+ development package.

To make each thread allocate a 4Meg stack, the command would be (for the
executable allergo.exe, repeat the command for other executables):

``` 
editbin /stack:4000000 allegro.exe
    
```

Unfortunately, MS Windows offers no way to have different reserve sizes
for different threads in the same process, so all the threads have to be
big enough to support the deepest computation on any thread.

<span id="s14q5"></span>

### Q. How do I get ANSI ACL (rather than Modern ACL) to start when I double-click on an lpr file?

The Windows registry associates file types with programs, so that double
clicking on a file of a particular type initiates a program in a clearly
defined way. (Thus, typically double clicking on a file with type txt
typically initiates the Notepad utility in Windows, opening the file
clicked on.) As defined by the installation procedure, lpr files (the
files defining projects) are associated with allegro.exe/allegro.dxl,
the Modern version of Allegro CL with the IDE. Double-clicking on an lpr
file thus starts the Modern image with the IDE, and opens the project
associated with the lpr file.

If you want the ANSI Allegro CL with the IDE
(allegro-ansi.exe/allegro-ansi.dxl) to start instead, you must modify
the registry.

The simplest way to do this is with a Windows tool. While Windows menu
choices move about, try opening the View menu on the Windows Explorer
and click on the Options... item or try the Tools menu and the Folder
Options choice. This will display an Options dialog. Click on the File
Types tab, and find Lisp project file in the displayed list of types.
Select it and click on the Edit... button. Select open in the Actions
pane and click on the Edit... button. Modify the text in the Application
used to perform action field, changing allegro.exe to allegro-ansi.exe
and allegro.dxl to allegro-ansi.dxl. Click on the OK buttons on the open
dialogs to complete the change. On Windows 2000, open the Tools menu and
click on the Folder Options item, and choose the LPR extension, click on
the Advanced button, click on the open action, click on the Edit...
button, find the associated command line, and modify it.

<span id="s14q6"></span>

### Q. Why is the compiler complaining about a missing in-package form when I am certain that my **offline file** starts with one?

When working with Windows offline files, the following situation has
been observed. As a result, we recommend that in general, one not
develop using offline files.

1.  A file, `foo.cl`, is compiled.

2.  The compiler signals an error that goes to a break loop.

3.  Go to an Emacs buffer where the file `foo.cl` is showing.

4.  Make some correction to the file and save it.

5.  :continue from the break.

6.  The compiler claims that there is no in-package.

7.  The file `foo.cl` on disk appears to be all hex zero bytes.

If the file `foo.cl` is still in the Emacs buffer, it can be saved again
to recover the content on disk; but if the Emacs buffer was killed, the
content of the file is lost.

There seems to be no way for ACL to detect this situation and thus avoid
it or warn the user about the possible danger. The only solution is to
use caution when working with offline files.

We have found that using an alternate tool such as WinSCP can be one way
to avoid this problem while retaining the ability to synchronize remote
files conveniently.

<span id="s14q7"></span>

### <span id="rightAlt">Q. Why does the right Alt key not work the same as the left Alt key?</span>

Common Graphics does not handle the righthand alt key on the Windows
platform because that overrides its functionality on some keyboards
(especially European keyboards) for entering characters that don't have
dedicated keys. You can revert to the old functionality by setting the
CG configuration option reserve-righthand-alt-key to nil, as in:

``` 
(setf (cg:reserve-righthand-alt-key (cg:configuration cg:*system*)) nil)
    
```

That option doesn't appear on the IDE's Options dialog, but if you
modify it once in the IDE then your options file will remember the value
for subsequent IDE sessions. In a standalone CG application you would
need to set the value in application code.

## <span id="s-linux86">Linux (architecture specific)</span>

<span id="s15q1"></span>

### <span id="selinux">Q. Why on Linux does Allegro CL die on startup?</span>

There are various errors which can occur:

  - `cannot restore segment prot after reloc: Permission denied`
  - Segmentation fault

This problem occurs when SELinux (Security-Enhanced Linux) is enabled.
This is a security extension originally developed by the NSA that comes
enabled by default in some newer linux distributions. One of the
security features changes the way shared libraries are loaded by
default, and this is preventing Allegro CL from properly starting.

The best solution is to run the following command to enable Allegro CL
to load its shared library:

``` 

# chcon -t textrel_shlib_t /usr/local/acl81_express/libacli817t.so
    
```

You need to substitute */usr/local/acl81\_express* with the actual path
to your Allegro CL installation directory. Also, *libacli817t.so* is the
name of the Allegro CL Express Edition shared library, and for other
versions of Allegro CL the name might be different. Run the above
command on any file named *.so* in the Allegro CL directory.

Another solution is to disable SELinux entirely. This is done by either
of these methods:

  - As root, run system-config-securitylevel, go to the SELinux tab, and
    change the SELinux setting to Disabled.
  - Set the line **SELINUX=disabled** in /etc/sysconfig/selinux.

<span id="s15q2"></span>

### Q. On which x86 (i.e., Intel Pentium and friends) Linux versions do the currently supported versions of Allegro CL run?

Allegro CL runs on a large number of kernels, for which we do not
provide a comprehensive listing. See our [Platform
Listing](https://franz.com/products/allegrocl/#osinfo) for current information about
kernel or glibc restrictions.

<span id="s15q3"></span>

### <span id="clim-lesstif-linux86">Q. How can I replace the lesstif installed with RedHat Linux 7.2 with openmotif (required for CLIM)?</span>

Allegro CL CLIM requires Motif 2.1, a free version of which is
available from www.openmotif.org.

Although the default installation of RedHat Linux 7.2 includes
installation of lesstif (a variant of Motif that does not work with
CLIM), there is an installation mode where you can alter the default
package installation list and therefore prevent the installation of
lesstif. If you do this, you can simply install openmotif Motif 2.1
after obtaining it from www.openmotif.org.

However, once lesstif is installed, you should remove it before
installing openmotif Motif 2.1. To uninstall lesstif, enter

``` 
% rpm --erase lesstif
    
```

The rpm program will notify you if removing the lesstif package would
break anything (and it will not continue with removing lesstif). rpm
will indicate which packages depend on lesstif. Please contact Franz
Inc. (sending mail to <support@franz.com>) for assistance if there are
problems removing lesstif.

Once lesstif is removed, openmotif Motif 2.1 can be installed following
instructions received with the software.

## <span id="s-macosx">Mac OS X (architecture specific)</span>

<span id="s16q1"></span>


<span id="s16q2"></span>


<span id="s16q3"></span>

### Q. Why do I get crash reports when running 32-bit PPC Allegro CL?

This is a known bug in Mac OS X. Programs which catch Unix-style signals
and handle them will still result in "crash" reports being generated
erroneously by the CrashReporter.

See
<http://developer.apple.com/technotes/tn2004/tn2123.html#SECLIMITATIONS>
and note close to the end of the page under the heading "CrashReporter
Limitations", specifically the bug labelled 2941263.

It looks from the page as though this CrashReporter has only started in
macOS 10.4, but we've seen the crash logs occur before that; perhaps it
is just the newer facilities that are more verbose.

For all other and future Mac OS X ports (including the 64-bit PPC port
and Intel Mac OS X) we have moved our exception handling style away from
Unix-style signals, and instead use the Mach exception style that Mac OS
X is used to seeing. We currently have no plans to back-port this new
style to the 32-bit PPC Mac.

You may be able to control the logging of these crash reports, depending
on what the current state of the tools are that are described on the
referenced page.

## <span id="s-using-cl">Using Common Lisp (non-Allegro specific)</span>

<span id="s17q1"></span>

### Q. Why does read-from-string ignore my first keyword argument (unless I also specify both optional arguments)?

If a function accepts both optional and keyword arguments, and you need
to pass any keyword arguments, then you must first pass all optional
arguments before any keyword arguments. Because the value of an optional
argument could be a keyword symbol, it would otherwise be ambiguous
whether a keyword that's passed just after all required arguments is an
optional or keyword argument. If you don't want to specify particular
values for the optional arguments, then you generally should pass the
default values for them, which typically are nil but which may be any
value -- and that requires learning the default values of the optional
arguments even though you don't care about them.

For these reasons, it's considered poor style to specify both optional
and keyword parameters when defining a function, and converting any
optionals to keywords in that case is preferred (especially when there
are more than a few, or there is a likelihood of adding additional
parameters in the future). Nevertheless, the Common Lisp spec does
include a few functions such as read-from-string that have both
optionals and keywords.

<span id="s17q2"></span>

### Q. Why does read-from-string signal an end-of-file error even when I pass the eof-error-p argument as nil?

According to the ANSI spec, a null eof-error-p argument suppresses an
end-of-file condition that occurs just before reading a new object, but
NOT one that occurs while in the middle of reading an object. Reading
from the string "(foo", for example, will still signal an error at end
of file, because it is in the middle of reading a list object at the
time.

Here's a rule of thumb to follow: If you know that a string is "well
formed", such that a sequence of valid objects can be read from it in
the usual iterative way with an end of file immediately afterward, then
you can rely on a null eof-error-p argument to avoid signaling an
end-of-file error. But in the general case where a string has unknown
contents, an end-of-file error (or some other read error such as "too
many colons") may still be signaled. Generally when reading from unknown
contents, it's a good idea to wrap a handler-case form around the read
to trap errors.

Here is the relevant text from the ANSI page for read-from-string,
describing the two distinct cases:

> If the end of the supplied substring occurs before an object can be
> read, an error is signaled if eof-error-p is true. An error is
> signaled if the end of the substring occurs in the middle of an
> incomplete object.

The documentation for READ goes into more detail:

> Description: ... If a file ends in a symbol or a number immediately
> followed by an end of file, read reads the symbol or number
> successfully; when called again, it sees the end of file and only then
> acts according to eof-error-p. If a file contains ignorable text at
> the end, such as blank lines and comments, read does not consider it
> to end in the middle of an object. ...

> Exceptional Situations:

> read signals an error of type end-of-file, regardless of eof-error-p,
> if the file ends in the middle of an object representation. For
> example, if a file does not contain enough right parentheses to
> balance the left parentheses in it, read signals an error. This is
> detected when read or read-preserving-whitespace is called with
> recursive-p and eof-error-p non-nil, and end-of-file is reached before
> the beginning of an object.
