# Scriptable step remote execution

This repository provides a ready-to-import Airlock IAM Config Snippet.


## Requirements

- Airlock IAM 8.5 or later
- An Airlock IAM instance including a working configuration, according to your requirements
- Remote exec host, e.g. [scriptExec](https://github.com/airlock-presales/scriptExec) for Python
- Lua 5.4 and Luarocks installed (previous versions may work but have not been tested)


## Import snippet

Clone this Git repository:
```console
git clone https://github.com/airlock-presales/iam-snippets
```

Next, open the IAM Config Editor and drag-and-drop the snippet <code>iam-snippets/snippets/remoteScriptExec/remote-exec-step.yaml</code> to the left-hand plugin-tree.

You will have two new Airlock Flow steps available:

* Scriptable Step - RemoteExec helloworld user
* Acknowledge Message Step - Show remoteExec result

