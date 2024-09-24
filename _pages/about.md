---
permalink: /
title: "Hi! 👋🏼 Please explore my website!"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
<span style="font-size: smaller;">"*In God we trust; all others must bring data.*”<br>-- W. Edwards Deming (American statistician).</span>

Interactive Machine Learning Demo
======
Explore a simple interactive demo of a machine learning model in action. This demo uses TensorFlow.js to run directly in your browser, allowing you to see how a neural network learns to classify data.

<html>
<head>
  <title>Interactive Fashion MNIST Demo</title>
  <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs"></script>
</head>
<body>
  <h2>Interactive Fashion MNIST Demo</h2>
  <p>Click the buttons below to label the image and train the model, or test the model.</p>
  <img id="image" width="28" height="28">
  <br>
  <button onclick="labelImage('Sneaker')">Sneaker</button>
  <button onclick="labelImage('Boot')">Boot</button>
  <button onclick="testModel()">Test</button>
  <div id="output"></div>

  <script>
    const model = tf.sequential();
    model.add(tf.layers.dense({units: 128, activation: 'relu', inputShape: [784]}));
    model.add(tf.layers.dense({units: 2, activation: 'softmax'}));
    model.compile({loss: 'sparseCategoricalCrossentropy', optimizer: tf.train.adam(0.01)});

    let xs = [];
    let ys = [];

    async function loadFashionMnist() {
      const response = await fetch('https://storage.googleapis.com/tfjs-examples/mnist-data/fashion-mnist_test.json');
      const data = await response.json();
      const images = data.images;
      const labels = data.labels;
      const sneakerImages = [];
      const bootImages = [];
      for (let i = 0; i < labels.length; i++) {
        if (labels[i] === 7) { // Sneaker
          sneakerImages.push(images[i]);
        } else if (labels[i] === 9) { // Ankle Boot
          bootImages.push(images[i]);
        }
      }
      return {sneakerImages, bootImages};
    }

    const {sneakerImages, bootImages} = await loadFashionMnist();

    function getRandomImage() {
      const isSneaker = Math.random() > 0.5;
      const image = isSneaker ? sneakerImages[Math.floor(Math.random() * sneakerImages.length)] : bootImages[Math.floor(Math.random() * bootImages.length)];
      const label = isSneaker ? 0 : 1;
      return {image, label};
    }

    function showImage(image) {
      const canvas = document.createElement('canvas');
      canvas.width = 28;
      canvas.height = 28;
      const ctx = canvas.getContext('2d');
      const imgData = ctx.createImageData(28, 28);
      for (let i = 0; i < image.length; i++) {
        imgData.data[i * 4] = image[i] * 255;
        imgData.data[i * 4 + 1] = image[i] * 255;
        imgData.data[i * 4 + 2] = image[i] * 255;
        imgData.data[i * 4 + 3] = 255;
      }
      ctx.putImageData(imgData, 0, 0);
      document.getElementById('image').src = canvas.toDataURL();
    }

    function labelImage(label) {
      const {image, label: trueLabel} = getRandomImage();
      showImage(image);
      xs.push(image);
      ys.push(label === 'Sneaker' ? 0 : 1);
      if (xs.length >= 10) {
        const xsTensor = tf.tensor2d(xs, [xs.length, 784]);
        const ysTensor = tf.tensor1d(ys, 'int32');
        model.fit(xsTensor, ysTensor, {epochs: 10}).then(() => {
          xs = [];
          ys = [];
        });
      }
    }

    function testModel() {
      const {image, label} = getRandomImage();
      showImage(image);
      const prediction = model.predict(tf.tensor2d([image], [1, 784]));
      const confidence = prediction.dataSync();
      document.getElementById('output').innerText = `Prediction: ${confidence[0] > confidence[1] ? 'Sneaker' : 'Boot'}, Confidence: ${Math.max(...confidence)}`;
    }

    // Initial image display
    const {image} = getRandomImage();
    showImage(image);
  </script>
</body>
</html>


Research Interests
======
* Data science, data analysis, and data reporting.
* NLP, NLU, LLMops, embedding spaces, RAG systems.
* Machine learning, specially graph neural networks.
* Reinforcement learning & integer linear programming optimization.
* Brain, financial, social, & car-traffic networks.
* Infereing network structure from its dynamics 🕸️ &harr; 〰️.

Recent Personal Projects
======
* [**Open-Forecast: A FinTech Tool**](https://open-forecast.streamlit.app/)
  * A fintech web app built with Streamlit, designed to forecast stock prices using machine learning. It analyzes pre-market data to predict price trends.
* [**Contextual Search: A RAG Tool**](https://github.com/kryogenica/Contextual_Search_Tool)
  * A search engine powered by a fine-tuned DistilBERT model that enables contextual searches within movie scripts. This tool uses Python scripts for scene extraction and embedding generation.

Award
======
Secured a prestigious [SBIR Phase I grant](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2309896) from the National Science Foundation along with my PhD Advisor for pioneering an artificial intelligence system to enhance transparency and predict trends in democratic elections.

Work experience
======
* **Machine Learning Engineer - Contract** (June 2024 - August 2024)
  * Developed an industry-first dataset by leveraging AWS and Azure large language models (LLMs) to generate and augment data from movie scripts, enabling content extraction and analysis. Employed prompt engineering to minimize paraphrasing and ensure structured output in the desired JSON format. This dataset was subsequently used to fine-tune a custom Named-Entity Recognition (NER) transformer model, driving accuracy in entity recognition and establishing a new standard for movie script data processing.
 
* **CUNY Graduate Center, Computational Research Assistant** (Sept 2019 - August 2024)
  * Project: Bridging the gap between physics, network theory and neuro-science:
    * Collaborated with a multidisciplinary and international team to guide their sourcing of neural activity signals and preprocessing, resulting in an ETL pipeline that provided a prime dataset for high-quality research.
    * Applied advanced concepts of graph theory to study the complex network of a worm's brain, leading to the identification of key structures responsible for synchronization and writing one of the first papers on how a particular type of network symmetry may exist in the brain's structure. Calculations were done using NetworkX and Pandas.
  * Project: A/B testing of optimal network repairing algorithms with statistical support:
    * Applied numerous statistical measurement techniques to the dataset collected above to capture relational information. Transformed each into a uniquely developed data structure and implemented various community detection algorithms on each, producing a plethora of options to be tested. Filtered results via p-value permutation tests and reproducibility of results to test the robustness of the pipeline... [**(more in CV)**](/files/Bryant_Avila_CV.pdf)

* **Kcore Analytics, Data Analyst** (Nov 2023 – April 2024)
  * Played a key role in a team that successfully designed and implemented an ETL pipeline to track and analyze electoral campaign performance in real-time, enabling data-driven decisions and improving outcome predictions. Leveraged U.S. Census Bureau data, extracted via APIs, to retrieve demographic information at multiple geographic levels. Preprocessed and aggregated this data using Spark and SQL for efficient storage, before performing geospatial analysis with GeoPandas. Integrated the processed data into convolutional graph neural networks, trained with PyTorch, to predict voting outcomes and monitor campaign performance.

* **Fashion Institute of Technology, Lab Manager** (Feb 2018 – Feb 2024)
  * Administered a yearly budget of over $100K, ensuring efficient allocation towards upgrades, chemical and equipment purchasing, and training initiatives. Successfully captured internal funds to spearhead the integration of 3D printing technology in the classroom, enhancing the practical learning experience for students. Led and managed team of staff members.
  * Collaborated with faculty in pioneering the development of sustainable materials, including bacterial leather, alginate & mushroom fabrics, and mycelium wood. Conducted detailed characterization of biological samples using Scanning Electron Microscope (SEM), and diligently reported findings relevant for further advancement... [**(more experiences in my CV)**](/files/Bryant_Avila_CV.pdf)

Education
======
* PhD in Physics - Graduate Center of the City University of New York - Writting Thesis
  * Advisors: [Hernan Makse](https://hmakse.ccny.cuny.edu/), [Manuel Zimmer](https://www.imp.ac.at/groups/manuel-zimmer)
* M.S. in Physics - Graduate Center of the City University of New York - Feb 2023
  * Advisors: [Hernan Makse](https://hmakse.ccny.cuny.edu/), [David Phillips](https://www.usna.edu/Users/math/dphillip/)
* B.S. in Physics - City College of New York - Feb 2016
  * Cum Laude and Research honors
  * Advisors: [Carlos Meriles](https://cmeriles.ccny.cuny.edu/), [Brain Tiburzi](https://www.gc.cuny.edu/people/brian-c-tiburzi)

Skills
======
* Coding
  * NLP, LLM, ML, AI, Python (NumPy, SciPy, Pandas, SKlearn, Matplotlib, TensorFlow, PyTorch, Geopandas, NetworkX, Selenium, GUROBI), C++, huggingface, R, C shell, Fortran, Matlab, SQL, LateX, Labview, Relion, Fusion 360, Solidworks, GitHub, ArcGIS, AutoCAD, WordPress and Salesforce.
* Soft skills
  * Team management, market research, leads into clients, tutoring / teaching, collaborations, public speaking, project managment,problem-solving, attention to detail, quick learner.

Publications
======
* Khayat R, Avila B, et al. [“Porcine circovirus 2 uses a multitude of weak binding sites to interact with heparan sulfate, and the interactions do not follow the symmetry of the capsin.”](https://jvi.asm.org/content/93/6/e02222-18)  Journal of Virology. 2019.
* Khayat R, Avila B, et al. [“Cryo-electron microscopy structure of the 70S ribosome from Enterococcus faecalis.”](https://www.nature.com/articles/s41598-020-73199-6) Nature. 2020.
* Avila B, et al. [“Fibration symmetries and cluster synchronization in the Caenorhabditis elegans connectome.”](https://arxiv.org/abs/2305.19367) Plos One 2024.
* Tommasone M, Avila B, et al. [“Scale-up of Dry Impregnation Processes for Porous Spherical Catalyst Particles in a Rotating Drum:
Experiments and Simulations.”](https://arxiv.org/abs/2307.14444) preprint arXiv:2307:1444, Granular Matter (submitted August 2023).
* Tommaso Gili, et al. [“Fibration symmetry-breaking supports functional transitions in a brain network engaged in language.”](https://www.researchsquare.com/article/rs-4409330/v1) (Submitted to Nature on June 2024).
* Avila B, et al. [“Symmetries and synchronization from whole-neural activity in C. elegans connectome: Integration of functional and structural networks.”](https://arxiv.org/abs/2409.02682) (Submitted to Plos One on August 2024).
