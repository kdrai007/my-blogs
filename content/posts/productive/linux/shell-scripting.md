---
title: "shell-scripting"
id: shell-scripting
aliases: []
tags: []
---

# Linux shell cookbook

Currently I'am trying to master linux cli so i'am reading linux cookbook where
i'll learn about bash scripting,cli cool tricks and tips etc

### Debugging bash scripts

bash -x *.sh

- Running the bash script using -x flag with print each source line with the current status.

We can use debugging technique in bash scripts itslef for ex:

`#!/bin/sh
for i in {1..6};
do
    set -x
    echo i
    set +x
done
`

using -x will start the debugging process and +x will end it,debugging is restricted uisng -x and +x flags.

' #!/bin/sh -xv '
using this shabang we can debug scripts without any extra hassle.


## Links

[[]]


