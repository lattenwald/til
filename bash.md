# Shell stuff

## Get timestamp from datetime

    date --date='2017-06-07 18:00:00' +"%s"

## Get datetime from timestamp

    date -d @1267619929

# tmux

Go to command mode: hotkey, `:`. In my case hotkey is `^a` (`Ctrl+a`), by default it's `^b` (`Ctrl+b`).

<dl>
  <dt>Horizontal split to vertical and back</dt>
  <dd>`: next-layout`</dd>

  <dt>Swap window with another</dt>
  <dd>`: swap-window -t <int>`</dd>

  <dt>Break panes into windows</dt>
  <dd>`: break-pane` or `hotkey !`</dd>

  <dt>Join pane into another window</dt>
  <dd>`: join-pane -t <int>`, add `-h` or `-v` for explicit horizontal/vertical split</dd>
</dl>
