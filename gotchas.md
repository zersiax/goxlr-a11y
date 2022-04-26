# Gotchas and Things to Know

This file is here to document the various oddities the GoXLR and its accompanying app sorta just expects you to roll with, as it were. There's several things that are non-apparent and can only be verified visually, which is what I've been  doing over the last week or two. Please note this info is based on my own research, conversations with other users both blind and sighted, and may very well be inaccurate in places. Feel free to PR or suggest changes.


## XML has been split up

Back in 2020, you pretty much stuck your XML in either the profile_name.goxlr or in  the goxlr.settings in AppData. It's been split up into several more  files these days, splitting out micProfiles, voice presets and such and storing them in your Documents folder. The default.goxlr file in AppData is essentially your start-off point for new profiles, and while you CAN modify that one you might not want to, to make sure you have sane defaults to falk back on.
On ...the other hand, I don't know how to select another profile to be the default either, so there's also that issue. This is easily done with a bit of sighted assistance if you have it available, though.


## The app is very picky in what it loads on startup

This is by far the most annoying thing to figure out as a blind user, which is why I was nice and went through the sulfuric acid for you folks. :P 

### Setting Voice Presets to the preset buttons

Essentially, you don't appear to have control over these in the XML. If you do, I haven't been able to figure out how, as changing the "name" value in the XML does not appear to change it in the actual profile.
The way to do it is to use OCR to click the Effects tab, then lock down the left mouse button on the preset you want, and release on one of the 6 numbered options in that same screen. NVDA and JAWS both have hotkeys to do this, and this generally works ok. Change takes effect immediately, even if you have the effect button in question active at the time.
It is NOT stored when you close the program, see below.


### Changing individual levels going to the Broadcast Stream Mix and Saving your changes

This burned me recently because of how counter-intuitive it feels, so let's go :)

The GoXLR app will load your routings just fine, as in ...there are toggles in the XML (either 0 or 8192) that instruct it on what audio needs to go where, and those are always loaded when the app starts. So you can just alter these in the XML and reload the app, and they work.
This is not the case, however, for the level attributes in that exact same XML tag, don't ask me why, I have no forking idea.  You can twiddle around with these values until you're old and grey, and NOTHING will happen whatsoever. It's infuriating because of how inconsistent it feels.
What you actually need to do to get the new values to load is manually reload the profile. You do this by double-clicking (single click won't work) a particular spot on the screen. I set this up with someone yesterday and stored it in a Golden Cursor positions file, but as a result I don't know if what we're clicking twice is your profile name, which I suspect is the case, or some random other position on the screen.
You also need to do this each and every time you restart the app, the new values are not stored automatically , the same way voice preset button assignments aren't. You need to explicitly click a save button which according to my research doesn't have a textual label and therefore doesn't show upin OCR. I have stored the position of that button, as well. The golden cursor file is in this repository as of this commit.
