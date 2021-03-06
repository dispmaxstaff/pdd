[![Made By Teamed.io](http://img.teamed.io/btn.svg)](http://www.teamed.io)
[![DevOps By Rultor.com](http://www.rultor.com/b/teamed/pdd)](http://www.rultor.com/p/teamed/pdd)

[![Build Status](https://travis-ci.org/teamed/pdd.svg)](https://travis-ci.org/teamed/pdd)
[![Gem Version](https://badge.fury.io/rb/pdd.svg)](http://badge.fury.io/rb/pdd)
[![Dependency Status](https://gemnasium.com/teamed/pdd.svg)](https://gemnasium.com/teamed/pdd)
[![Code Climate](http://img.shields.io/codeclimate/github/teamed/pdd.svg)](https://codeclimate.com/github/teamed/pdd)
[![Coverage Status](https://img.shields.io/coveralls/teamed/pdd.svg)](https://coveralls.io/r/teamed/pdd)

Install it first:

```bash
$ apt-get install -y libmagic1 libmagic-dev ruby-dev
$ gem install pdd
```

Run it locally and read its output:

```bash
$ pdd --help
```

Every puzzle has to be formatted like this (pay attention
to the leading space in every consecutive line):

```java
/**
 * @todo #234:15m/DEV This is something to do later
 *  in one of the next releases. I can't figure out how
 *  how to implement it now, that's why the puzzle.
 */
```

It starts with `@todo`, followed by a space and a puzzle marker.
Possible formats of puzzle markers:

```
#224
#TEST-13
#55:45min
#67/DES
#678:40m/DEV
```

Read this article about
[Puzzle Driven Development](http://www.yegor256.com/2009/03/04/pdd.html).
Check also patent application [US 12/840,306](http://www.google.com/patents/US20120023476)

## Rules

You can specify post-parsing rules for your puzzles, in command line,
for example:

```
$ pdd --rule=min-estimate:60 --rule=max-estimate:120
```

These two parameters will add two post-parsing rules `min-estimate`
and `max-estimate` with parameters. Each rule may have an optional
parameter specified after a colon.

Here is a list of rules available now:

  * `min-estimate:15` blocks all puzzles that don't have an estimate
  or their estimates are less than 15 minutes.

  * `max-estimate:120` blocks all puzzles with estimates over 120 minutes.

  * `available-roles:DEV,IMP,DES` specifies a list of roles that
  are allowed in puzzles. Puzzles without explicitly specified
  roles will be rejected.

  * `min-words:5` blocks puzzles with descriptions shorter than five words.

  * `max-duplicates:1` blocks more than one duplicate of any puzzle
  (this rule is used by default).

## .pdd

You can put all command line options into `.pdd` file. The options from the
file will be used first. Command line options may be added on top of them.
