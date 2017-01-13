# 100 Days Of Code - Log

##New Project: Fix Pic Timestamp
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

### Day 2: January 5th, Thursday

**Today's Progress**:
- Looked up how to read and write files in python ([source](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)) and then realized this isn't the kind of reading I'm interested in b/c I'm not reading in text files, but rather images (binary files)
- Was going around in circles looking for file object methods till I came upon [this](http://stackoverflow.com/questions/27580917/get-file-modification-date-in-python) and learned that getting information like the timestamp of a file isn't a method on the file object but from the os.path module T_T
- [This](http://stackoverflow.com/a/39501288) seemed like the best approach for getting the creation date (and modification date instead if can't get creation date) of a file in a cross-platform way.
- Now to figure out how one sets the creation time on files...well, I don't need to set the creation time, just last modified time since that's the usual field you're allowed to sort files w/. Saw from [here](http://stackoverflow.com/a/38754092) and [here](https://www.tutorialspoint.com/python/os_utime.htm) that we can use ```os.utime(path_to_file, (access_time, modification_time))``` using Unix epoch time (seconds since epoch) to set the timestamps.

**Thoughts**:
- Not very productive today. So easily distracted, and it's only day 2. XP

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

### Day 3: January 6th, Friday

**Today's Progress**:
- Looked up how to use regular expressions in python so that I can find a pattern in a string ([source](https://docs.python.org/3/howto/regex.html)).
- Just realized that the pictures have different timestamps based on time zone too...eric's pics are 2 hrs behind the timestamps implied by Jason's pics' filenames since Eric's camera was probably on Central time instead of Pacific time. And then some of Eric's pics no longer have their original modification timestamp and instead have one from when the trip was already over (maybe when Eric uploaded to dropbox?), so there's that batch that I can't help w/. And then there's DFan's, which look like they're 6 hrs ahead of Jason's...oh well, this project is just to get my brain working and not to fix all timestamp problems, so let's see what the best we can do is~

**Thoughts**:
- Squished a bit of time in btwn work and leaving for the LA Zoo Lights event; wasn't technically a full hr today...mainly just realized/thought about "Today's Progress" point 2

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

### Day 4: January 7th, Saturday

**Today's Progress**:
- Was trying to figure out how to take the components of a date (e.g. year, month, hour) and change it to unix epoch time when I came upon the handy table found on [this page](https://docs.python.org/2/library/time.html). Gotta use time module's [mktime()](https://docs.python.org/2/library/time.html#time.mktime).
- Found [this site](http://www.pyregex.com/) helpful for testing out regular expression matching.
- Found the documentation for the match object returned for [match()](https://docs.python.org/3/library/re.html#match-objects).

**Thoughts**:
- Better focused today, but definitely not an hr's worth of focus though that much time had passed.
- Writing steps in "Today's Progress" is helpful to remember what I was last trying to do and keeps me from falling off the rails too far.

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

### Day 5: January 9th, Monday

**Today's Progress**:
- Ah yes, forgot I ended w/ an error. Found this helpful [answer](http://stackoverflow.com/a/9551570). I think I'll take the suggestion of using datetime.datetime() and calling its timetuple() method to get a time.struct_time.
- I'm using this [site](http://www.epochconverter.com/) to help me see if the unix epoch timestamps that get spit out match the date they should be.
- Just realized that in python3, you have to use print as a function (e.g. print('hello')) instead of option to use print as a statement (e.g. print 'hello'). Learned from this [thread](http://stackoverflow.com/questions/28225881/python-string-interpolation-syntax-error).
- Now to make this work for a whole folder as well as the individual file path passed in. I need to know how to extract the directory/folder name from the path passed in, and it looks like [os.path](https://docs.python.org/3/library/os.path.html) has the necessary methods, like [split()](https://docs.python.org/3/library/os.path.html#os.path.split).
- I tried testing os.path.isdir() on "~/Downloads", but it gives False for that...[this](http://stackoverflow.com/questions/36684443/python-3-an-existing-file-not-being-identified-using-os-path-isfile-function) was a good thread to explain why ~ isn't recognized as home (it's cuz it's a shell variable) and what an alternative could be (e.g. use os.path.expanduser()).
- This [thread](http://stackoverflow.com/questions/3964681/find-all-files-in-directory-with-extension-txt-in-python) was helpful to show how one might get all the files of a type found in a directory. I'm going to go w/ the os.walk method from this [answer](http://stackoverflow.com/a/3964691) since it allows you to traverse subdirectories too (since I'll probably want to locally split up the pictures by the person who took them since some may have a similar naming convention but require different 'fixes' to get the order right).
- Hmm, I was able to run the script w/o error on my Downloads folder on my Thinkpad, and it seemed to go through all the jpg's that matched the pattern I was looking for. I moved one of the jpg's into a subfolder to see if it'd go through the subdirectories fine, which it did, but I saw unexpected output: since I had already run the folder through the script, I had expected the 'Before' and 'After' last-modified timestamps to look the same, but the output looked the same as when I ran the script the first time. Maybe I need to do a save of some sort to make sure the changes 'stick' to the file? But none of the examples for os.utime() implied that would be required. Mmm, the output is questionable too; looks like the 'after' timestamp of the file previously processed is the 'before' timestamp of the currently processed file:
 ```
 Before: 11/08/2016 08:40:34 PM
 After: 04/30/2016 08:55:13 AM
 Before: 04/30/2016 08:55:13 AM
 After: 11/08/2016 09:02:20 AM
 Before: 11/08/2016 09:02:20 AM
 After: 11/08/2016 10:28:18 AM
 Before: 11/08/2016 10:28:18 AM
 After: 03/19/2016 06:36:18 PM
 Before: 03/19/2016 06:36:18 PM
 After: 01/30/2016 02:25:19 PM
 Before: 01/30/2016 02:25:19 PM
 After: 04/30/2016 08:58:58 AM
 Before: 04/30/2016 08:58:58 AM
 After: 11/08/2016 08:40:34 PM
 ```
 Ohhhh, just realized it's cuz I passed the path of 1 jpg file to the script, so it's just passing *that* particular path each time to get its timestamp modified. XP I need to change it so that I'm passing the path that's the result of joining the directory name, and the filename.
- Hmm, another problem: why doesn't os.path.isfile(filename) evaluate to True if it's indeed a ... ohhh, I need the full path for os.path.isfile() to be able to check whether it's a file.
- Next task: figure out what needs to be 'fixed' for the others' pics and how it can be done.

**Thoughts**:
- I definitely enjoy any kind of work more when goals are clear and concrete, and I can see the way forward.

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

### Day 6: January 10th, Tuesday

**Today's Progress**:
- Yeah, looks like echow's pics are 2 hrs behind. Oh wait, argh, some of his are just way off cuz it was modified somehow at a later date (uploaded later?). DFan's pics actually have the timestamp embedded in the names like Jason's but w/ "IMG_" at the beginning, so those I can alter. Hmm, maybe for echow's pics that are really off, maybe if I see that the the pic's timestamp is after 11/27, I'll look for the previous pic ('previous' in terms of name b/c the files are named in order taken) that had a timestamp before 11/27 and use that as the timestamp (I can probably do a running update of 'last timestamp' for echow's pics). Yay, we have a plan.
- Note: some of echow's pics end w/ uppercase JPG instead of jpg, so need a case-insensitive match.
- Next: need to see how to add 2hrs to an mtime and need to update pics 'in future' to last valid timestamp.

**Thoughts**:
- Didn't quite code for a full hour, but I was probably as 'productive' as I was in previous days just due to the concentration given to crank stuff out in the limited time I had before leaving to watch La La Land in Ontario Mills, which was worth the rush. (;

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

### Day 7: January 11th, Wednesday

**Today's Progress**:
- Saw this [answer](http://stackoverflow.com/a/13685221/2313357) about using e.g. timedelta(hours=2) to add 2 hrs to datetime object, but I'll still need to turn that into a struct_time to pass to mktime() to get unix epoch time. Oh wait, oops. I need to know how to add hours to a struct_time cuz that's what we get from mtime of a file. Since unix time is just seconds, I can probably just add 2 hrs by multiplying 2 * 60 * 60 to get seconds in 2 hrs. Yeah, seems to be the case by checking on [pythonanywhere](https://www.pythonanywhere.com).
- Realized my logic for processing eric's photos was flawed cuz I keep resetting the last valid timestamp after each photo, so it's always the default timestamp instead of the desired constantly-updated one. XP Hmm, how do I keep track of a variable outside the scope of my function...I could turn this processor into a class and have it keep a variable? Or rather, just the last_valid_timestamp...maybe I'll just have an object that I pass...yeah.
- Lol, I was thinking, "this is the moment of truth..." in preparation to run the script on the folder of pics I selected from the batch of hiking photos, and then I saw it simply exited after the first print statement...so something clearly did not work. Ah, cuz I forgot the trailing slash to let my script know it's the directory. Whee! It [sorta] solved my photo ordering problem! At least the pics have timestamps closer to what they should be though there were still a few that were pretty off. Oh well. Gotta think of sthg new tmrw!

**Thoughts**:
- Didn't think it'd take me so long, but at least the first simple project is finally at a mediocre level!

**Link(s) to work**: [Fix Pic Timestamp](https://github.com/sabliao/fix-pic-timestamp)

##New Project: Can I Eat It? (Web)
### Day 8: January 12th, Thursday

**Today's Progress**:
- I've decided my next project will be the start of a web version of an app my friend jokingly said I should make: Can I Eat It?
- Trying to find a mini-tutorial that'd help me setup a reactjs app w/ webpack, babel, etc, and found 3:
    - [codementor](https://www.codementor.io/tamizhvendan/tutorials/beginner-guide-setup-reactjs-environment-npm-babel-6-webpack-du107r9zr)
    - [freecodecamp](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki/Setting-Up-A-React-ES6-Webpack-Project)
    - [tylermcginnis](https://tylermcginnis.com/react-js-tutorial-1-5-utilizing-webpack-and-babel-to-build-a-react-js-app/) (one I remember going through)

 I'll just start w/ freecodecamp b/c it has the most recent date of the 3 (Aug 2016).
- Got as far as the end of the tutorial for setting up a project. Maybe next time can look up how you structure a multi-file react app.

**Thoughts**:
- I hope I don't keep looking up tutorials at the cost of forgetting to code, but I want to do things the "right" way and have the framework in place.

**Link(s) to work**: [Can I Eat It? (Web)](https://github.com/sabliao/can-i-eat-it-web)
