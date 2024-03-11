---
permalink: /
title: "Hi! 👋🏼 Please explore my website!"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<span style="font-size: smaller;">"*In God we trust; all others must bring data.*”<br>-- W. Edwards Deming (American statistician).</span>

Research Interests
======
* Data science, data analysis, and data reporting.
* Machine learning, specially graph neural networks.
* Reinforcement learning & integer linear programming optimization.
* Brain, financial, social, & car-traffic networks.
* Simulating complex systems / physics through equations.
* Infereing network structure from its dynamics 🕸️ &harr; 〰️.

Education
======
* PhD in Physics - Graduate Center of the City University of New York - Summer 2024
  * Advisors: [Hernan Makse](https://hmakse.ccny.cuny.edu/), [Manuel Zimmer](https://www.imp.ac.at/groups/manuel-zimmer)
* MPhil in Physics - Graduate Center of the City University of New York - Feb 2023
  * Advisors: [Hernan Makse](https://hmakse.ccny.cuny.edu/), [Manuel Zimmer](https://www.imp.ac.at/groups/manuel-zimmer)  
* B.S. in Physics - City College of New York - Feb 2016
  * Cum Laude and Research honors
  * Advisors: [Carlos Meriles](https://cmeriles.ccny.cuny.edu/), [Brain Tiburzi](https://www.gc.cuny.edu/people/brian-c-tiburzi)  

Work experience
------
* Graduate Center of CUNY, PhD in Physics (Sept 2019 - Summer 2024)
  * **Project: Bridging the gap between physics, network theory and neuro-science:**
    * Collaborated with a multidisciplinary and international team to guide their sourcing of neural activity signals by analyzing their data resulting in a pipeline leading to a prime dataset providing the basis for high quality research.
    * Applied advanced concepts of graph theory to study the complex network of a worm's brain, leading to the identification of key structures responsible for synchronization and writing one of the first papers on how a particular type of network symmetry may lurk in the brain's structure. Calculations done via NetworkX and Pandas.
    * Developed an open-source GUI Matlab software toolkit for analyzing and visualizing time series neural dynamics through which the previous hypotheses were further supported.
  * **Project: A/B testing of optimal network repairing algorithms with statistical support:**
    * Applied dozens of statistical measuring techniques on the dataset collected above to capture relational information, transformed each into a unique developed data structure, implemented various community detection algorithms on each, producing a plethora of options to be tested... **(more in CV)**

* Kcore Analytics, Data Analyst (Nov 2023 – April 2024)
  * Built new calls not offered in the US census bureau python library via their API to retrieve demographic data on multiple resolution levels, stored data into custom SQL tables prior to GeoPandas calculations. Created a Selenium based web crawler tailored towards specific websites for data extraction.
  * Implemented pre-trained transformers to do sentiment analysis on retrieved tweets, incorporating results with aforementioned population data to infer election outcomes via the training of multiple convolutional graph neural network models via PyTorch.

* Fashion Institute of Technology, Principal Lab Technician (Feb 2018 – Feb 2024)
  * Administered a yearly budget of over $100K, ensuring efficient allocation towards upgrades, chemical and equipment purchasing, and training initiatives. Successfully captured internal funds to spearhead the integration of 3D printing technology in the classroom, enhancing the practical learning experience for students. Led and managed teqam of staff members.
  * Collaborated with faculty in pioneering the development of sustainable materials, including bacterial leather, alginate & mushroom fabrics, and mycelium wood. Conducted detailed characterization of biological samples using Scanning Electron Microscope (SEM), and diligently reported findings relevant for further advancement... **(more in CV)**



The main configuration file for the site is in the base directory in [_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml), which defines the content in the sidebars and other site-wide features. You will need to replace the default variables with ones about yourself and your site's github repository. The configuration file for the top menu is in [_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml). For example, if you don't have a portfolio or blog posts, you can remove those items from that navigation.yml file to remove them from the header. 

Create content & metadata
------
For site content, there is one markdown file for each type of content, which are stored in directories like _publications, _talks, _posts, _teaching, or _pages. For example, each talk is a markdown file in the [_talks directory](https://github.com/academicpages/academicpages.github.io/tree/master/_talks). At the top of each markdown file is structured data in YAML about the talk, which the theme will parse to do lots of cool stuff. The same structured data about a talk is used to generate the list of talks on the [Talks page](https://academicpages.github.io/talks), each [individual page](https://academicpages.github.io/talks/2012-03-01-talk-1) for specific talks, the talks section for the [CV page](https://academicpages.github.io/cv), and the [map of places you've given a talk](https://academicpages.github.io/talkmap.html) (if you run this [python file](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py) or [Jupyter notebook](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb), which creates the HTML for the map based on the contents of the _talks directory).

**Markdown generator**


How to edit your site's GitHub repository
------
Many people use a git client to create files on their local computer and then push them to GitHub's servers. If you are not familiar with git, you can directly edit these configuration and markdown files directly in the github.com interface. Navigate to a file (like [this one](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md) and click the pencil icon in the top right of the content preview (to the right of the "Raw | Blame | History" buttons). You can delete a file by clicking the trashcan icon to the right of the pencil icon. You can also create new files or upload files by navigating to a directory and clicking the "Create new file" or "Upload files" buttons. 

Example: editing a markdown file for a talk
![Editing a markdown file for a talk](/images/editing-talk.png)

For more info
------
More info about configuring academicpages can be found in [the guide](https://academicpages.github.io/markdown/). The [guides for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) (which this theme was forked from) might also be helpful.
