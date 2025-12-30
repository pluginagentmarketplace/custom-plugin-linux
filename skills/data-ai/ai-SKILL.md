---
name: ai
description: AI/LLM skill - Prompt engineering, RAG, fine-tuning, LangChain
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [prompt, rag, finetune, agent, evaluate] }
    model: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    solution: { type: string }
    code: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# AI/LLM Skill

## PURPOSE
LLM applications, prompt engineering, and AI system design.

## CORE COMPETENCIES
```
Prompt Engineering:
├── Zero-shot, few-shot
├── Chain-of-thought
├── System prompts
└── Output formatting

RAG (Retrieval-Augmented Generation):
├── Document chunking
├── Embedding models
├── Vector databases
├── Retrieval strategies
└── Context window management

LLM Frameworks:
├── LangChain
├── LlamaIndex
├── Anthropic SDK
└── OpenAI API
```

## CODE PATTERNS

### RAG Pipeline
```python
from langchain.embeddings import OpenAIEmbeddings
from langchain.vectorstores import Pinecone
from langchain.chains import RetrievalQA
from langchain.chat_models import ChatOpenAI

# Initialize
embeddings = OpenAIEmbeddings()
vectorstore = Pinecone.from_existing_index("docs", embeddings)
llm = ChatOpenAI(model="gpt-4", temperature=0)

# RAG chain
qa_chain = RetrievalQA.from_chain_type(
    llm=llm,
    retriever=vectorstore.as_retriever(
        search_kwargs={"k": 5}
    ),
    return_source_documents=True
)

result = qa_chain({"query": "How does X work?"})
```

### Retry with Backoff
```python
from tenacity import retry, stop_after_attempt, wait_exponential

@retry(
    stop=stop_after_attempt(3),
    wait=wait_exponential(multiplier=1, min=1, max=10)
)
def call_llm(prompt: str) -> str:
    return client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    ).choices[0].message.content
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Hallucinations | No grounding | Use RAG, add sources |
| Rate limited | Too many requests | Implement backoff |
| Context overflow | Too long | Chunking, summarization |
| Poor retrieval | Bad embeddings | Tune chunk size, model |

## BEST PRACTICES
```
1. Use structured outputs (JSON mode)
2. Implement proper error handling
3. Add observability (LangSmith, Arize)
4. Cache responses when possible
5. Use streaming for long responses
6. Evaluate with diverse test sets
```
