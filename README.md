# LangChain ile Yapay Zeka Yanıtını Yönetmek

> LangChain mesaj yapısını kullanarak Groq üzerinde Llama 3.1 modeline prompt gönderme ve cevap alma — RAG serisinin 1. adımı

[![Colab'da Aç](https://img.shields.io/badge/Colab'da%20Aç-F9AB00?style=flat-square&logo=googlecolab&logoColor=white)](https://colab.research.google.com/github/yasir237/rag-langchain-1/blob/main/rag_langchain_1.ipynb)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yasir-alrawi-12814521a/)

---

## Problem

Bir LLM modeline düz metin göndermek yeterli değil. Modelin kim olduğunu, ne yapması gerektiğini ve kullanıcının ne sorduğunu **ayrı ayrı tanımlamak** gerekiyor.

## Çözüm

LangChain'in mesaj yapısı bu sorunu çözüyor. Üç mesaj tipiyle modele net bir bağlam veriyorsun — bu yapı, RAG sistemlerinin, agent'ların ve çok turlu sohbetlerin temelidir.

---

## Mesaj Mimarisi

```
Kullanıcı sorusu
      │
      ▼
┌─────────────────────────────────┐
│         LangChain Zinciri       │
│                                 │
│  SystemMessage  →  Kim olduğu   │
│  HumanMessage   →  Ne sorduğu   │
│  AIMessage      →  Cevap + geçmiş│
└─────────────────────────────────┘
      │
      ▼
  Groq API (Llama 3.1 8B)
      │
      ▼
   Cevap
```

| Mesaj Tipi | Görevi |
|---|---|
| `SystemMessage` | Modele kim olduğunu ve nasıl davranacağını söyler |
| `HumanMessage` | Kullanıcının sorusunu taşır |
| `AIMessage` | Modelin ürettiği cevabı temsil eder — chat geçmişi bununla kurulur |

---

## Kullanılan Teknolojiler

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat&logoColor=white)
![Llama](https://img.shields.io/badge/Llama_3.1_8B-0467DF?style=flat&logo=meta&logoColor=white)
![Python](https://img.shields.io/badge/Python_3-3776AB?style=flat&logo=python&logoColor=white)
![Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)

---

## Kurulum

```bash
pip install langchain langchain-core
pip install langchain-groq
```

### API Anahtarı

Google Colab **Secrets** sekmesine `GROQ_API_KEY` ekle.

Groq API anahtarı almak için → [console.groq.com](https://console.groq.com)

---

## Kullanım

```python
from langchain_core.messages import HumanMessage, SystemMessage
from langchain_groq import ChatGroq

chat = ChatGroq(model="llama-3.1-8b-instant", temperature=0)

messages = [
    SystemMessage(content="You are an expert data scientist"),
    HumanMessage(content="Write a Python script that trains a neural network")
]

response = chat.invoke(messages)
print(response.content)
```

---

## Seri İçindeki Yeri

Bu notebook, LangChain ile kurulan RAG serisinin **1. adımıdır.**

```
[1] ✅ Mesaj yapısı ve LLM bağlantısı   ← bu repo
[2]    PromptTemplate ile şablonlu prompt 
[3]    Çoklu zincir kurma ve zincirleri bağlama
[4]    Metin bölme ve embedding
[5]    Vektör store ve benzerlik araması
```

Her adım bir sonrakine köprü kuruyor.
Serinin tamamını takip etmek için LinkedIn profilimi ziyaret edebilirsin 👇

---

## Bağlantı

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yasir-alrawi-12814521a/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yasir237)

---

## Lisans

MIT
