# resume_analyzer
AI-powered Resume Analyzer using RAG, LLM and GenAI — upload your resume and job description to get match percentage, missing skills and suggestions.

# AI Resume Analyzer

## Why I built this

After my interview at a company, I got feedback 
that my projects don't have real AI experience 
like LLMs, RAG, or GenAI.

Instead of feeling bad about it, I went home 
and started building.

This is my second project where I actually used 
RAG, LLM, and GenAI together in one place.

---

## What does it actually do

You give it two things:
- Your resume (PDF)
- A job description (text)

And it tells you:
- How much your resume matches the job (in %)
- What skills you already have
- What skills you are missing
- What you should improve

Simple as that.

---

## How it works behind the scenes

When I first built this, I had no idea how 
to compare a resume with a job description 
using AI. So I broke it down step by step.

**Step 1 — Read the resume**
I used PyPDF to read the PDF and extract 
all the text from it.

**Step 2 — Break it into small pieces**
The whole resume at once is too big for an 
AI model to process properly. So I broke it 
into small chunks of 500 characters each.
This is called chunking.

**Step 3 — Convert text to numbers**
AI does not understand words directly. 
It understands numbers. So I used 
HuggingFace embeddings to convert each 
chunk into a list of numbers.
These numbers capture the meaning of the text.

**Step 4 — Store in FAISS**
FAISS is like a smart library. It stores 
all those numbers and can quickly find 
which chunks are most relevant to any 
given question or job description.
This is the Retrieval part of RAG.

**Step 5 — Connect the AI model**
I used Groq's LLaMA 3.3 model which is 
free and very fast. This is the actual 
AI that reads the resume and job description 
and gives the analysis.

**Step 6 — Get the analysis**
When you give a job description, FAISS 
finds the most relevant parts of your resume.
Those parts + job description are sent to 
LLaMA together.
LLaMA then gives you match %, missing skills,
strong skills and suggestions.
This full flow is called RAG — 
Retrieval Augmented Generation.

---

## Tech I used

- Python
- LangChain — to connect everything together
- FAISS — to store and search resume chunks
- HuggingFace — to convert text into numbers
- Groq LLaMA 3.3 — the actual AI brain
- PyPDF — to read PDF files

---

## Challenges I actually faced

### Version conflicts in LangChain
LangChain updates very frequently. 
Many modules I used first were moved 
or removed in newer versions.
I spent a lot of time uninstalling and 
reinstalling to find versions that 
actually work together.

### Getting the right chunks
At first the AI was giving wrong analysis 
because it was picking irrelevant chunks 
from the resume.
I fixed the chunk size and overlap to make 
sure the right content gets retrieved.

### Prompt Engineering
Just asking the AI to "analyze the resume" 
was not enough. I had to carefully write 
the prompt — telling it to act as an HR 
expert and give structured output.
This made a huge difference in the quality 
of the output.

### API Key Security
I accidentally exposed my API key once 
while uploading to GitHub.
GitHub detected it immediately and warned me.
I deleted the key, created a new one, 
and learned to never put real keys in code.

---

## What I learned from this project

Honestly, two weeks ago I did not know 
what RAG was.

I got rejected from a job because my 
projects did not have LLM or GenAI experience.

I built this in 2 days after that rejection.

Now I understand:
- How RAG actually works in real life
- How to connect an LLM to your own data
- How prompt engineering changes everything
- Why API key security matters
- How FAISS searches through vectors

Building this taught me more than 
any tutorial could.

---

## Setup

pip install langchain-groq langchain-community 
faiss-cpu pypdf sentence-transformers

Add your Groq API key where mentioned 
and run all cells in order.

---

## Connect with me

LinkedIn: linkedin.com/in/vikas-mali-4a467a286
GitHub: github.com/Vikas15102003
Email: vikasbharatmali18@gmail.com
