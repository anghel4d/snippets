/loop We're going over this codebase like a multi-stage water filter, sifting through over and over again until it is squeaky clean.

For every iteration, you are to spawn a Fable agent. Its job will be to go through each module one by one, and find ONE bug. It will tally it to the new docs/BUGS.md file, divided by section category and added to the appropriate section.

Try to spawn only one agent per bug, and do them sequentially.
A special case for the # Interlink / Composition bugs: treat every module-module intersection as its own module; eg: if you currently spawn one agent per includes/ entry and its associated src/ implementation, you should also imagine and treat every module-module intersection as its own "imaginary module" to check as well. A graph-theoretical approach.

If a bug is not found, add a test that might flush a *plausible* one out. If a bug IS found and tallied, add a test that would trigger it and cause the CTest suite to record a failure. If a hypothetical bug is found but not reliably surfaced in a Test, add it to the tally anyways but mark its testing / smoking out as tentative.

Keep going until BUGS.md has a good tally overall.

The REASON we are not merely fixing bugs *one at a time*: When you aggregate and collect as many of them as possible into one bug census, it becomes possible to analyze the data and make sweeping corrections upstream of them. That's the idea here.