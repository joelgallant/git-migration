# git migration
The document below outlines how and why software development should be migrated
from an subversion SCM system to git. Various notes are included to describe
how to deal with normal pitfalls of migration, like data storage and proper
project structure.

### FAQs
- [Why use version control?](http://mikemcquaid.com/2014/01/18/why-use-version-control/)
- [Mote on why to use version control](https://stackoverflow.com/questions/1408450/why-should-i-use-version-control)
- [Why git?](https://www.atlassian.com/git/tutorials/why-git/)

# Process
There are a number of ways a team can migrate. Some require lots of downtime and
a development freeze, some require no upstart time at all.

| Migration | Second Step | Pros | Cons |
| --------- | ----------- | ---- | ---- |
| svn to git | Split repositories | git has full history | Large repositories even for small projects |
| svn to git | Use branches for projects | git has full history, and doesn't clone data | Still a large repository when you only need a small project |
| svn to git | | git has full history | No natural separation, still a large repository |
| None | Split repositories | lightweight, proper structure | git does not have full history |

In terms of overall view for a multi-project svn server, there are options.
- Migrate some projects to git, and continue to use svn for others
- Migrate all projects to git
- Use svn and git simultaneously
- Migrate some projects to git, migrate some to datastorage (such as dropbox), and continue to use svn for others

### [Migrate to Git from SVN](https://www.atlassian.com/git/tutorials/migrating-overview/)
The above tutorial goes step by step on how to transition, and I will summarize.

There is a `git svn` command to migrate repositories, so the actual migration
step is actually quite straightforward, often happening in two or three commands
and a couple hours.

1. Synchronize history of git with svn (full or partial) (or skip this step)
2. Host git clone through bitbucket / github / gitlab, in **read only** mode
3. Prepare processes, scripts, etc. for using the git repository
4. Once tools & the team are comfortable with git, migrate and retire the svn 
   server

### Hosting
The main hosting providers are

| Host | Pricing |
| [Github](https://github.com/) | $25 / month (5 users) + $9 / user |
| [Bitbucket](https://bitbucket.org) | $10 / month (10 users) |
| [Gitlab](https://about.gitlab.com/) | $35 / month (30 users) |

# Learning git
1. "try git": https://try.github.io
2. "learn git branching": http://learngitbranching.js.org
3. "dig deeper": https://www.codecademy.com/learn/learn-git

# Structure
There are some things that should and should not be checked in to version
control. Version control is good for source code. It's designed for plaintext,
human readable code. It is not good for databases, builds, some images / assets,
large files, etc. There are better systems to host these files, meant for that
purpose. [gitignore](https://www.gitignore.io/) is a good resource to automate
the ignoring of such files.

Normal software projects follow a broadly agreed upon structure, with a README,
LICENSE, etc. It is a good idea to modularize projects into digestible pieces,
that are usable on their own. This enforces good practices, rather than relying
on specific system setups. See [project-desc](https://github.com/joelgallant/project-desc)
for a template.

# History
When migrating from scm to git, history can be kept in a few different ways.

1. Full migration of trunk -> master, tags -> branches, revisions -> commits,
   with user data migrated
2. Partial migration, without tags or only to a specified depth
3. "Lossy" migration, without any revisions, using svn as an archive for history
