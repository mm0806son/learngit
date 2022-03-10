# Quick Start

## Git

Link a off-line folder with a online repo or clone from a online repo.

```shell
git remote add origin <your repository link>
git remote set-url origin https://<your token>@github.com/<your username>/<your repository name>/
```

Clone from a repo.

```shell
git clone <your repository link>
```

Always do `git pull` before start to work.

Use these codes to save.

```shell
git add yourfile.py
git commit -m "ASuperMessage"
git push
```

Check all changes.

```shell
git status
```

## SSH for IMT

Simply use this from a pc connected on Eduroam. If fail, try to add `.imt` at the end.

`ssh z20ning@pc-elec-387.priv.enst-bretagne.fr`

If you use VsCode, download the extention `remote-SSH` and add these lines in the config. As mentioned before, if fail, delete `.imt` to desactivate VPN and try again.

```shell
Host              pc-elec-387.priv.enst-bretagne.fr.imt
  User              z20ning
  ForwardX11       yes
  HostName          pc-elec-387.priv.enst-bretagne.fr

Host *.imt
  ProxyCommand C:\Windows\System32\OpenSSH\ssh.exe z20ning@ssh.telecom-bretagne.eu "/bin/nc `basename %h .imt` %p"
```

The `ForwardX11` line above is for seeing the figures genereted on remote.

## Run a program on remote

When runing a very long program such as traning a neuron network, we should use `krenew` to prevent the terminal from being shutted down.

```shell
kinit
krenew -K 60 python ...
```

We can use `tmux` to turn off the local computer safely without interrupting the remote.

```shell
krenew -K 60 tmux
# You will enter a virtual terminal and see a green line

RUN YOUR PROGRAM AS USUAL
BUT ADD & AT THE END

tmux detach
```

Now you can close your local terminal. Next time, use `tmux attach` to find back your remote terminal.

You can also try

```shell
tmux -s <A super name>
tmux attach -t <Same super name>
```
