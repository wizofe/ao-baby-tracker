# Ao: An eye tracking platform for babies

<!-- TABLE OF CONTENTS -->
<h2 id="table-of-contents"> :book: Table of Contents</h2>

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project"> ➤ About The Project</a></li>
    <li><a href="#prerequisites"> ➤ Prerequisites</a></li>
    <li><a href="#roadmap"> ➤ Roadmap</a></li>
    <li><a href="#folder-structure"> ➤ Folder Structure</a></li>
    <li><a href="#api"> ➤ API</a></li>
    <li><a href="#implementation"> ➤ Implementation</a></li>
    <li><a href="#psychometrics"> ➤ Psychometrics</a></li>
    <li><a href="#future"> ➤ Future Goals</a></li>
    <li><a href="#acknowledgments"> ➤ Acknowledgments</a></li>
    <li><a href="#license"> ➤ License</a></li
  </ol>
</details>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<h2 id="about-the-project"> :pencil: About The project</h2>

This project is the work for the Google Summer of Code 2022, with the organisation INCF: Eye tracking project for neonates. The project is created by [Ioannis Valasakis](@wizofe) under the mentoring of Arvind Chandna, MD DO FRCS FRCophth and Suresh Krishna, PhD from McGill University.

Ao is the personification of light in Māori mythology and it sounds like a suitable name for the project.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
<!-- PREREQUISITES -->
<h2 id="prerequisites"> Prerequisites</h2>

[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/) <br>
[![Made withJupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)](https://jupyter.org/try) <br>

<!--This project is written in Python programming language. <br>-->
The following open source packages are used in this project:
* Numpy
* Pandas
* Matplotlib
* Scikit-Learn
* TensorFlow
* Keras
* PsychoPy
* LibWebCam

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- ROADMAP -->
<h2 id="roadmap"> :dart: Roadmap</h2>

The result of this work which was about 420 hours, is divided in the following parts:

1. Research and development of an input device for eye tracking. We considered the following devices: WebCam, Tablet WebCam (iPad but also Android was considered from other members in the project) and Tobii devices. As the time wasn't enough to properly get a loan, I could only get data from a lab in King's College London, in order to test (not available publicly).

2. MAIN PART of the work - Coding an API: Create the API which accepts the streaming input of any device (webcam, Tobii positional eye tracker, etc) and create a unified framework API, able to be the glue of the project for any further experiments.

3. Create sample PsychoPy builder files; extended from previous work but also modular in order to be used for the project 

4. Create a prototype using `libwebcam` to feed the stream of the input device (web camera) to IoHUB (part of the module `psychopy.iohub`

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- :paw_prints:-->
<!-- FOLDER STRUCTURE -->
<h2 id="folder-structure"> :cactus: Folder Structure</h2>

    code
    .
    │
    ├── 
    │   ├── api
    │   │   ├── imports.py
    │   │   ├── openvisionapi.py
    |   |   ├── __pycache__
    ├── docs
    |   ├── openvisionapi.html
    |   ├── index.html
    |   ├── search.js

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
## API

Please [CLICK HERE](https://external.ink/?to=https://htmlpreview.github.io/?https://raw.githubusercontent.com/wizofe/ao-baby-tracker/master/docs/openvisionapi.html) for the API documentation. Important: the main documentation is inside the folder as an HTML file. GitHub doesn't render HTMLs, so this preview is using an external website.

In case this doesn't work, please download the repository locally and view with the web browser of your choice.

Extra fun fact: If you click on "source" in the documentation, it takes you directly to the function and shows you the respective API code.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
<!-- IMPLEMENTATION -->
<h2 id="psychometrics"> Psychometrics</h2>

This is an indication 
![Psychometrics](/images/psychometrics.png)

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
<!-- :paw_prints:-->
<!-- IMPLEMENTATION -->
<h2 id="implementation"> Implementation</h2>

Finally, here's an example of how to use the library with psychopy (of course you need to install the respective anaconda/miniconda environment with all the required files):

```
# Display properties
DISPSIZE = (1920, 1080)
DISPTYPE = 'psychopy'
 
# Eye tracker properties
TRACKERTYPE = 'OpenVision'

# Create new imports and initialise the screen

from pygaze.display import Display
from pygaze.screen import Screen
from pygaze.eyetracker import EyeTracker
import pygaze.libtime as timer
 
disp = Display()
scr = Screen()
 
# Show a waiting message.
scr.draw_text("Preparing experiment...", fontsize=20)
disp.fill(scr)
disp.show()
 
# Open a connection to the eye tracker and calibrate
tracker = EyeTracker(disp)
tracker.calibrate()
 
# Start streaming and logging samples.
tracker.start_recording()
 
# Run for 4 seconds displaying a dot on the current gaze position
t0 = timer.get_time()
while timer.get_time() - t0 < 4000:
	# Get the latest gaze sample.
	gazepos = tracker.sample()
	# Clear the current contents of the Screen.
	scr.clear()
	# Draw a dot on the Screen, at the current gaze position.
	scr.draw_fixation(fixtype='dot', pos=gazepos)
	# Show the Screen.
	disp.fill(scr)
	disp.show()
 
# Stop streaming and logging samples.
tracker.stop_recording()
# Close the connection to the tracker.
tracker.close()
 
# Close the display.
disp.close()
```

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- FUTURE -->
<h2 id="future"> Future Goals </h2>

Alas, the end of Summer of Code shouldn't be the end of this project! With an amazing scope to go forward, I would love to put much more effort and create a full-working application that could be used in a clinical setting with help and testing from other researchers and labs we already had contact with. As an example researchers from Birkbeck, University of London and King's College London provided insight, data and offered future help to test a complete eye tracker with developmental populations.

Here's some future roadmap suggestions, starting from low-hanging fruit to more universal features:

- Create custom xxx-conda environments with yaml configuration files depending on the configuration (e.g. development, testing, release)
- Integrate with psychopy, builder output using the eye position from the API output
- Create grading acuity 
- Create a modular input system for psyexp files (the standalone)
- Test first with laptops before deciding a mobile platform

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- Acknowledgments -->
<h2 id="acknowledgments"> Acknowledgments! </h2>

First of all my supervisor Suresh (Dr Krishna) from McGill University for the amazing insight and information! Sometimes this information was a lot for me to grasp and make out where we are heading but I know that this is invaluable for the future versions of the app and collaborative efforts with other researchers.

I also want to thank Dr Harris from King's College London for giving my access to Tobii data to test out the API and the basic functionality of the unit interface and comparison between a WebCam on my device and a state-of-the-art eye tracker. I also want to thank Dr T Smith form Birkbeck for his insight on the training of baby eye trackers and his previous experience on it, as well as his willingness to help test-out our code.

Last but not least I would also like to thank Dr Arvind Chandna for providing the ophthalmological medicine background and insights on our preliminary and later discussions! 

I hope that with Google's open source support, I was able to create a seed via a useful API and code suggestions which can result in a project which can be useful for the future in the clinical setting! Thanks Google! 

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
<h2 id="license"> License</h2>

The project is by definition of Google Summer of Code and Open Source software project and it's licensed under the GNU GPL v3+
