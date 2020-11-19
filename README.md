# tomato

A pomodoro logger and timer for the terminal


Introduction
------------

I am a fan of the pomodoro technique. I have used gnome-pomodoro happily so far, but I found it had the following features that I was missing:

 1. I do most of my work (programming) on the terminal. I wanted something bare-bones for the terminal, so that I wouldn't have to deal with minimizing/maximizing windows and pressing start/stop buttons.

 2. More importantly, I feel like my pomodoros are far more effective when I log them. However, this adds an extra layer of complexity with a gui app like gnome-pomodoro, since I need to remember to write something in my log, either before or after each pomodoro timer has completed. It's so easy to forget to do this, or simply not bother. This is very frustrating if you later want to use your pomodoro logs for planning, e.g. "how many pomodoros does this kind of task usually take?", "how many pomodoros can I usually do in a day?", "what kind of tasks take me more pomodoros than others (possibly for psychological reasons)", etc.


`tomato` addresses both problems. It is a bare-bones pomodoro logger/timer, which forces you to launch each pomodoro interval separately in the terminal, and allows providing a description as an optional argument, thereby encouraging logging with minimal effort and thought.


Installation instructions
-------------------------

1. Edit the `tomatoconfig` file as appropriate

2. Make the files `tomato`, `tomatoconfig`, `tomatoes`, and `untomato` executable

3. Copy them to /usr/local/bin (or simply add the directory containing these files to your PATH)


`tomato` has the following dependencies:

 - The `sox` package (provides the 'play' function for playing audio files)

 - Optionally, the `gnome-pomodoro` package, if you intend to use the default sound files I used, which were shamelessly stolen from gnome-pomodoro.


On apt based systems you can install these via

    sudo apt install gnome-shell-pomodoro sox


Usage
-----

Type `tomato` to log a tomato without a description

Type, e.g. `tomato Solving Math Problems` to log a tomato with the description "Solving Math Problems"

Type, `tomato continue` to log a tomato that repeats the previous description used (i.e. continuing with that task)

Type `untomato` to remove the last entry from the log. If no more entries remain, the logfile itself will be deleted

Type `tomatoes` to inspect the current state of your tomato log


Notes
-----

- You can press Ctrl-C while a tomato is running to terminate that tomato; note that this does not remove the entry already logged (therefore this is also an easy way of adding a tomato to the log without having to complete the timer interval required)

- It is **not** possible to 'pause' the timer. Obviously it _is_ possible to do Ctrl-Z on a linux terminal (which effectively stops the ticking sound -- `fg` will resume the sound), but this does not pause the _timer_ itself. This is a feature, not a bug. I consider "pausing" a pomodoro interval to deal with interruptions, to defeat the whole point of the pomodoro technique. Either your interruption is of the kind that you can quickly 'jot down' while the tomato is running, so that you can deal with it _after_ the tomato has finished, _or_ it is a significant interruption that has destroyed your current tomato as a unit of uninterrupted focus. If this happens, you should cancel your tomato, and `untomato` the invalid log.

- The way I, personally, use this, it to save my tomato logs inside a dropbox folder, which I keep synced on my phone. This allows me to inspect my logs from my phone if needed. I've left my personal default folder reflecting this in the `tomatoconfig`, but obviously you should change it to whatever works for you.

- For the name of the logfile itself, the default saves it to today's date in yyyy-mm-dd format. This means that running `tomato` will add a log to a file with today's date. Tomorrow it will start a new file, and so forth. This means that you do not need to specify each time at the terminal 'where' you want to log your tomatoes. However, if this is not the behaviour you want, you can edit `tomatoconfig` to use a different system (e.g. a fixed file).
