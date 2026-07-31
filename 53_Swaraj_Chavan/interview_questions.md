# Comprehensive AI/ML Interview Question Bank
> **Candidate:** Swaraj Narendra Chavan  
> **Target Roles:** Machine Learning Engineer | Computer Vision Specialist | AI Research & Systems Engineer  
> **Source Context:** Academic & Professional Resume (M.Tech AI & ML, LPU | B.E. CSE, GCOER)

---

## 📑 Table of Contents
1. [Part 1: CV-Specific Technical & Project Questions](#part-1-cv-specific-technical--project-questions)
   - [Real-Time Face Mask Detection System](#1-real-time-face-mask-detection-system-feb-2026---apr-2026)
   - [UPSC Interview Chatbot (Microsoft Founders Hub)](#2-upsc-interview-chatbot-aug-2023---mar-2024)
   - [HXRAI: Explainable & Responsible AI Framework](#3-hxrai-explainable--responsible-ai-in-healthcare)
   - [Internships & Professional Experience](#4-internships--professional-experience)
   - [Core Technical & Theoretical AI/ML](#5-core-technical--theoretical-aiml-cv-derived)
   - [Logical, System Design & Scenario-Based Questions](#6-logical-problem-solving--scenario-based-questions)
   - [Academics, Career & Soft Skills](#7-academics-career--soft-skills)
2. [Part 2: Domain & Field-Based Technical Questions](#part-2-domain--field-based-technical-questions)
   - [AI & Machine Learning Foundations](#1-ai--machine-learning-foundations)
   - [Computer Vision & Edge AI](#2-computer-vision--edge-ai)
   - [Explainable & Responsible AI (XAI / Trustworthy AI)](#3-explainable--responsible-ai-xai--trustworthy-ai)
   - [Natural Language Processing & Conversational AI](#4-natural-language-processing-nlp--conversational-ai)
   - [Software Engineering, Tools & Data Pipelines](#5-software-engineering-tools--data-pipelines)
   - [Responsive Web Technologies & Frontend Integration](#6-responsive-web-technologies--frontend-integration)

---

# Part 1: CV-Specific Technical & Project Questions

### 1. Real-Time Face Mask Detection System (Feb 2026 - Apr 2026)
> **Key Focus Areas:** MobileNetV2, Transfer Learning, Focal Loss, Edge CPU Optimization, OpenCV Latency Reduction.

1. **How** did you choose MobileNetV2 over other architectures (e.g., ResNet, YOLO, or VGG) for your face mask detection system?
2. **What** specific hyperparameter tuning steps did you take to achieve 99% classification accuracy?
3. **Why** did you implement Focal Loss instead of standard Binary Cross-Entropy, and how does Focal Loss specifically address class imbalance?
4. **How** does Focal Loss mathematically adjust the loss for easy vs. hard examples?
5. **What** data augmentation techniques were used, and how did they ensure robustness against varying environmental conditions like lighting or occlusion?
6. **How** did you achieve a 20% reduction in inference latency for OpenCV-based video processing?
7. **Where** were the bottleneck operations during real-time video streaming, and how did you profile them?
8. **Why** did you target CPU-based edge deployment instead of leveraging GPU acceleration?
9. **How** do depthwise separable convolutions in MobileNetV2 reduce parameter count and computational complexity compared to standard convolutions?
10. **What** metrics beyond accuracy (e.g., FPS, memory footprint, precision/recall per class) did you track during real-time edge deployment?

---

### 2. UPSC Interview Chatbot (Aug 2023 - Mar 2024)
> **Key Focus Areas:** Detailed Application Form (DAF) Engine, Context Mapping, Tokenization, Conversational Memory, Microsoft Founders Hub.

11. **What** was your exact architectural design for the DAF (Detailed Application Form) parsing engine?
12. **How** did you extract structured features (e.g., hobbies, education history, regional background) from unstructured DAF documents?
13. **Why** did you use specific tokenization and context-mapping techniques, and how did they prevent hallucination during mock board interactions?
14. **How** was long-term context managed across multi-turn interview conversations so the chatbot remembered early interview responses?
15. **What** underlying NLP model or LLM framework did you leverage, and why?
16. **Where** and how did you deploy this system within the Microsoft Founders Hub infrastructure?
17. **How** did you evaluate the quality, tone, and domain accuracy of the generated interview questions?
18. **What** fallback mechanisms were implemented when the parsing engine encountered an improperly formatted DAF PDF/document?

---

### 3. HXRAI: Explainable & Responsible AI in Healthcare
> **Key Focus Areas:** Clinical Interpretability, LIME, SHAP, Grad-CAM, Algorithmic Fairness, AIF360.

19. **What** inspired the development of the HXRAI framework, and what specific problem in healthcare AI does it solve?
20. **How** do LIME and SHAP complement each other in your framework, and how do their underlying mathematical approaches differ?
21. **Why** is Grad-CAM particularly suited for clinical image interpretability compared to model-agnostic methods like LIME?
22. **What** specific bias metrics (e.g., Disparate Impact, Equalized Odds) did you evaluate using AIF360?
23. **How** did you apply AIF360 bias mitigation (pre-processing, in-processing, or post-processing) without significantly degrading model accuracy?
24. **Where** is the research currently accepted/submitted, and what were the main reviewer comments?
25. **How** would a medical clinician interact with the combined outputs of LIME, SHAP, and Grad-CAM in a real-world software interface?

---

### 4. Internships & Professional Experience
> **Key Focus Areas:** Regression & Classification Pipelines, Business Data EDA, Reusable UI Components, Responsive Layouts.

26. **What** business datasets did you work on during your Machine Learning Internship at YBI Foundation?
27. **How** did you decide which feature engineering techniques to apply during your data preprocessing at YBI Foundation?
28. **Why** might F1-Score or Precision be a better evaluation metric than Accuracy in business classification scenarios?
29. **What** techniques did you use to build reusable UI components during your web development internship at Oasis Infobyte?
30. **How** did you ensure cross-browser compatibility and layout optimization for both mobile and desktop views?

---

### 5. Core Technical & Theoretical AI/ML (CV-Derived)
> **Key Focus Areas:** High-Dimensional Data, Activation Functions, Regularization, Optimization, Interpretability Maths.

31. **What** is the curse of dimensionality, and how does it affect distance-based machine learning algorithms?
32. **How** does the trade-off between Bias and Variance manifest when choosing model complexity in Scikit-learn algorithms?
33. **Why** do neural networks require non-linear activation functions (e.g., ReLU, GELU) instead of linear activations?
34. **How** does transfer learning work fundamentally, and when should you fine-tune the entire network versus freezing lower layers?
35. **What** is the difference between L1 (Lasso) and L2 (Ridge) regularization, and how do they affect feature weights?
36. **How** does the Adam optimizer combine the concepts of Momentum and RMSProp?
37. **What** is Vanishing/Exploding Gradient, and how do architectures like MobileNetV2 or ResNet mitigate it?
38. **How** do precision, recall, and the PR-AUC curve behave when dealing with extreme class imbalance?
39. **Why** is SHAP computationally expensive compared to LIME, and how are Shapley values calculated?
40. **How** does Grad-CAM use the gradients of the target class with respect to the final convolutional layer to generate a heat map?

---

### 6. Logical, Problem-Solving & Scenario-Based Questions
> **Key Focus Areas:** Production Debugging, System Scalability, Data Quality Imputation, Multithreading, Concept Drift.

41. **Logical Scenario:** If your face mask detection model achieves 99% accuracy in testing but drops to 60% accuracy in production due to night lighting, how would you debug and fix the pipeline?
42. **System Design:** How would you scale the UPSC Chatbot to handle 10,000 concurrent user sessions while maintaining low latency?
43. **Data Quality:** If a dataset for healthcare AI has 30% missing values in key numerical features, what imputation strategy would you use and why?
44. **Optimization:** If a C++ or Python implementation of image processing is bottlenecked by frame-by-frame processing, how would you redesign it using multithreading or vectorization?
45. **Model Drift:** How would you detect and handle concept drift in a real-time object detection or classification system deployed on edge devices?

---

### 7. Academics, Career & Soft Skills
> **Key Focus Areas:** M.Tech Research, C++/Python Engineering Foundations, Role Preferences, Adaptability.

46. **What** specific subjects or research areas during your M.Tech at Lovely Professional University directly influenced your work on HXRAI?
47. **How** did your Computer Science foundational courses at Govt. College of Engineering and Research help you write efficient AI/ML code in C++ and Python?
48. **Where** do you see yourself contributing most in an engineering team—core ML research, model optimization/edge deployment, or full-stack AI system development?
49. **Can you describe a time** when you had to adapt quickly to a tool or framework you had never used before to meet a project deadline?
50. **How** do you balance model interpretability/explainability with raw predictive accuracy when building real-world AI applications?

---

# Part 2: Domain & Field-Based Technical Questions

### 1. AI & Machine Learning Foundations
51. How do you evaluate whether a problem requires a traditional statistical/ML model versus a Deep Learning approach?
52. What is the bias-variance tradeoff, and how do you diagnose and address underfitting or overfitting in your models?
53. Can you explain the difference between generative and discriminative models, giving examples of when you would use each?
54. How do feature scaling techniques like standardization (Z-score) and normalization (Min-Max) impact gradient descent optimization?
55. What strategies do you use when dealing with severely imbalanced datasets beyond resampling techniques (e.g., SMOTE)?

---

### 2. Computer Vision & Edge AI
56. How do convolutional layers differ from fully connected layers in terms of feature extraction and parameter efficiency?
57. What are the main trade-offs between speed, accuracy, and model size when preparing a Computer Vision model for edge deployment?
58. How does transfer learning work, and how do you decide which layers to freeze versus fine-tune?
59. What techniques (e.g., quantization, pruning, batch inference, hardware acceleration) are most effective for reducing inference latency?
60. How do data augmentation strategies differ between object classification, object detection, and semantic segmentation tasks?

---

### 3. Explainable & Responsible AI (XAI / Trustworthy AI)
61. Why is model explainability critical in high-stakes domains like healthcare, finance, or recruitment?
62. What is the key difference between local explainability methods (e.g., LIME, Grad-CAM) and global explainability methods (e.g., global SHAP values)?
63. How do you measure and identify algorithmic bias in a machine learning pipeline before deploying it to production?
64. What are the main limitations or failure modes of popular interpretability tools like SHAP or LIME?
65. How do you handle scenarios where mitigating algorithmic bias leads to a slight decrease in overall model performance metrics?

---

### 4. Natural Language Processing (NLP) & Conversational AI
66. What are the key differences between traditional rule-based/regex NLP techniques and modern Transformer-based architectures?
67. How do tokenization choices (word-level, character-level, subword units like Byte-Pair Encoding) affect downstream model performance?
68. What approaches exist for tracking multi-turn context and intent in conversational dialog systems?
69. How do you evaluate the quality, coherence, and safety of generated conversational responses when standard accuracy metrics aren't applicable?
70. What mechanisms can be put in place to prevent language models from hallucinating factual inaccuracies during specialized tasks?

---

### 5. Software Engineering, Tools & Data Pipelines
71. How do you structure a Python project to ensure clean code, modularity, and easy scalability across different environments?
72. How do dynamically typed languages like Python compare to statically typed languages like C++ when optimizing for memory management and computational performance?
73. What best practices do you follow for version control using Git when working on collaborative data science or software projects?
74. How do pandas and NumPy optimize matrix and array computations under the hood compared to native Python lists?
75. What design patterns do you use when building RESTful APIs or integrating ML backends with web frontends?

---

### 6. Responsive Web Technologies & Frontend Integration
76. What are the key principles of responsive web design, and how do frameworks like Bootstrap simplify cross-device compatibility?
77. How does the Document Object Model (DOM) work, and how do modern JavaScript frameworks optimize DOM manipulation?
78. How do you bridge the connection between asynchronous frontend user interfaces (HTML/CSS/JS) and machine learning microservices?