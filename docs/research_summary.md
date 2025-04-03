

 # SECTRAIN – Detailed Research Summary 
 
 This document provides an in-depth explanation of the decisions made during Steps 1 to 3 of Phase 2 for the SECTRAIN chatbot project. Each component was selected based on technical fit, ease of integration, local inference capability, and educational objectives.
 
 ---
 
 ## 1. Language Model Selection
 
 ### ✅ **Chosen Model: SecureFalcon**
 
 **SecureFalcon** is a domain-specific language model fine-tuned on cybersecurity data, including secure code practices, vulnerability analysis, and security-focused documentation. It was selected after evaluating several open-source alternatives.
 
 ### 🔍 Alternatives Considered
 - **Mistral-7B**: A powerful general-purpose model with excellent reasoning capabilities.
 - **WhiteRabbitNeo**: A lightweight model with fast inference speed but limited domain depth.
 
 ### 🔗 Why SecureFalcon?
 - **Domain Relevance**: Fine-tuned on cybersecurity-specific data, which aligns directly with SECTRAIN’s use cases (e.g., secure code analysis, OWASP concepts).
 - **Inference Feasibility**: Available in GGUF format for `llama.cpp`, allowing efficient local CPU-only inference without GPU dependency.
 - **License**: Open-source and safe for academic or educational use.
 - **Performance**: While not as generalized as Mistral, it provides more targeted and context-aware responses in the field of secure programming.
 
 SecureFalcon reduces hallucinations for cybersecurity queries and supports high-fidelity explanations in an educational context.
 
 ---
 
 ## 2. Vector Database Selection
 
 ### ✅ **Chosen Vector Store: ChromaDB**
 
 **ChromaDB** is a lightweight, open-source vector database designed for local-first operations. It integrates natively with both LangChain and LlamaIndex and is optimized for use cases like document-based question answering.
 
 ### 🔍 Alternatives Considered
 - **FAISS**: High-speed and robust, but lacks built-in metadata support and requires additional logic for persistence.
 - **Weaviate**: Powerful but heavier and overkill for small, local applications.
 
 ### 🔗 Why ChromaDB?
 - **Ease of Use**: Simple installation (`pip install chromadb`) and minimal configuration.
 - **Local Persistence**: Built-in local storage capabilities, suitable for offline RAG workflows.
 - **Metadata Support**: Allows indexing and filtering by custom fields (e.g., topic, source, difficulty).
 - **Compatibility**: Seamless integration with LlamaIndex, enabling rapid prototyping.
 
 ChromaDB is well-suited for educational applications that require quick deployment, flexible document filtering, and reliable CPU-based operations.
 
 ---
 
 ## 3. RAG Framework Selection
 
 ### ✅ **Chosen Framework: LlamaIndex**
 
 **LlamaIndex** is a lightweight RAG (Retrieval-Augmented Generation) framework that simplifies the process of loading, indexing, and querying document-based data with LLMs.
 
 ### 🔍 Alternatives Considered
 - **LangChain**: Feature-rich and modular but has a steeper learning curve and more boilerplate code.
 
 ### 🔗 Why LlamaIndex?
 - **Simplicity**: Easier to use and well-documented, with out-of-the-box support for most common use cases.
 - **Document Handling**: Offers better built-in document loaders for Markdown, PDF, and HTML (relevant for lecture slides and scraped OWASP content).
 - **ChatEngine Support**: Supports both stateless and memory-based chat engines; ideal since SECTRAIN opts for stateless design.
 - **Local-Friendly**: Works smoothly with Chroma and does not require cloud APIs or advanced multi-agent setups.
 - **Evaluation Utilities**: Useful built-in tools for testing and benchmarking chatbot accuracy.
 
 LlamaIndex ensures fast development, clean abstractions, and robust performance for a focused educational tutor like SECTRAIN.
 
 ---
 
 ## 📌 Summary of Stack Decisions
 
 | Component         | Selection       | Rationale                                                  |
 |------------------|-----------------|------------------------------------------------------------|
 | Language Model   | SecureFalcon    | Domain-tuned, locally runnable, good at secure code tasks  |
 | Vector Database  | ChromaDB        | Lightweight, easy setup, supports metadata and persistence |
 | RAG Framework    | LlamaIndex      | Educational focus, easy to use, great for stateless RAG    |
 
 Each component has been carefully selected to balance performance, usability, and alignment with SECTRAIN’s goals: local operation, educational quality, and cybersecurity expertise.