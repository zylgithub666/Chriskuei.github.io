---
title: Elasticsearch
layout: post
description: Running as a daemon.
---

> Running as a daemon

To run Elasticsearch as a daemon, specify `-d` on the command line, and record the process ID in a file using the -p option

```bash
./bin/elasticsearch -d -p pid
```

Log messages can be found in the `$ES_HOME/logs/` directory.

To shut down Elasticsearch, kill the process ID recorded in the `pid` file:

```shell
kill `cat pid`
```

