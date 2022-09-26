# !!!!
# DANGER: The final public version is currently updated - end of the day of Monday 26th.
# !!!!

# DRAFT FOLLOWS:

# Ao: An eye tracking platform for babies

<!-- TABLE OF CONTENTS -->
<h2 id="table-of-contents"> :book: Table of Contents</h2>

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project"> ➤ About The Project</a></li>
    <li><a href="#prerequisites"> ➤ Prerequisites</a></li>
    <li><a href="#folder-structure"> ➤ Folder Structure</a></li>
    <li><a href="#dataset"> ➤ Dataset</a></li>
    <li><a href="#roadmap"> ➤ Roadmap</a></li>
    <li>
      <a href="#preprocessing"> ➤ Preprocessing</a>
      <ul>
        <li><a href="#preprocessed-data">Pre-processed data</a></li>
        <li><a href="#statistical-feature">Statistical feature</a></li>
        <li><a href="#topological-feature">Topological feature</a></li>
      </ul>
    </li>
    <!--<li><a href="#experiments">Experiments</a></li>-->
    <li><a href="#results-and-discussion"> ➤ Results and Discussion</a></li>
    <li><a href="#future"> ➤ Future</a></li>
    <li><a href="#acknowledgments"> ➤ Acknowledgments</a></li>
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
    │   │   ├── wip.py
    │   │   ├── input.py
    
    ETC

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
## API

<!-- FUTURE -->
<h2 id="future"> Future Goals </h2>

Alas, the end of Summer of Code shouldn't be the end of this project! With an amazing scope to go forward, I would love to put much more effort and create a full-working application that could be used in a clinical setting with help and testing from other researchers and labs we already had contact with. As an example researchers from Birkbeck, University of London and King's College London 

<!-- Acknowledgments -->
<h2 id="acknowledgments"> Acknowledgments! </h2>

First of all my supervisor Suresh (Dr Krishna) from McGill University for the amazing insight and information! Sometimes this information was a lot for me to grasp and make out where we are heading but I know that this is invaluable for the future versions of the app and collaborative efforts with other researchers.

I also want to thank Dr Harris from King's College London for giving my access to Tobii data to test out the API and the basic functionality of the unit interface and comparison between a WebCam on my device and a state-of-the-art eye tracker. I also want to thank Dr T Smith form Birkbeck for his insight on the training of baby eye trackers and his previous experience on it, as well as his willingness to help test-out our code.

Last but not least I would also like to thank Dr Arvind Chandna for providing the ophthalmological medicine background and insights on our preliminary and later discussions! 

I hope that with Google's open source support, I was able to create a seed via a useful API and code suggestions which can result in a project which can be useful for the future in the clinical setting! Thanks Google! 

## License

The project is by definition of Google Summer of Code and Open Source software project and it's licensed under the GNU GPL v3+
