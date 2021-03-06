# pretty-printk

[Overview](#overview) / [Usage](#usage) / [Features](#features) / [License](#license) / [Links](#links)

## [Overview](#overview)

Debugging the Linux Kernel in a way most developers are familiar with is challenging. Setting breakpoints, stepping
through code and watching for the last important variable to change is hard. Sometimes just printing values to the
Kernel Ring Buffer can be a better and especially faster approach to debugging. After having print almost the
hundredths message with printk it started to feel dull and pointed me to tinker with its output.

When developing for the Web it is quite common to pretty such output and I was wondering why not to take my chances
and pretty the *printk-ing* inside the Kernel. The goal is to ease on the hand the process of printing and on the
other one it should increase readability when running dmesg.

## [Usage](#usage-testing-playing)

```c
#include "pretty_printk.h"

// [...]

pp_warn("Shortcut for severity level and flushing '\n' character");
pp_debug("Extended metadata while printk-ing with debug=1 or PP_DEBUG");
pp_walker();

// [...]
```

```sh
[ 12.300004] pretty_printk_demo: "Shortcut for severity level and flushing '\n' character"
[ 12.300006] pretty_printk_demo (pretty_printk_demo_init @ pretty_printk_demo.c, 62): "Extended metadata while printk-ing with debug=1 or PP_DEBUG"
[ 12.300008] pretty_printk_demo (pretty_printk_demo_init @ pretty_printk_demo.c, 63): "It worked up to this line"
```

For testing, debugging and looking at the features the repository provides a demo module **pretty_printk_demo** to
illustrate the different features. For building just call ```make``` and insert/remove the module in the common tools.
Inside the [init function](https://github.com/tpiekarski/pretty-printk/blob/master/pretty_printk_demo.c#L36) all features 
are demonstrated.

## [Features](#features)

Feature|Issue|PR|Status
---|---|---|---
Metadata when printk-ing| [#3](https://github.com/tpiekarski/pretty-printk/issues/3) | [7fcb473](https://github.com/tpiekarski/pretty-printk/commit/7fcb4734ef52453069d364074a28a5c6273242f6) | done
Severity shortcuts| [#4](https://github.com/tpiekarski/pretty-printk/issues/4) | [3dfc02d](https://github.com/tpiekarski/pretty-printk/commit/3dfc02d468fdc9c401f3b24c3c3b9a15b3043bce) | done
Switch for debugging| [#5](https://github.com/tpiekarski/pretty-printk/issues/5) | [62be4d5](https://github.com/tpiekarski/pretty-printk/commit/62be4d5c13a6e5bb1de8cc8e2a8fc95c28b7cf53) | done
Pretty print of multiple variables| [#6](https://github.com/tpiekarski/pretty-printk/issues/6) | - | todo
Walking Macro| [#7](https://github.com/tpiekarski/pretty-printk/issues/7) | [ab52416](https://github.com/tpiekarski/pretty-printk/commit/ab5241608e3c6915424e9311a4b499a843b20166) | done
Shortcut for printing conditional expressions | [#8](https://github.com/tpiekarski/pretty-printk/issues/8) | - | todo
Snippets for a few major editors | - | - | todo
Generic testing pipeline with Travis CI | [#9](https://github.com/tpiekarski/pretty-printk/issues/9) | - | todo
Testing pipeline for different major Kernel versions | [#10](https://github.com/tpiekarski/pretty-printk/issues/10) | - | todo
Testing pipeline for different architectures | [#11](https://github.com/tpiekarski/pretty-printk/issues/11) | - | todo
Output surrounding information | [#12](https://github.com/tpiekarski/pretty-printk/issues/12) | - | todo
Convenient throttling of printk | [#13](https://github.com/tpiekarski/pretty-printk/issues/13) | - | todo
Colorize output | [#14](https://github.com/tpiekarski/pretty-printk/issues/14) | - | todo
Little Banners | [#15](https://github.com/tpiekarski/pretty-printk/issues/15) | - | todo

## [License](#license)

pretty-printk is free software: you can redistribute it and/or modify it under the terms of the GNU General Public
License as published by the Free Software Foundation, either version 2 of the License, or (at your option) any later
version.

pretty-printk is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied
warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with pretty-printk.
If not, see [<https://www.gnu.org/licenses/>](https://www.gnu.org/licenses/).

## [Links](#links)

- GNU, GCC, [The C Preprocessor](https://gcc.gnu.org/onlinedocs/cpp/index.html#SEC_Contents)
- Stack Overflow, [__FILE__ macro shows full path](https://stackoverflow.com/questions/8487986/file-macro-shows-full-path)
