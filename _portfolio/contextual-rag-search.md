---
title: "Contextual Search: A RAG Tool"
excerpt: "Vaguely recall a piece of text from a file, simply describe it and find it! <br/><img src='/images/Scene_contextual_search.png' width='50%'>"
collection: portfolio
---

Ever found yourself vaguely recalling a piece of text from a document but struggling to find it through traditional keyword searches? Imagine a tool where you can describe what you remember (a brief description, summary, or paraphrase) and instantly retrieve the most relevant pieces of text. That's exactly what my new project, the 𝗖𝗼𝗻𝘁𝗲𝘅𝘁𝘂𝗮𝗹 𝗦𝗲𝗮𝗿𝗰𝗵 𝗧𝗼𝗼𝗹, does, and it's now available on my GitHub!

🧠 𝗛𝗼𝘄 𝗗𝗼𝗲𝘀 𝗜𝘁 𝗪𝗼𝗿𝗸?
This tool harnesses the power of transformer models to perform contextual searches across any body of text. It breaks down the text into meaningful chunks, focusing on the most relevant aspects. Using a transformer model, these chunks and your description are converted into numerical representations (embeddings). The tool then uses cosine similarity to measure how alike these pieces of text are, even if they don’t share exact words, and filters out the chunks that best match your query.

🤖 𝗦𝗲𝗲 𝗜𝘁 𝗶𝗻 𝗔𝗰𝘁𝗶𝗼𝗻
In my demo, I applied the tool to a movie script, allowing users to search for matching dialogue and scene descriptions based on a simple query. Check out this [Jupyter notebook](https://github.com/kryogenica/Contextual_Search_Tool/blob/main/examples/Contextual_Search_Tool.ipynb)  to see how effortlessly it can find a scene description just from a summary!

This tool, and others like it, can be tuned and adapted to search through large volumes of data in fields such as media, law, literature, and beyond. Let’s connect if you're interested in AI, ML, or NLP opportunities; or if you just want to chat about the possibilities! 🤝


[Repository](https://github.com/kryogenica/Contextual_Search_Tool/tree/main).

\#AI \#NLP \#Transformers \#ContextualSearch \#HuggingFace \#DataScience \#Embedding \#ML \#RAG

