Tmux refresher
=====================
2016-10-17


my tmux refresher notes.



Tmux allows you (amongst other things) to:

- organize your terminal into multiple windows
- each window is a screen that can be divided in multiple panes
- attach/detach sessions (see explanations below in the "Tmux concepts" section)



I'll be using tmux on ubuntu 14, via vagrant, and I'll be root all the time.



Tmux concepts
-------------------

### Session

tmux uses the concept of sessions.

You work in a session.

The session is attached to the machine, and you can attach/detach your terminal to/from a session.

This basically means that you can start a long running command in a session, then close your terminal and
the task will continue on the machine. 

Later, you can attach back to the session and see where your task is at.

This concept of session is one of the most powerful thing that tmux gives you out of the box.




### prefix

Ctrl+b is called the $prefix.







Install
-------------

```bash
apt-get install tmux
```



To start tmux server
---------------------

```bash
tmux
```



Basic workflow
--------------------
1. Create a session
```bash
tmux new -s mySession
```

2. Do your things inside the tmux session

3. When you are done, detach from the session (see tmux commands below)
```bash
$prefix d
```

4. Then, you can list the sessions, and attach back to a session
```bash
tmux list-sessions
tmux attach -t mySession
```





tmux commands
------------------

https://tmuxcheatsheet.com/



Once you have started the tmux server, you can use tmux commands.

The default commands are the following.


command 			|   	description
------------------- | --------------------------
$prefix ?			|	 list all key bindings
$prefix c         	|    create a new window (the tabs at the bottom of your tmux screen)
$prefix ,			|	 rename the current window (the one with the asterisk next to it)
$prefix p			|	 switch to previous window
$prefix n			|	 switch to next window
$prefix w			|	 list windows
$prefix %			|	 split window by drawing a vertical line
$prefix "			|	 split window by drawing an horizontal line
$prefix d			|	 detach from the session
$prefix o			|	 go to the next pane
$prefix z			|	 toggle focus to the current pane
$prefix arrow		|	 switch to the pane indicated by the arrow
$prefix :			|	 enter command mode, then type split-window to split the window vertically
$prefix :resize-pane -D | resize the current pane down
$prefix :resize-pane -U | resize the current pane upward
$prefix :resize-pane -L | resize the current pane left
$prefix :resize-pane -R | resize the current pane right
$prefix :resize-pane -D 10 | Resize the current pane down by 10 cells
$prefix :resize-pane -U 10 | Resize the current pane upward by 10 cells
$prefix :resize-pane -L 10 | Resize the current pane left by 10 cells
$prefix :resize-pane -R 10 | Resize the current pane right by 10 cells


Sessions
--------------

Create a new session called mySession

```bash
tmux new -s mySession
```

List current sessions

```bash
tmux list-sessions
```

Re-attach to a session

```bash
tmux attach -t mySession
```









All bind keys ($prefix ?)
------------------------------
```bash
bind-key        C-b send-prefix                                                                                                                  [0/0]
bind-key        C-o rotate-window
bind-key        C-z suspend-client
bind-key      Space next-layout
bind-key          ! break-pane
bind-key          " split-window
bind-key          # list-buffers
bind-key          $ command-prompt -I #S "rename-session '%%'"
bind-key          % split-window -h
bind-key          & confirm-before -p "kill-window #W? (y/n)" kill-window
bind-key          ' command-prompt -p index "select-window -t ':%%'"
bind-key          ( switch-client -p
bind-key          ) switch-client -n
bind-key          , command-prompt -I #W "rename-window '%%'"
bind-key          - delete-buffer
bind-key          . command-prompt "move-window -t '%%'"
bind-key          0 select-window -t :0
bind-key          1 select-window -t :1
bind-key          2 select-window -t :2
bind-key          3 select-window -t :3
bind-key          4 select-window -t :4
bind-key          5 select-window -t :5
bind-key          6 select-window -t :6
bind-key          7 select-window -t :7
bind-key          8 select-window -t :8
bind-key          9 select-window -t :9
bind-key          : command-prompt
bind-key          ; last-pane
bind-key          = choose-buffer
bind-key          ? list-keys
bind-key          D choose-client
bind-key          L switch-client -l
bind-key          [ copy-mode
bind-key          ] paste-buffer
bind-key          c new-window
bind-key          d detach-client
bind-key          f command-prompt "find-window '%%'"
bind-key          i display-message
bind-key          l last-window
bind-key          n next-window
bind-key          o select-pane -t :.+
bind-key          p previous-window
bind-key          q display-panes
bind-key          r refresh-client
bind-key          s choose-tree
bind-key          t clock-mode
bind-key          w choose-window
bind-key          x confirm-before -p "kill-pane #P? (y/n)" kill-pane
bind-key          z resize-pane -Z
bind-key          { swap-pane -U
bind-key          } swap-pane -D
bind-key          ~ show-messages
bind-key      PPage copy-mode -u
bind-key -r      Up select-pane -U
bind-key -r    Down select-pane -D
bind-key -r    Left select-pane -L
bind-key -r   Right select-pane -R
bind-key        M-1 select-layout even-horizontal
bind-key        M-2 select-layout even-vertical
bind-key        M-3 select-layout main-horizontal
bind-key        M-4 select-layout main-vertical
bind-key        M-5 select-layout tiled
bind-key        M-n next-window -a
bind-key        M-o rotate-window -D
bind-key        M-p previous-window -a
bind-key -r    M-Up resize-pane -U 5
bind-key -r  M-Down resize-pane -D 5
bind-key -r  M-Left resize-pane -L 5
bind-key -r M-Right resize-pane -R 5
bind-key -r    C-Up resize-pane -U
bind-key -r  C-Down resize-pane -D
bind-key -r  C-Left resize-pane -L
bind-key -r C-Right resize-pane -R
```



Sources
------------
https://www.youtube.com/watch?v=BHhA_ZKjyxo



