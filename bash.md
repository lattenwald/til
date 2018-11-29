# Shell stuff

## Get timestamp from datetime

    date --date='2017-06-07 18:00:00' +"%s"

## Get datetime from timestamp

    date -d @1267619929

# tmux

Go to command mode: hotkey, `:`. In my case hotkey is `^a` (`Ctrl+a`), by default it's `^b` (`Ctrl+b`).

<dl>
  <dt>Horizontal split to vertical and back</dt>
  <dd><tt>: next-layout</tt></dd>

  <dt>Swap window with another</dt>
  <dd><tt>: swap-window -t &lt;int&gt;</tt></dd>

  <dt>Break panes into windows</dt>
  <dd><tt>: break-pane</tt> or <tt>hotkey !</tt></dd>

  <dt>Join pane into another window</dt>
  <dd><tt>: join-pane -t &lt;int&gt;</tt>, add <tt>-h</tt> or <tt>-v</tt> for explicit horizontal/vertical split</dd>
</dl>
