# git migration
The document below outlines how and why software development should be migrated
from an subversion SCM system to git. Various notes are included to describe
how to deal with normal pitfalls of migration, like data storage and proper
project structure.

### FAQs
- [Why git?](https://www.atlassian.com/git/tutorials/why-git/)

# Process
There are a number of ways a team can migrate. Some require lots of downtime and
a development freeze, some require no upstart time at all.

Some of the main methods are
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

# Learning git

# Structure

# History
