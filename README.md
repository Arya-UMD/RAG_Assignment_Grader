## **RAG-Based PCA Assignment Grading System**

### **Overview**  
This project implements an **AI-powered Retrieval-Augmented Generation (RAG)** system designed to **automatically grade assignments** related to **Principal Component Analysis (PCA)**. By leveraging cutting-edge NLP tools such as **Cohere embeddings**, **ChromaDB**, and **document retrievers**, the system evaluates student submissions with precision and provides **detailed, step-by-step feedback**.

---

### **Key Features**  
- **Automated Assignment Grading:**  
  Automatically grades assignments on PCA by verifying each step against the expected PCA process flow.
  
- **Fact-Checking and Validation:**  
  Ensures that submissions contain **accurate explanations** of PCA steps (e.g., standardization, covariance matrix computation, eigenvalue decomposition) and flags **missing or incorrect steps**.

- **Structured Output Parsing:**  
  Generates **clear, JSON-like feedback** with sections for:
  - Correct answers.
  - Missing or incorrect steps.
  - Suggested corrections to guide students.

- **Scalability and Resilience:**  
  Designed to handle diverse assignment formats (PDF, text, markdown) and provides **consistent, unbiased grading** across different configurations.

---

### **System Workflow**  
1. **Document Ingestion:** The system reads assignment PDFs or text-based submissions using `PyPDFLoader` and splits them into manageable chunks.
2. **Embedding and Retrieval:** Assignments are converted into vector representations using **Cohere’s "embed-english-v2.0" model** and stored in **ChromaDB** for semantic search.
3. **Retrieval and Verification:** The system retrieves relevant content using **similarity search** and verifies the assignment’s PCA steps using a **RetrievalQA chain**.
4. **Output Parsing and Grading:**  
   The **StructuredOutputParser** ensures that feedback is returned in a consistent format, highlighting correct steps, errors, and recommended improvements.

---

### **Sample Grading Output**  
```json
{
  "correct_steps": [
    "Standardize the data.",
    "Calculate the covariance matrix."
  ],
  "incorrect_steps": [
    "Eigenvalue computation step missing.",
    "Incorrect sorting of eigenvectors."
  ],
  "suggested_fixes": [
    "Add eigenvalue computation alongside eigenvectors.",
    "Sort eigenvectors by descending eigenvalues."
  ]
}
```

---

### **Technology Stack**  
- **Language Model:** Cohere's `command-xlarge-nightly` for question-answering and feedback generation.  
- **Vector Database:** ChromaDB for fast, semantic content retrieval.  
- **Document Handling:** PyPDFLoader and RecursiveCharacterTextSplitter for parsing and splitting assignment submissions.  
- **Output Parsing:** StructuredOutputParser and OutputFixingParser for formatting responses and handling parsing errors.  

---

### **Use Cases**  
- **Educational Grading:** Automatically grades PCA-related assignments, reducing the manual workload for instructors and ensuring consistent feedback.  
- **Learning Feedback:** Provides students with actionable feedback, highlighting their strengths and areas for improvement in a structured format.  
- **Scalable Assessments:** Supports grading for large-scale student submissions across different formats and ensures unbiased, fact-based evaluations.  

---

### **Conclusion**  
The RAG-Based PCA Assignment Grading System serves as a robust, scalable framework for **automated and accurate assessment of machine learning assignments**. By combining **state-of-the-art NLP** with a **retrieval-augmented framework**, the system not only grades submissions but also provides valuable insights that can improve learning outcomes.
