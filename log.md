# 100 Days Of Code - Log

### Day 1: January 4th, Wednesday

**Today's Progress**:
- Forked the 100 Days of Code repo and decided to start w/ project that would help me organize Thanksgiving backpacking trip pictures by date/time taken (since timestamp modified field on some pics were simply the timestamp the pics were uploaded, but at least the data is embedded in the filename).
- I'm going to write the script in python since that seems simplest.
- Looked up up python naming conventions: somefilename or some_filename for filename/module and SomeClassName for class name ([source](http://stackoverflow.com/questions/5978557/association-between-naming-classes-and-naming-their-files-in-python-convention)). Actually, [this](http://stackoverflow.com/a/8423697) was a more helpful source.
- Looked up how to get command line arguments: must ```import sys``` and then use ```sys.argv[1:]``` to get a list of the arguments not including the python file being executed ([source](http://stackoverflow.com/questions/4033723/how-do-i-access-command-line-arguments-in-python))
- I wanted to look up how you read in a file, which led me to want to update my python version (I'm at 2.7.6 and feel like I should be coding w/ 3.*), which led me to [this thread](http://superuser.com/questions/241865/updating-python-on-ubuntu-system), which made me want to try using [pyenv](https://github.com/yyuu/pyenv) to allow multiple versions of python to exist (this is the cautious side of me; I'm afraid I might break something in the process of simply updating python [and there's no one way to update]).
- When I tried to install a version using pyenv, I got the following warnings

 ```
 WARNING: The Python readline extension was not compiled. Missing the GNU readline lib?
 WARNING: The Python bz2 extension was not compiled. Missing the bzip2 lib?
 WARNING: The Python sqlite3 extension was not compiled. Missing the SQLite3 lib?
 ```

 But it did say it installed pip and python-2.7.8. Figured I had to install a whole bunch of stuff to get started, so ran the command found [here](https://github.com/yyuu/pyenv/wiki/Common-build-problems): ```sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
 libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils```
 Seemed to give me the same output but w/o the warnings, so maybe we're in a good place?
- Most recent python version is 3.6.0, so that's the other one I'll install and probably also use for the script.

**Thoughts**:
- I do want to continue w/ FreeCodeCamp, but the 'rules' for this challenge require not simply following tutorials.
- Everything feels so rusty. Even just getting a git repo started.

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)
