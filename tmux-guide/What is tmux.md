What is tmux?

tmux stands for Terminal Multiplexer.
It is a Linux/Unix tool that lets you run multiple terminal sessions inside a single window and keep them running even if you close your terminal or get disconnected.

Think of it like tabs and split screens for your terminal.

🔹 Why use tmux?

Run multiple sessions in one terminal.

Detach and reattach to sessions (your work keeps running in the background).

Split windows into panes (horizontal & vertical).

Useful for remote servers (via SSH) where you don’t want your processes to stop if your internet disconnects.

🔹 Common tmux Commands
Start a new session
tmux

Start a new session with a name
tmux new -s mysession

Detach from session (leave it running)

Press:

Ctrl + b  d

List all sessions
tmux ls

Reattach to a session
tmux attach -t mysession

Kill a session
tmux kill-session -t mysession

🔹 Splitting Windows into Panes

Split vertically:

Ctrl + b  %


Split horizontally:

Ctrl + b  "


Move between panes:

Ctrl + b  ArrowKey


Resize pane:

Ctrl + b  :resize-pane -D   # Down
Ctrl + b  :resize-pane -U   # Up
Ctrl + b  :resize-pane -L   # Left
Ctrl + b  :resize-pane -R   # Right

🔹 Cheatsheet
Action	Command
New session	tmux new -s name
Detach	Ctrl+b d
List sessions	tmux ls
Attach session	tmux attach -t name
Kill session	tmux kill-session -t name
Split vertically	Ctrl+b %
Split horizontally	Ctrl+b "
Switch panes	Ctrl+b ArrowKey

✅ In short:
tmux = multiple persistent terminals in one. Very useful for Linux admins, developers, and anyone working on remote servers.
