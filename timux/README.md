# Timux

Tmux (short for "terminal multiplexer") is a powerful command-line tool that allows you to manage multiple terminal sessions within a single window. It's particularly handy for organizing and multitasking in the terminal. Here are some basic commands and functionalities of Tmux:

### Starting Tmux:
- To start Tmux, simply type `tmux` in your terminal and press Enter. This will create a new Tmux session.

### Key Bindings:
- **Key Combination**: Tmux commands are often invoked with a prefix key, which by default is `Ctrl + b`.
  - After pressing the prefix key, you can execute various Tmux commands.
  - For example, to split the window horizontally, you'd press `Ctrl + b` followed by `%`.

### Tmux Windows and Panes:
- **Windows**: In Tmux, you can have multiple windows within a session. Some commands related to windows:
  - `Ctrl + b, c`: Create a new window.
  - `Ctrl + b, n`: Move to the next window.
  - `Ctrl + b, p`: Move to the previous window.
  - `Ctrl + b, &`: Close the current window.

- **Panes**: Tmux allows splitting a window into multiple panes for multitasking:
  - `Ctrl + b, %`: Split the window vertically.
  - `Ctrl + b, "`: Split the window horizontally.
  - `Ctrl + b, arrow keys`: Navigate between panes.

### Tmux Sessions:
- **Sessions**: Tmux allows you to have multiple sessions, each containing multiple windows.
  - `tmux new -s <session_name>`: Create a new session.
  - `tmux ls`: List existing sessions.
  - `tmux attach -t <session_name>`: Attach to a specific session.

### Other Useful Commands:
- `Ctrl + b, d`: Detach from the current session.
- `tmux kill-session -t <session_name>`: Terminate a session.

Tmux provides a lot of flexibility in managing terminal sessions. Experimenting with these commands will help you get comfortable with its functionalities and enhance your productivity when working in the terminal.
