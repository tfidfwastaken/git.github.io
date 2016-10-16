---
layout: default
title: SoC 2017 Ideas
---

This is the idea page for Summer of Code 2017 for Git and libgit2.

## About applying for SoC with the Git project

*Please read this section completely before reading the idea list
 below.*

It is required that students who want to apply to the Git
project for the Summer of Code 2017 complete a tiny, code-related
"microproject" as part of their application.  Please refer to our
[guidelines and suggestions for microprojects](https://git.github.io/SoC-2017-Microprojects)
for more information. Completing a microproject is not only an important
way for us to get experience with applicants, but it will also help
applicants become familiar with Git's development and submission
process.

A complete GSoC application should include a presentation of yourself
(include any argument that may convince mentors that you are able to
complete the project) and detailed explanations about your project.
Ideas below are just ... ideas! The list is not exhaustive, and more
importantly each idea only includes a summary of what is to be done.
An application must include detailed plans on the design, timeline ...
A typical application takes several pages. You should already have read
[the GSoC Student Guide](http://write.flossmanuals.net/gsocstudentguide/writing-a-proposal/)
by now, but re-read it if needed.

Also, working in Git project is not only about writing your own
patches. Constructively critiquing design and implementation of
patches by other people is also an important skill you need to learn
in order to effectively collaborate with others. So, if you have time
and inclination, it would be beneficial to read and understand other
applicants' patches (or any other patch submitted to the mailing-list),
think if you agree that the problem they are trying to solve is worth
solving, the approach they are taking is the best way (or if you think
of a better way to solve it), etc., and respond to their patches with
the result of your thinking as a review.

Please, include link(s) to the mailing-list discussion(s) related to
your microproject in your application (e.g. linking to
[public-inbox](https://public-inbox.org/git/)). If you
participate in the review of other patches, then you may also include
links to discussions that would support your application.

Students must send drafts of their proposal on the mailing-list before
submitting it officially to GSoC to get feedback from the
community. They are strongly encourraged to publish a draft on the
official GSoC website *and* post it to the mailing list for
discussion.

Getting your proposal right can follow the same process as usual patch
submission for Git, as described in the
[microprojects](https://git.github.io/SoC-2017-Microprojects) page and
in `Documentation/SubmittingPatches` in Git's source code. It is also
expected that you will send several versions of your draft, responding
to comments on the list. If you are not sure about your proposal, you
can discuss that in the same email where you introduce yourself or in
separate emails. Please use "[GSoC]" at the beginning of such emails.

In summary, all applicants must (not necessarily in this order):

* Complete a [microproject](https://git.github.io/SoC-2017-Microprojects).

* Write a detailed application explaining their project.

* Discuss their project by posting drafts of their application on the
  mailing-list long before the deadline.

In your application, it is a good idea to:

* Include link(s) to the mailing-list discussion(s) related to the
  project you chose in your application, for example previous
  discussions or patch series about the topic. There might be
  interesting discussions about the topics that are several year old.
  It is also a good idea to summarize them.

* Include link(s) to the mailing-list discussion(s) related to the
  previous drafts of your application itself.

* Include link(s) to the mailing-list discussion(s) related to your
  microproject.

* Include what is suggested in
  [the GSoC Student Guide](http://write.flossmanuals.net/gsocstudentguide/writing-a-proposal/)

([public-inbox](https://public-inbox.org/git/) can be
used for searching the mailing list and linking to previous
discussions.)

## Note about the number of slots

In 2016, the Git organization has very limited mentoring capacity.
These days we usually accept between 0 and 2 students per year.

## Summer of code main project ideas

**Students**: Please consider these ideas as starting points for
generating proposals. We are also more than happy to receive proposals
for other ideas related to Git or libgit2. For libgit2, see the bottom
of the list and
[the libgit2 list of projects](https://github.com/libgit2/libgit2/blob/master/PROJECTS.md).


### git bisect improvements

 - Language: C, shell (bash)
 - Difficulty: medium
 - Possible mentors: Matthieu Moy, Christian Couder

#### Implement `git bisect --first-parent`.

When your project is strictly "new features are merged into trunk,
never the other way around", it is handy to be able to first find
a merge on the trunk that merged a topic to point fingers at when
a bug appears, instead of having to drill down to the individual
commit on the faulty side branch. Cf.  <http://thread.gmane.org/gmane.comp.version-control.git/264661/focus=264720>



### Convert scripts to builtins

Many components of Git are still in the form of shell and Perl scripts.
While this is an excellent choice as long as the functionality is
improved, it causes problems in production code – in particular on
multiple platforms, e.g. Windows (think: POSIX-to-Windows path
conversion issues).

The idea of this project is to dive into the Git source code and
convert a couple of shell and/or Perl scripts into portable and
performant C code, making it a so-called "built-in".

(Un)fortunately, the easy-to-port scripts like `git-pull.sh` are
already ported by now. It is still possible to start with something
small by porting portions of existing shell-scripts to C using a C
helper inside the existing shell-script.
