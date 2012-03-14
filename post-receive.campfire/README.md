Campfire notification post-receive hook for git
===============================================

A git hook for sending commit notifications to a Campfire room.

Based on `post-receive.irc` by Mikael Fridh <frimik@gmail.com>
https://gist.github.com/1821358

Install
--------

- copy `post-receive.campfire` to the repository's `hooks` directory,
  rename to `post-receive`.
- Make it is executable.

Configure
---------
Configure mandatory settings:

    cd repository
    git config hooks.campfire.api-key  "a23231..."
    git config hooks.campfire.org-name "mycompany"
    git config hooks.campfire.room-id  "12345"
    
The Campfire api-key can be retrieved from the web UI by clicking on 
'My Info'.

The Campfire room-id can be found in the web url of the room, eg:
`https://org_name.campfirenow/room/<ID>`

Notification Format
-------------------

The hook will send a message to the configured Campfire room similar to:

    [repo] joe miller pushed 2 new commits to 'environment/development'.
    - commit by joe miller (7 hours ago): Merge branch 'feature/git_hook_test' into environment/development
      Changeset: 073eefe4f39f9128a403f853d50e0bf0c87dd862
    - commit by joe miller (7 hours ago): adding a dummy test file for debugging git hooks
      Changeset: f2e0428cf1588ae5f630187cc55d04d609d15b6e</body>
      