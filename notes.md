Notes from getting together to chat about this stuff: 

https://github.com/bbatsov/ruby-style-guide

https://www.pivotaltracker.com/help/api?version=v3#github_hooks
https://www.pivotaltracker.com/help/api?version=v3#scm_post_commit_message_syntax
SCM Post-Commit Message Syntax
To associate an SCM commit with a specific Tracker story, you must include a special syntax in the commit message to indicate one or more story IDs and (optionally) a state change for the story. Your commit message should have square brackets containing a hash mark followed by the story ID. If a story was not already started (it was in the "not started" state), a commit message will automatically start it. For example, if Scotty uses the following message when committing SCM revision 54321:
  [#12345677 #12345678] Diverting power from warp drive to torpedoes.
  
...it will result in the following comment being added to Tracker stories 12345677 and 12345678, and the stories will be started if they were not yet started:
  Commit: Scotty
  54321
  [#12345677 #12345678] Diverting power from warp drive to torpedoes.
  
To automatically finish a story by using a commit message, include "fixed", "completed" or "finished" in the square brackets in addition to the story ID. You may also use different cases or forms of these verbs, such as "Fix" or "FIXES", and they may appear before or after the story ID. Note: For features, this will put the story in the 'finished' state. For chores, it will put the story in the 'accepted' state. For example:
  [Fixes #12345678] Torpedoes now sufficiently powered.
  
In some environments, code that is committed is automatically deployed. For this situation, include "delivers" and the story will be put in the 'delivered' state:
  [Delivers #12345679] Scotty can beam up Captain Kirk.

Commit messages: 
[#124234] This commit fixes a thing
It’s really nice if we add something in the body
Simon has a template to make this the default


Branches
feature/making-a-nice-new-thing-1234563
chore/doing-some-work-for-success-6453456
bug/fixing-the-broken-thing-9384573
spike/trying-this-crazy-thing

Here's the message template: https://github.com/srt32/dotfiles/blob/master/.gitmessage

Try to avoid reverts - strive to always move forward. 

Solo requires a pr for code review. (exceptions made for emergency fixes)
Pairs can commit and/or merge to master

When and why do we branch? Always. For clarity and reviewability. 

We should be rebasing branches multiple times a day. 
When rebasing, nobody should be working on the branch you are. 
Also, instead of --force, use --force-with-lease

Never force push master

For now, let’s pr everything. 

The dev submitting PR owns merges. (and state of build).

In order to merge - rebase, then git merge --no-ff

Share git-config? 

Rule of thumb is to no-ff when there are a number of commits above 3(?)

Codeclimate

OVERCOMMIT_DISABLE=1 git commit -m "Blah blah WIP”
SKIP=RuboCop git commit -m ‘Blah Blah WIP’

Need to go all the way with rubocop
.
.
.
.
.
.
.
.
.
.
.
.
..
Notes from 3/14/17
Must do: 
[#3485457] This is a commit message

features/
chores/
spikes/
bugs/

“Nit: Blah” in comments on pull requests shows that we aren’t necessarily asking for a change
Spend some time on tuning rubocop
Specifically white space before blocks, auto-correcting these, and only touching the ones we change

Stories are a placeholder for conversations (until they’re moved to the backlog, then it should be summarized and the work to be done should should be clear) - citation needed

A-Z Blog Post: 
Jobs:
A-C: Thin jobs, starting with the work being done in the job and tested (probably via side effects of having been called)
D-G: When the code needs to be used elsewhere, create a class and use the job to call the class and write better unit tests. 

Controllers: 
A-G: Do all the things in the endpoint. Test everything in the controller specs. 
H-K: Create service objects and test independently. 

Models: 
A: Everything is in the models directory
B-E: Classes that are executing instructions and/or representing data go into models
Z: Models directory holds files that represent data. Services directory has services

To consider before next meeting: 
Log output from manually run rake tasks
Class for service objects are nominalized into a verb(end in -er)
Have a def call method that takes no args and the class gets initialized with args.
Live in app/services
Move Classes from Chores -> Utilities -> Services
Nuke chores that can be nuked


DO NOT UPDATE EXISTING SHIT

To consider for next meeting: 
[#no-story] This is intentionally not related to a story
Should we use a template for git commits?
1 more month of Codeclimate - is it worth it? 

Notes: 

We should talk about: Refactor on master, in a separate branch, in different commits? 


