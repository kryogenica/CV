---
permalink: /
title: "Hi! 👋🏼 Please explore my website!"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
<span style="font-size: smaller;">"*In God we trust; all others must bring data.*”<br>-- W. Edwards Deming (American statistician).</span>

<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs"></script>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs-vis"></script>
<script>
  async function loadAndPrepareData() {
    const data = new fashion_mnist.FashionMNIST();
    await data.load();
    const classNames = ['Sneaker', 'Sandal'];
    const trainData = data.nextTrainBatch(60000);
    const testData = data.nextTestBatch(10000);

    const filterData = (data, label) => {
      const indices = data.labels.argMax(-1).equal(tf.scalar(label)).where().squeeze();
      return {
        images: data.images.gather(indices),
        labels: data.labels.gather(indices)
      };
    };

    const sneakers = filterData(trainData, 7);
    const sandals = filterData(trainData, 5);

    return { sneakers, sandals, classNames };
  }

  async function createModel() {
    const model = tf.sequential();
    model.add(tf.layers.flatten({ inputShape: [28, 28, 1] }));
    model.add(tf.layers.dense({ units: 42, activation: 'relu' }));
    model.add(tf.layers.dense({ units: 2, activation: 'softmax' }));
    model.compile({
      optimizer: tf.train.adam(0.001),
      loss: 'categoricalCrossentropy',
      metrics: ['accuracy']
    });
    return model;
  }

  async function trainModel(model, data, label) {
    const xs = data.images.reshape([data.images.shape[0], 28, 28, 1]);
    const ys = tf.oneHot(tf.tensor1d([label], 'int32'), 2);
    await model.fit(xs, ys, { epochs: 1 });
  }

  async function predict(model, data) {
    const xs = data.images.reshape([1, 28, 28, 1]);
    const prediction = model.predict(xs);
    const label = prediction.argMax(-1).dataSync()[0];
    const confidence = prediction.max().dataSync()[0];
    return { label, confidence };
  }

  async function setup() {
    const { sneakers, sandals, classNames } = await loadAndPrepareData();
    const model = await createModel();
    let currentImage, currentLabel;

    function showImage(image) {
      const canvas = document.getElementById('canvas');
      tf.browser.toPixels(image.reshape([28, 28, 1]), canvas);
    }

    function getRandomImage() {
      const isSneaker = Math.random() > 0.5;
      currentImage = isSneaker ? sneakers.images.slice([Math.floor(Math.random() * sneakers.images.shape[0]), 0], [1, 784]) : sandals.images.slice([Math.floor(Math.random() * sandals.images.shape[0]), 0], [1, 784]);
      currentLabel = isSneaker ? 0 : 1;
      showImage(currentImage);
    }

    document.getElementById('sneaker').addEventListener('click', async () => {
      await trainModel(model, { images: currentImage }, 0);
      getRandomImage();
    });

    document.getElementById('sandal').addEventListener('click', async () => {
      await trainModel(model, { images: currentImage }, 1);
      getRandomImage();
    });

    document.getElementById('test').addEventListener('click', async () => {
      const testImage = Math.random() > 0.5 ? sneakers.images.slice([Math.floor(Math.random() * sneakers.images.shape[0]), 0], [1, 784]) : sandals.images.slice([Math.floor(Math.random() * sandals.images.shape[0]), 0], [1, 784]);
      const { label, confidence } = await predict(model, { images: testImage });
      alert(`Prediction: ${classNames[label]}, Confidence: ${(confidence * 100).toFixed(2)}%`);
    });

    getRandomImage();
  }

  setup();
</script>

<canvas id="canvas" width="28" height="28"></canvas>
<button id="sneaker">Sneaker</button>
<button id="sandal">Sandal</button>
<button id="test">Test</button>


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
