# 100 Days Of Code - Log

##Project Start Links
- [Fix Pic Timestamp](#new-project-fix-pic-timestamp)
- Can I Eat It? (Web): [first day](#new-project-can-i-eat-it-web)
- [Tribute Page (FreeCodeCamp)](#new-project-tribute-page-freecodecamp)
- [Personal Portfolio Webpage (FreeCodeCamp)](#new-project-personal-portfolio-webpage-freecodecamp)
- [exercism.io Practice](#new-project-exercismio-practice)

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

##New Project: Tribute Page (FreeCodeCamp)
### Day 9: January 14th, Saturday

**Today's Progress**:
- I'm lower energy today and am not sure I'll be able to focus enough to have a productive time if I need to follow some other post about how to set up a multi-file react app, so I'm going to continue w/ the FreeCodeCamp track, esp. since the next item on the list is to build a tribute page, and at least that's more than just following a tutorial. XP
- Wanted to know how to do rounded corners for a background like in the example ([answer](http://stackoverflow.com/a/6484880)).
- Hmm, I should look up what the standards are for showing html elements (I already forgot...).
- Nevermind, stopped work to have phone call w/ friend.

**Thoughts**:
- It's so easy for me to skip/forget a day if time for this isn't scheduled (since it's not part of some daily routine that happens at the same time every day, which would make it easier to remember).

**Link(s) to work**: [Tribute Page](http://codepen.io/sabliao/full/qRadMr/)

### Day 9.5-9.9: January 15th, Sunday; January 16th, Monday; January 18th, Wednesday

**Today's Progress**:
- Reading [this](https://www.smashingmagazine.com/2009/07/html5-and-the-future-of-the-web/) and [this](https://www.smashingmagazine.com/2009/08/designing-a-html-5-layout-from-scratch/) to learn of some semantic html elements.
- [Re]learned how to center an img by seeing this [jsfiddle](http://jsfiddle.net/3k3CC/1866/) example: you put the img in a div, set auto for margin-left an margin-right on the containing div, make img a block element, and then set img margin to auto.
- Next, figure out how to make text below image the same width as the image w/o setting a width on the image.

**Thoughts**:
- At the rate I've been going, this challenge may end up taking the whole year...but I do think relationships are still a higher priority, and however many mistakes I make on the way towards learning to find balance and boundaries, I'm still praying God will make something beautiful out of my proffered crumbs.
- An hr of coding is not very productive when a sudden mental reminder to do X flashes across the display of one's consciousness every 5 min.
- Sore muscles, cold extremities, and an emptying stomach are quite the distractions.

**Link(s) to work**: [Tribute Page](http://codepen.io/sabliao/full/qRadMr/)

### Day 10: January 19th, Thursday

**Today's Progress**:
- [This](http://stackoverflow.com/a/618737) gave me a starting point for how to get the text and main image the same width, but then I realized I could just use padding on my 'shell' element (the element w/ the light gray background inside which all my content would be placed).
- Finally finished the tribute page! Didn't expect this to take more than 1 night for sure...

**Thoughts**:
- It's not a binary choice between improving yourself career-wise and placing God and people above that.
- Lol, I spent most of today's coding period using my rusty writing skills to write about Naruto's creator, Masashi Kishimoto.

**Link(s) to work**: [Tribute Page](http://codepen.io/sabliao/full/qRadMr/)

##New Project: Personal Portfolio Webpage (FreeCodeCamp)
### Day 11: January 20th, Friday

**Today's Progress**:
- I'll try the next FreeCodeCamp project cuz it comes right after the Tribute Page one: a personal portfolio webpage. It'll probably be very empty.
- Reading [this](https://skillcrush.com/2015/03/12/impressive-tech-portfolio/) and [this](https://medium.com/@learntocodewithme/15-web-developer-portfolios-to-inspire-you-137fb1743cae#.kav329h6t) for inspiration on how to put one together.
- Cool, there are such things as [css variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables) that you can define on e.g. the [:root](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) pseudo-class.

**Thoughts**:
- Not much done, but learned about 2 new things! Off to prepare for tomorrow.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 12: January 25th, Wednesday

**Today's Progress**:
- I want to get that parallax effect w/ a background image and style my site similar to example #6 [here](https://medium.com/@learntocodewithme/15-web-developer-portfolios-to-inspire-you-137fb1743cae#5677). [This](http://keithclark.co.uk/articles/pure-css-parallax-websites/) was a cool article on how you use pure css to get the parallax effect (on mobile too)!
- I'm using this [article](https://css-tricks.com/perfect-full-page-background-image/) to show me how to have a background image fill the entire canvas. Mmm, I can't get my google photo image to show though. Oh, I forgot it's cuz my photo's served via https and codepen's using http and so won't show 'secured' content.
- Hmm, I keep getting the following error even though I have jquery in my list of added javascript before bootstrap's js:
 ```
 Uncaught Error: Bootstrap's JavaScript requires jQuery
     at VM142 bootstrap.min.js:6
 ```
- From this [thread](https://teamtreehouse.com/community/is-there-anyway-to-add-your-images-when-using-code-pen), I decided to sign up for cloudinary to host my picture. Cool service.
- Having trouble getting the parallax effect to work w/ my background and having my foreground not block it. Realized I need to have my background image directly on the background layer of the parallax html structure and not on a child element inside.

**Thoughts**:
- Again, not much to show, but really cool to see that the parallax effect can be done so easily! I'll want to eventually figure out how I can get the picture to stay on the whole page even w/ scrolling (I get a lot of whitespace on the bottom).
- I need to just lay stuff down next time and not worry about it not being quite right the first time. Need to get used to simply working through, like drafts, which I was never good at b/c the perfectionist inside has complaints. XP

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 13: January 26th, Thursday

**Today's Progress**:
- Gonna look for free fonts I can add via a cdn. Getting the links through [http://fontcdn.org/](http://fontcdn.org/); I chose Cinzel for now. So easy!
- I wanted to add an outline (learned later called 'stroke') to my links so that they're more easily readable. Saw this old [page](https://css-tricks.com/adding-stroke-to-web-text/) that showed how you can use webkit to do it (can set a default text color if not a webkit browser and use -webkit-text-fill-color to override the color style).
- Need to get font awesome icons for social media links.

**Thoughts**:
- Codepen's html preview has been very finicky. I often need to see the full page preview to actually see how the page looks instead of simply relying on the html section in the developer view.
- Seeing things actually come together helps w/ momentum and motivation.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 14: January 30th, Monday

**Today's Progress**:
- Added social media icons and links. Learned about sizing for icons, but didn't figure out how to actually make the icons all the same height.

**Thoughts**:
- slow
- are social media links helpful if most all my accounts are private?

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 14.5: January 31st, Tuesday

**Today's Progress**:
- I'm trying to figure out how to evenly space items horizontally and am finally learning/reading about [flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).
- [Autoprefixer](https://css-tricks.com/autoprefixer/) sounds like a cool thing we could use for actual projects as it removes the need to remember vendor prefixes for css and seems not too hairy to integrate.

**Thoughts**:
- Even though I wanted to model my page after pierre.io, the fact that you can't access the navigation links (to the rest of the page) after scrolling down is annoying, so I'll probably add a header navbar (was also thinking of side navbar, but to make it simple and keep it mobile-friendly, will go w/ header).

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 15: February 1st, Wednesday

**Today's Progress**:
- Hmm, I can't do position: fixed on the header navbar cuz the parallax__layer already sets the layer to have position: absolute, so position: fixed doesn't actually stay in the same place relative to the browser window. Or at least that's my hypothesis. Even placing the header/nav block outside of and after the parallax blocks, it still looks like it's got default positioning...oh wait, I just realized I'm looking at the elements for my page's sections (e.g. Projects); no wonder...

**Thoughts**:
- Need to figure out how to get the linking to the sections of the same page working since my use of # is not working.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 16: February 2nd, Thursday

**Today's Progress**:
- Lol, just realized my linking wasn't working because the id for the linked-to element isn't supposed to have the # in front of it.

**Thoughts**:
- Unsuccessfully tried to get active links to work w/o javascript. Maybe I was reading things wrong.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 17: February 6th, Monday

**Today's Progress**:
- I'm trying to get active link styling to work again. For some reason, just clicking on 'Home' link will give the link a text-decoration of underline even though through the inspector, text-decoration for a link should always be none. 0.o Well, I moved that style rule from the hover state to the anchor element (for the main nav), and now there's no underline.
- Hmm, also, clicking 'Home' doesn't bring me back to the top of the page. Based on this old [article](http://www.promo.sharmweb.net/simplest-html-home-and-back-top-link-works-all-browsers), simply using href of '#' should do the trick, so I dunno why that doesn't work for me. Mmm, maybe it tries to go to the first element, but since my first element is the navbar, which is always showing, it doesn't move? That's my best hypothesis. I'll get around this by setting an id on the main element for home. Oh darn, that doesn't go up quite high enough (ends up w/ my name half-covered). Even moving the id up one element (to the parallax layer) didn't change things.
- I can't get the scrolling to work using the example jQuery code [here](https://codepen.io/MyXoToD/post/look-ma-such-a-smooth-scroll) as a basis (and checking [this](http://stackoverflow.com/a/9696633) to remember how to target an element using an attribute match). Instead of scrolling $('html, body'), I decided to try to scroll on the main parallax layer element, but that didn't work either. Made sure to add a ```return false``` statement at the end of the click handler function as seen [here](http://stackoverflow.com/a/5580456), but that didn't work either (note to self: ```$('html, body')``` is used for cross-browser compatability, briefly mentioned [here](http://stackoverflow.com/a/26050575)). Maybe I'm not targeting the element to which the scrollbar belongs (going off this [answer](http://stackoverflow.com/a/26050549)), but I don't know what else to target...ohhh, I had to target the parent div element that contains both the background and main parallax layers. Whee!
- To get the active link clicking working, needed a combination of references:
    - [how to remove and add classes](http://stackoverflow.com/a/28443371)
    - [how to target class on same element selector in scss](http://stackoverflow.com/a/11084798)

**Thoughts**:
- It's been a while since I've touched jQuery...

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 18: February 7th, Tuesday

**Today's Progress**:
- Gonna add thumbnails to my 'projects' section. Oh, but first, why's all the text after the social media icons off to the left? 0.o Oh, it's actually centered, and it's the *top* part that's off to the right a bit due to a custom margin-left I had applied to it in an attempt to have the text not overlap w/ a dark object in the background image.
- Ooh, just saw this cool site/service that gives you placeholders of any size called [placeholdit](https://placehold.it/).

**Thoughts**:
- I do eventually want to have each linked-to section work as a sort of sticky element so that scrolls snap in place, but for now, I'll just work on content.
- I was thinking to upload whichever thumbnails I end up using to cloudinary and use their service of giving me a resized image...it should be faster than my codepen's css is what I'm thinking.
- For skills section, maybe can have each 'skill' be represented by that framework/tool's icon.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 19: February 8th, Wednesday

**Today's Progress**:
- Instead of just having thumbnails of projects, I'll add a description beside each one to give more background. For ones that you can't really see from a public visit (e.g. Legacy or non-existent ones like Cytosport), maybe I can have a modal pop up to show a bit more about it w/ more screenshots. I'll leave that (modal popup) as a todo for next time b/c I'll need to spin up my vagrant instances or just start up my local webserver for these older projects to actually get screenshots of them and describe them (I don't even remember how we used to get them running). Might be nice to have a timeline of sorts to show when each project happened, but that'd be more like a sticky link for each year as scroll down through the projects. Mmm, I'll leave the sticky aspect of the year link for another time.
- 3rd comment on this [answer](http://stackoverflow.com/a/8579673) helped me get started on figuring out how to at least have my year link scroll to the top of its div (even if I leave the sticky part for later).
- Hmm, I'm trying to get all my nav links to scroll to the appropriate spot (so can just have one handler taking care of that for all), but the scrollTop values seem off (goes to high or too low) except for the value of 0 for home...oh, I think it's cuz I need to take into account where we currently are on the page in terms of scroll position; no wait, that's what offset()'s supposed to do. Turns out [position()](http://api.jquery.com/position/) is what I needed.
- I have a mystery underline for my year link...can't figure out what's triggering it (it's not any of the element states I can toggle). It happens after I've clicked on the link and hover wherever the text *isn't* at in its area (i.e. in the blank space underneath or to the side). Ahh, this [answer](http://stackoverflow.com/a/27989757) made me aware of yet another element state: "a:link", for an unvisited link (which doesn't make sense in this case as to why the underline would come after I've clicked the link), and that was the one I had to target to get rid of the underline finally.
- Wanted to add stroke to my year text so easier to see; this [post](https://css-tricks.com/adding-stroke-to-web-text/) helped.
- Since my logs are so long, decided to add links at the top to navigate to the start of each project. [This](http://stackoverflow.com/a/16426829) helped me figure out how to link to headers.

**Thoughts**:
- Not really doing as much web dev practice as content creation for this webpage. XP
- I should use [parallax sections](http://keithclark.co.uk/articles/pure-css-parallax-websites/#parallax-sections) to give the projects section a different background (otherwise, too hard to read descriptions on the main photo background).
- Need to get my old projects up and running to use as fodder for the webpage.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 20: February 9th, Thursday

**Today's Progress**:
- Trying out parallax groups, but it's a lot harder to get it working for me than I expected. I can't figure out why my content for different parallax groups end up on top of each other. Tried to inspect the [demo](http://keithclark.co.uk/articles/pure-css-parallax-websites/demo3/) but haven't figured out what's wrong.
- Hmm, that's weird, I saw that the pen was exported as a gist for an anonymous account when I did the first time, so I assumed my github account wasn't linked, but now that I'm checking it again, it's indeed linked, and when I exported the 2nd time, it exported to a different gist instead of the same one (probably cuz it's exporting as an anonymous user). Had to unlink my github account and relink it again. [Here](https://gist.github.com/sabliao/3b3be18afbae4da2015127f6cac5e877)'s the permananet gist link.

**Thoughts**:
- Downside of using codepen for developing is there's no versioning, so if I wanted to go back to undo a bad series of changes, it'd be impossible if the changes weren't done in the same session. Oh, but there's a feature where we can export codepens to a github gist, which will essentially act as version control, yay! [[ref](https://blog.codepen.io/2016/09/19/using-gists-see-versions-pens-dif-pen-changes/)]. Cool, ~~[here](https://gist.github.com/anonymous/e5eea89b8a62c2f660f4ead2f91928b8)'s my gist link.~~(see link under "Today's Progress")

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 21: February 10th, Friday

**Today's Progress**:
- Ah, issue w/ overlap from yesterday was that I was missing closing div tags on the parallax groups.
- Ooh, can just crop my background image (I don't want it as tall) using cloudinary; just need to access a specific url like http://res.cloudinary.com/sgl/image/upload/c_crop,h_710,w_2560/v1485406016/IMG_20161024_211640_otpuk0.jpg
- Was playing w/ layer placement and scale and then discovered I couldn't click on my links anymore. It *looks* like my background layer for my project section is 'on top' of that area of my first parallax group (w/ the mini bio + picture & social media links) based on what my right-click inspect returns (i.e. when I right-click > inspect on my profile pic, I get directed to the background layer of the project group), but the z-index for backgrounds are 3 while main layers are 4, which should cover any background layer. :/ Wish the css styling suggested by the blogger from whom I learned about parallax layers worked on my site (all I see are long streaks of color) or that I'd be able to figure out the magic numbers that'd make the 3-d effect work. Ah, it was easier to not do the transform thing and simply apply the border outlines of each parallax layer, so that helped me see when the project background layer was still covering my base layer of my intro section.
- Ah, reading [this](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/) is helping me understand how it's possible for a higher z-index to be below another one (esp. helpful was the added 'Update' note in the [stacking contexts](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/#stacking-contexts) section). I think in my case, it has to do w/ transforms being applied on the background layers (so that they can appear farther away and scroll at a different speed -> parallax effect). Wonder if there's a way around this...

**Thoughts**:
- Oof, tricky css gotchas.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 22: February 13th, Monday

**Today's Progress**:
- I'm rereading the stacking contexts article, but I don't see how the the parallax groups, which are the parent elements contaiing a background parallax layer and a base parallax layer each, are forming new stacking contexts, so I don't know why the z-index...nevermind, parallax groups are forming a new stacking context due to the ```transform-style: preserve-3d;``` styling. I just tested in a codepen [here](http://codepen.io/sabliao/pen/GrzWLq). See how the pink goes over the dark green even though the green has a higher z-index? If comment out the preserve-3d transform-style styling on .group elements, the stacking would be solely based on z-index then default to order of appearance when z-index's are the same.
- Checking the parallax demo. Ah, looks like he got around the issue by setting z-indexes on the groups themselves. Lol, but now parts of my second group are hidden behind my first group's background cuz there's some overlap...hmm, and I see why my 'Projects' group is so far up into my main/intro one, and it's because the parallax group has a height of 100% of the viewport, so the next parallax group gears up to be right after that. I realize I don't need it to be 100vh (the blog w/ the demo said he just wanted every group to fill the viewport but that arbitrary values can be set for that), so I'll fix that now! I figured I'll just take the height requirements out all together b/c who knows how long each group will be on each device? But it looks like if I remove the height setting for .parallax-group, the whole page just turns white (removing from .parallax [parent element] messed up the look too, but at least there was sthg you could still see). T__T I fiddled w/ the height and ended up removing the z-index's I had added for the parallax groups (in an attempt to put the first group above the second group so that picture and icons wouldn't be blocked), but now we're back at the same problem of having the picture and icons unclickable until they slide up from under the 'background' layer of the second group.

**Thoughts**:
- Gonna get rid of parallax effect and stick w/ simple non-moving backgrounds b/c this is not worth the effort.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 23: February 14th, Tuesday; February 15th, Wednesday

**Today's Progress**:
- Ooh, actually, if I just remove the transform styling, the site looks okay if I just leave everything else the way it is. Of course, need a few adjustments for placement, so gonna work on that, esp. now that the lamppost in the background picture is blocking part of my main text.
- Hmm, strange: when I first tested some changes to the background's css rules/positioning, I thought I was able to get it perfect w/ breaking up the background css rule into a background-image, background-position (gave it value ```calc(50% - 75px) 50%``` w/ help from [here](http://stackoverflow.com/a/25955384)), and background-repeat (w/ value ```no-repeat```), but when I transferred that over to the actual code and refreshed the page, it looked messed up and said the background-position code was invalid. Oh, I guess the spaces before and after the minus sign are really important in the calc() function. Also just realized that the background size changes if you open the inspector tool and if you keep background-size to the value 'cover'.
- Can't figure out why I can't get rid of the white space above my name title even after changing margin to padding and changing my background for my base layer to transparent. Ah, it's actually cuz I misunderstood the positioning style and a higher percentage for the second number makes the photo go down, not up. Got it working, at least on a desktop...

**Thoughts**:
- This css stuff takes me longer to figure out than code sometimes. XP

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 24: February 16th, Thursday

**Today's Progress**:
- Oh darn, just realized I don't have my old code on this partition (Ubuntu 14.04) and only have it in the 12.04 partition, which was made inaccessible by my n00bness while trying to install 14.04. T__T. One last place the old code could be is on my mac, which came much later. Will have to try another time.
- Background options for projects section (and other sections too): darkgray, gold, lightskyblue, maroon, orange, powderblue, silver. I think I'll go w/ orange for projects.
- Realized that I didn't actually remove all the parallax styling, so I'm commenting those parts out to see if it'll remain about the same. I can't understand why there's an overlap of the elements when the window's squished though but okay when the window's full-sized. I've commented out all height stylings...

**Thoughts**:
- Again, css is beasting me.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 25: February 17th, Friday

**Today's Progress**:
- Oh, nevermind. Apparently a complete refresh of the full page shows that the content overlaps regardless. Ahhh, it's the position: absolute rule I missed seeing!
- Adding skills.

**Thoughts**:
- Focussss

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 26: February 18th, Saturday

**Today's Progress**:
- Finishing up skills section. I'm liking the way it looks!
- Notes/drafts for descriptions for old projects I'll need to look for:
    - make sure to briefly describe what each app was for at the start of each description
    - irn realty (old site): first web app, in-over-my-head feelings intensified w/ a lot of firsts packaged into [what felt like] one elephant of a project: had to learn how to integrate w/ API services (both w/ CARETS [describe this] *and* googlemaps api), figure out how to programatically create sitemaps and site indices to send to search engines, learn about a new database (all example Symfony projects I'd been exposed to up to that point had used MySQL) as well as how one would use a mapreduce function to find properties near a specific property using latitude and longitude coordinates, learn about mail services(?), set up infrastructure through AWS by myself, all while barely having gotten a grasp of how the various components of the Symfony framework came together. The later addition of a new service called Click(?), which visually captured mouse movements and clicks on a website, proved to be a test of patience. [add in how Phu redid app in 2015 to use new stack of python-eve and angularjs, which made app much faster and new look given by the designers improved the overall feel]. I came in, as I usually do, after the groundwork was laid and continued development of features as requested by the client. Had to think more with responsive design at forefront of mind. Current site at: http://irnrealty.com/search.
    - (the spine health products website): lead developer decided he wanted me to try a fledgling framework called Sylius that had the cart flow built into it. It was my first time dealing w/ multiple payment gateways(?) and a first w/ shipping (used yet another shiny, new 'toy' for handling shipping called RocketShipIt) and learning what a nightmare shipping can be when you have items of various sizes and are trying to give an estimate for how large the overall containing box would be. Due to the young nature of Sylius, there were still a high number of kinks that were yet to be resolved; I learned to not blame myself for every instance of non-working software; it was also the first time I became rather active on StackOverflow and on a GitHub repo. Beyond that, learning how to mold the project's needs to the narrower, highly specific structure of Sylius was quite the challenge.
    - cytosport (2014-2016): first(?) dealing w/ ecommerce and for a well-known brand (in the sports nutrition industry). first time dealing with import of images and storage of them as well as import of files from client via browser and ftp for faster updating of item and order information. first time figuring out how to get ElasticSearch to work so that products would be easily searchable. first huge disaster with payments and verification and learning how transactions and authorizations with credit cards worked. ... Unfortunately, eventually bought out by Hormel, and a budget for this new wholesale-to-customer ecommerce website no longer existed, so we began the process of retiring the website.
    - LakinTire: ...
    - GDB: first use of internally created bundles (we were trying to go in a direction where we build many small bundles/components that could be used for multiple projects). Similar issue w/ having used
    - Legacy: first time being tasked to come up with wireframes for the app (but was also thankfully given feedback by our interim manager at the time). First time using the angularjs + python-eve stack for an application (though the first draft of the website was still started by our lead developer first). Good ramp-up challenge since it had been a while since I had to familiarize myself with a new framework. one of biggest challenges was learning how the 3-part pdf generation process using aws lambda functions worked and how to understand and resolve the problems that cropped up when reports were generated.

**Thoughts**:
- I'll need to do a lot of reading of old google docs to remember exactly what I had done and when for each of the old projects. And to see how I can start up old projects to potentially get a screenshot of an old site (otherwise, can fallback to using logo's)

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

##New Project: exercism.io Practice
### Day 27: February 22nd, Wednesday

**Today's Progress**:
- Gonna practice python on http://exercism.io/.
- I'm trying to follow the instructions [here](http://exercism.io/cli/mac) for installing exercism, but I'm getting an error when I try to run the brew commands:
 ```
 /usr/local/Library/brew.sh: line 32: /usr/local/Library/ENV/scm/git: No such file or directory
 Error: update-report should not be called directly!
 ```
- Found this [fix](https://github.com/Homebrew/brew/issues/557#issuecomment-233710397), yay!
- Finished submitting first exercise

**Thoughts**:
- Wow...the 'previous' day was 4 days ago. Just goes to show, there's always something in life that'll come up, which is why scheduling is helpful in getting *anything* done.
- Took a while to figure out that the test suite didn't want me to run my own function to print out the hello world message and that printing wasn't what was desired but rather the return of the desired string (instructions could've been clearer), but yay for first pass. Hopefully subsequent exercise submissions will go faster.

**Link(s) to work**: [Hello World (Python)](http://exercism.io/submissions/814f6dac195d4c2da921afe3e7863c23)

### Day 28: February 23rd, Thursday

**Today's Progress**:
- Will continue to practice python on http://exercism.io/.
- Submitted exercise 2

**Thoughts**:
- These are actually 'fun', but maybe it's b/c I'm not struggling and being stuck w/ some error I can't get to the bottom of.

**Link(s) to work**: [Leap (Python)](http://exercism.io/submissions/cea2a672c84e4bd285196461add6c6ef)

### Day 29: February 25th, Saturday; February 26th, Sunday

**Today's Progress**:
- Gonna read up on my old projects and try to get them started so that I can get screenshots.
- Darn, can't get my old irnrealty project running. Guess I'll just use the screenshot of the current site.
- Looking at my site again, the background is too small for the space it should be taking up (white space at top and bottom), the cause of which is eluding me. I don't remember changing the size; I just remember it being the right size after removing all the parallax styles. Ohhh, actually, I see that I was using a cropped version of my background. I think I just need to increase the height specified via the cloudinary url.

**Thoughts**:
- Life happens.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 30: February 28th, Tuesday

**Today's Progress**:
- I'll try to do a mix of a lil coding and working on my page b/c I want to progress on both fronts. Hopefully I can get exercism installed on this other computer I'm using now as well as get some more work done at least on the written content side for the page.
- Didn't get to the personal page today.

**Thoughts**:
- Actually, after reading over a message from an acquaintance from back in August, I feel like I should focus on strengthening my javascript instead of broadening out to get better at Python b/c I still don't have a skill that's at a 'hireable' level just yet. Thus, I'll start the javascript track on exercism.

**Link(s) to work**:
- [Hello World (JavaScript)](http://exercism.io/submissions/232a5ac55eb7468e973ebe42c08397af)
- [Leap (JavaScript)](http://exercism.io/submissions/28af5f9f092244d3980047b9f62f36a3)

### Day 31: March 1st, Wednesday

**Today's Progress**:
- Completed 3rd javascript exercise.

**Thoughts**:
- March 1st coding was only half an hour, but thought it'd be better to do something than nothing, so did one more exercism exercise. Completed it faster than I thought it would. Having 'deadline' (in this case, to go to bed) helps things get done faster. :P

**Link(s) to work**: [Hamming (JavaScript)](http://exercism.io/submissions/cf324272b80d4c6fb22ae3754b727d4b)

### Day 32: March 2nd, Thursday

**Today's Progress**:
- Completed 4th javascript exercise. This guy's [iteration](http://exercism.io/submissions/3f11535be2724629bca84382f38dac04) looks better/cleaner; he uses Array.prototype.foreach!
- I'm working some on the content of my personal portfolio page. I see that the amount of text can look cumbersome (I should also look into getting another font that's not all capital letters), so I want to add a bottom border to just the project thumbnail and the description columns for each row but not under the year column. However, when I try to group the image and description in a parent div, that messes up the grid layout. Only solution I can think of now (and even this is found from a stackoverflow question) is to add another row after every project row to specify I want a div that has the offset and combined width of the thumbnail and description columns and have a border styled for that row. There should be a better way to do this but can't think of one right now.

**Thoughts**:
- I'm glad I'm doing these javascript exercises b/c I'm realizing the need to write out (and dig through old journals to find the missing details) is what's making me put off returning to 'finishing' that page. XP
- Maybe I can put the descriptions in modal windows and then next to each thumbnail, have a link to the project and a button to launch the modal to see more info. This way the layout will look less clunky.

**Link(s) to work**:
- [RNA Transcription (JavaScript)](http://exercism.io/submissions/f06fe3f407d34a9694fc33440ed4a68e)
- [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 33: March 7th, Tuesday

**Today's Progress**:
- Completed 5th javascript exercise (Pangram).

**Thoughts**:
- Eating out a lot...
- I just looked at the implementation of the guy below me [here](http://exercism.io/submissions/28a6c05bde8049d38f6d2792dc91a003), and it's so good... faster implementation (e.g. don't need to go through and search all 26 letters if just go through and remove a letter once you see it), cleaner code (e.g. use of String.prototype.split('') on string of alphabet letters to create the array), good variable naming (e.g. 'phrase' instead of 'string' like I used, lol), and use of regular expression to remove ... unnecessary characters? Not exactly sure what /[\"\s!?,\t\n\t]/g is supposed to represent.

**Link(s) to work**: [Pangram (JavaScript)](http://exercism.io/submissions/15d689121c154f15adaf038633c48d72)

### Day 34: March 29th, Wednesday

**Today's Progress**:
- Read this [answer](http://stackoverflow.com/a/10940138) and saw that using a regex object's test() function is faster than String.prototype.match(regexpObj) since the latter gives you the actual matches while former just lets you know if expression exists.
- Completed 6th javascript exercise (Bob).
- I only looked at the person who submitted right before me [here](http://exercism.io/submissions/178e204dcc684589bea2f9f4df608d5f), and I was super impressed by how organized she wrote her code! And in such a different and still clear way so that no comments were needed to explain anything; the code speaks for itself. There's some unnecessary code (checking for a number question vs just a number) and some of the checks are way too specific to the test cases, but I still like how she approached the problem in general.
- Gonna read a bit through http://eloquentjavascript.net/

**Thoughts**:
- Taking umlauts into consideration (hex code) wasn't as intimidating as I first thought.

**Link(s) to work**: [Bob (JavaScript)](http://exercism.io/submissions/b9c9d7c48a784022b002b22a4f70aafc)

### Day 35: March 31st, Friday

**Today's Progress**:
- Gonna suck it up, override my perfectionist tendencies, and just paste what I have so far for the different projects I wrote draft descriptions for onto my personal portfolio webpage so that I can continue w/ FreeCodeCamp.
- Still in progress for putting in descriptions...

**Thoughts**:
- Goodness, the amount of text makes the site feel so unwieldy. Well, at least I'll commit to putting the text down. Maybe it won't take too long to change it so each thumbnail has a link next to it that opens a modal that'll have the scrolling text...

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 36: June 7th, Wednesday

**Today's Progress**:
- After dumping of the rest of the drafts for explanations I already had from an earlier log, I _actually_ just submitted my portfolio page as-is this time. Maybe it helps that I'm so far removed from work on it that my perfectionist tendencies are out the window on this one.

**Thoughts**:
- Lol, I clearly did not "suck it up" like I said I would last time.
- I felt bad/a lil ashamed at having told a friend I still hadn't restarted my self-learning. I had sent her a text about that today and even mentioned my idea of a way forward (just submit my personal portfolio webpage as is cuz I know it's been the big blocker to my continuing forward due to my insistence that it be 'complete' before submitting, and then just restarting w/ a bite-sized chunk), so I felt like today was the day I should do that. It's been a while.

**Link(s) to work**: [Personal Portfolio Webpage](http://codepen.io/sabliao/pen/mRmbMy)

### Day 37: June 13th, Tuesday

**Today's Progress**:
- Gonna just continue w/ freecodecamp.com progress.

**Thoughts**:
- Why did they give such a relatively 'complex' project of setting up one's portfolio page (including a user story where one should be able to click on a section tab and have the page scroll down to the appropriate section) *before* all this really basic javascript stuff?

### Day 38: (some other days), June 27th, Tuesday

**Today's Progress**:
- Continuing w/ freecodecamp.com

**Thoughts**:
- Super basic code is killing me too.

### Day 39: July 27th, Thursday

**Today's Progress**:
- Tried out a codewars exercise

**Thoughts**:
- So hard to concentrate after not having had to in this way for a while. Ended up doing other things like cutting my nails and learning a lil about the best woman fencer in the country and world, who's currently at Notre Dame.

### Day 40-41: August 2nd-3rd, Wednesday/Thursday

**Today's Progress**:
- Finally bought 3 udemy courses yesterday to give me more structure, challenge, and motivation to get off my butt. Doing ~1 hr of Modern React w/ Redux and ~1 hr of Learning Node.js

**Thoughts**:
- This way of going about spending time w/ code and learning is definitely the lower-threshold method I needed to help me get into a routine.

### Day 42: August 6th, Sunday

**Today's Progress**:
- ~1 hr of Modern React w/ Redux and just under half an hr of Learn and Understand Node.js (got sleepy)

**Thoughts**:
- N/A

### Day 43-44: August 15th, Tuesday & August 17th, Thursday

**Today's Progress**:
- ~1 hr of Modern React w/ Redux and an hr of Learn and Understand Node.js

**Thoughts**:
- N/A

### Day 45-51: August 19th, August 22nd-24th, August 28th-29th, August 31st

**Today's Progress**:
- Watched s'more of the Modern React w/ Redux and Learn and Understand Node.js videos.

**Thoughts**:
- N/A

### Day 52: September 2nd, Saturday

**Today's Progress**:
- Watched s'more of the Modern React w/ Redux and Learn and Understand Node.js videos.

**Thoughts**:
- N/A

### Day 53: September 4th, Monday

**Today's Progress**:
- Trying out React-Native for a bit.

**Thoughts**:
- N/A

### Day 54: September 11th, Monday

**Today's Progress**:
- Watched s'more of the Modern React w/ Redux and Learn and Understand Node.js videos.
- Read a lil about API keys and security issues while going through the Modern React course.

**Thought**:
- N/A
