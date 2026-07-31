# 100 Technical Interview Questions & Answers

### Programming Languages: Python, HTML, & CSS

**1. What is the difference between a List and a Tuple in Python?**  
**Answer:** Lists are mutable, meaning their contents can be modified after creation, whereas tuples are immutable and cannot be changed. 

**2. How does Python manage memory?**  
**Answer:** Python utilizes a private heap space managed by the Python memory manager, along with a built-in garbage collector that handles reference counting to free up unused memory.

**3. What are decorators in Python?**  
**Answer:** Decorators are functions that modify the functionality of another function or method without permanently changing its source code.

**4. Can you explain the difference between `__init__` and `__new__` in Python?**  
**Answer:** `__new__` is responsible for creating a new instance of a class, while `__init__` is responsible for initializing the newly created object.

**5. How do you handle exceptions in Python?**  
**Answer:** Exceptions are handled using `try`, `except`, `else`, and `finally` blocks, which allow the program to catch errors and execute alternative code without crashing.

**6. What are Lambda functions?**  
**Answer:** Lambda functions are small, anonymous functions defined using the `lambda` keyword, typically used for short, throwaway operations.

**7. How do you manage package dependencies in a Python project?**  
**Answer:** Dependencies are typically managed using a virtual environment (like `venv` or `conda`) and tracked in a `requirements.txt` file.

**8. What is the difference between multithreading and multiprocessing in Python?**  
**Answer:** Multithreading runs multiple threads within a single process (limited by the Global Interpreter Lock), while multiprocessing creates separate memory spaces and processes, enabling true parallelism.

**9. How does CSS specificity work?**  
**Answer:** Specificity determines which CSS rule applies by assigning weights: inline styles have the highest weight, followed by IDs, classes/pseudo-classes, and finally element tags.

**10. What is the DOM in HTML?**  
**Answer:** The Document Object Model (DOM) is a programming interface for web documents that represents the page so programs can change the document structure, style, and content.

---

### Core CS Fundamentals: DSA & OOPS

**11. What are the four main principles of Object-Oriented Programming (OOPS)?**  
**Answer:** The four principles are Encapsulation, Abstraction, Inheritance, and Polymorphism.

**12. What is the difference between method overloading and method overriding?**  
**Answer:** Overloading occurs when multiple methods have the same name but different parameters in the same class. Overriding occurs when a subclass provides a specific implementation of a method already defined in its parent class.

**13. How does a Hash Table resolve collisions?**  
**Answer:** Collisions are commonly resolved using chaining (storing a linked list of elements at the same hash index) or open addressing (finding the next available slot).

**14. What is the time complexity of searching in a Binary Search Tree (BST)?**  
**Answer:** The average time complexity is O(log n), but in the worst-case scenario (an unbalanced tree), it degrades to O(n).

**15. What is the difference between a Stack and a Queue?**  
**Answer:** A Stack follows the Last-In-First-Out (LIFO) principle, whereas a Queue follows the First-In-First-Out (FIFO) principle.

**16. When would you use a Breadth-First Search (BFS) over a Depth-First Search (DFS)?**  
**Answer:** BFS is preferred for finding the shortest path in unweighted graphs, while DFS is better for exploring deep paths or detecting cycles.

**17. What is a memory leak, and how does it happen?**  
**Answer:** A memory leak occurs when a program fails to release memory that is no longer needed, eventually exhausting available system memory.

**18. Explain the difference between an Array and a Linked List.**  
**Answer:** Arrays store elements in contiguous memory locations, allowing fast index-based access. Linked lists store elements in non-contiguous nodes containing data and pointers, allowing faster insertions and deletions.

**19. What is a Deadlock in OS?**  
**Answer:** A deadlock is a state where two or more processes are blocked forever because they are each waiting for a resource held by another.

**20. What is Virtual Memory?**  
**Answer:** Virtual memory is an OS feature that uses hardware and software to allow a computer to compensate for physical memory shortages by temporarily transferring data from RAM to disk storage.

---

### Core CS Fundamentals: DBMS, SQL, & Computer Networks

**21. What is normalization in DBMS?**  
**Answer:** Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity.

**22. What are the ACID properties in database transactions?**  
**Answer:** ACID stands for Atomicity, Consistency, Isolation, and Durability, which guarantee that database transactions are processed reliably.

**23. Explain the difference between a Primary Key and a Foreign Key.**  
**Answer:** A Primary Key uniquely identifies a record in a table. A Foreign Key is a field in one table that links to the Primary Key of another table, establishing a relationship.

**24. What is the difference between `DELETE` and `TRUNCATE` in SQL?**  
**Answer:** `DELETE` removes rows one by one and records the action in the transaction log, while `TRUNCATE` removes all rows quickly without logging individual row deletions.

**25. Explain the difference between `INNER JOIN` and `LEFT JOIN`.**  
**Answer:** `INNER JOIN` returns only the rows with matching values in both tables, whereas `LEFT JOIN` returns all rows from the left table and the matched rows from the right table (filling with NULL if no match exists).

**26. How do indexes improve database performance?**  
**Answer:** Indexes create data structures (like B-trees) that allow the database engine to locate and retrieve specific rows much faster than scanning the entire table.

**27. What is the OSI Model in Computer Networks?**  
**Answer:** The OSI model is a conceptual framework consisting of 7 layers (Physical, Data Link, Network, Transport, Session, Presentation, Application) that standardizes networking communication.

**28. What is the difference between TCP and UDP?**  
**Answer:** TCP is a connection-oriented protocol that ensures reliable data delivery. UDP is a connectionless protocol that sends data quickly but without guaranteeing delivery or order.

**29. What is the role of a DNS server?**  
**Answer:** A Domain Name System (DNS) server translates human-readable domain names into IP addresses that computers use to identify each other on a network.

**30. Explain what a subnet mask does.**  
**Answer:** A subnet mask is used to divide an IP address into two parts: the network address and the host address, allowing the creation of sub-networks.

---

### Frameworks, Libraries & Machine Learning

**31. How does NumPy differ from standard Python lists?**  
**Answer:** NumPy arrays are strictly homogeneous, store data in contiguous memory blocks, and offer optimized, vectorized mathematical operations written in C, making them significantly faster.

**32. What is a Pandas DataFrame?**  
**Answer:** A DataFrame is a two-dimensional, mutable, tabular data structure with labeled axes (rows and columns) in Pandas.

**33. How do you handle missing data in Pandas?**  
**Answer:** Missing data can be dropped using `dropna()` or imputed using techniques like mean/median substitution via the `fillna()` method.

**34. What is the difference between supervised and unsupervised learning?**  
**Answer:** Supervised learning uses labeled training data to predict outcomes, whereas unsupervised learning finds hidden patterns or groupings in unlabeled data.

**35. Explain the concept of Overfitting.**  
**Answer:** Overfitting occurs when a machine learning model learns the training data too well, including its noise, resulting in poor performance on unseen or test data.

**36. What is Cross-Validation in Scikit-learn?**  
**Answer:** Cross-validation is a resampling procedure (like k-fold) used to evaluate machine learning models on a limited data sample to ensure the model generalizes well.

**37. How does a Random Forest algorithm work?**  
**Answer:** Random Forest is an ensemble learning method that constructs multiple decision trees during training and outputs the mode of the classes or mean prediction of the individual trees.

**38. What is Principal Component Analysis (PCA)?**  
**Answer:** PCA is a dimensionality reduction technique that transforms a large set of variables into a smaller one that still contains most of the original data's information.

**39. How is Matplotlib utilized in an ML pipeline?**  
**Answer:** Matplotlib is used for data visualization, allowing developers to plot graphs like histograms, scatter plots, and loss curves to understand data distributions and model performance.

**40. What is a Confusion Matrix?**  
**Answer:** A confusion matrix is a table used to evaluate the performance of a classification model, outlining True Positives, True Negatives, False Positives, and False Negatives.

---

### Projects: Predicting and Diagnosing Diseases Using Deep Learning

**41. What structured healthcare data features did you engineer for the disease prediction system?**  
**Answer:** Feature engineering typically involved handling missing clinical values, normalizing numerical test results, and encoding categorical patient data to optimize it for deep learning architectures.

**42. How did you structure the end-to-end ML pipeline for disease diagnosis?**  
**Answer:** The pipeline included data preprocessing, feature extraction, model training using ANN/CNN/RNN architectures, and finalizing the model through rigorous performance evaluation.

**43. What is an Artificial Neural Network (ANN)?**  
**Answer:** An ANN is a computational model inspired by biological neural networks, consisting of interconnected nodes (neurons) distributed across input, hidden, and output layers.

**44. How does a Convolutional Neural Network (CNN) differ from an ANN?**  
**Answer:** CNNs utilize convolutional layers and pooling to automatically detect spatial hierarchies and features, making them highly effective for structured grid data or images.

**45. What specific problem does a Recurrent Neural Network (RNN) solve?**  
**Answer:** RNNs contain loops that allow information to persist, making them highly suited for sequential or time-series data where the current output depends on previous inputs.

**46. You achieved 95% accuracy in your disease prediction model; how do you ensure this wasn't due to an imbalanced dataset?**  
**Answer:** High accuracy in imbalanced medical datasets can be misleading, which is why I also evaluated the model using precision, recall, and the F1-score to ensure reliable diagnostic performance across all classes.

**47. Explain Precision vs. Recall in the context of disease diagnosis.**  
**Answer:** Precision measures how many predicted positive diseases were actual positives, while recall measures how many actual positive diseases the model successfully identified (crucial for minimizing false negatives in healthcare).

**48. Why is the F1-score an important metric in healthcare ML pipelines?**  
**Answer:** The F1-score is the harmonic mean of precision and recall, providing a single metric that balances the trade-off between false positives and false negatives.

**49. What activation function would you use in the output layer for a binary disease classification problem?**  
**Answer:** The Sigmoid activation function is standard for binary classification as it outputs a probability value between 0 and 1.

**50. How do TensorFlow and PyTorch handle computational graphs differently?**  
**Answer:** Historically, TensorFlow used static computational graphs (though Eager Execution changed this), whereas PyTorch inherently relies on dynamic computation graphs, allowing for more flexible debugging.

---

### Projects: Touchless Brightness Control & Computer Vision

**51. What role did OpenCV play in your Touchless Brightness Control project?**  
**Answer:** OpenCV was used to capture real-time video frames from the webcam, preprocess the images, and overlay visual feedback on the screen.

**52. How does MediaPipe extract hand landmarks?**  
**Answer:** MediaPipe utilizes machine learning models to infer 21 3D landmarks of a hand from a single video frame in real-time.

**53. How did you map finger-distance gestures to screen brightness levels?**  
**Answer:** I calculated the Euclidean distance between the tip of the thumb and the index finger landmarks and interpolated this distance range into a brightness percentage (0-100%).

**54. What is the formula for Euclidean distance?**  
**Answer:** The Euclidean distance between two points $(x_1, y_1)$ and $(x_2, y_2)$ is $\sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$.

**55. How do you handle hand tracking occlusion or when hands exit the camera frame?**  
**Answer:** The pipeline includes validation checks to ensure landmarks are actively detected in the current frame before attempting to calculate coordinates or adjust brightness.

**56. In OpenCV, what color format are images read in by default?**  
**Answer:** OpenCV reads images in BGR (Blue, Green, Red) format by default, which often requires conversion to RGB for compatibility with libraries like MediaPipe.

**57. What is an affine transformation in image processing?**  
**Answer:** An affine transformation is a geometric transformation that preserves points, straight lines, and planes (e.g., rotation, scaling, and translation).

**58. How do you optimize real-time computer vision pipelines to maintain high FPS?**  
**Answer:** Optimizations include reducing the resolution of input frames, processing every *nth* frame, or offloading heavy computations to GPU hardware.

**59. What accessibility problem did your brightness control project solve?**  
**Answer:** It improved accessibility by enabling hands-free interaction, reducing the need for physical device contact to manage system settings.

**60. What is image thresholding?**  
**Answer:** Thresholding is a simple segmentation technique that converts grayscale images into binary images by setting pixels above a certain threshold to white and others to black.

---

### Projects: Detection of Oil Spill Using Marine Environments

**61. What types of image preprocessing techniques are essential for satellite imagery?**  
**Answer:** Essential techniques include noise reduction (filtering), radiometric calibration, atmospheric correction, and contrast enhancement.

**62. How did you extract features from marine images to detect oil spills?**  
**Answer:** Feature extraction involved identifying texture, shape, and color/intensity variations that distinguish the smooth, dark signatures of oil slicks from natural wave patterns.

**63. What challenges exist when classifying oil spills versus "look-alikes" (like algal blooms)?**  
**Answer:** Look-alikes can have similar pixel intensities, requiring advanced machine learning models to analyze complex spatial textures and contextual features to prevent false positives.

**64. Which machine learning algorithms are typically best suited for binary image classification?**  
**Answer:** Support Vector Machines (SVMs), Random Forests, or Convolutional Neural Networks (CNNs) are highly effective for binary classification of image features.

**65. What is the role of automated image analysis in environmental monitoring?**  
**Answer:** It replaces slow, manual analysis with high-speed, continuous processing, allowing for the timely identification of hazards like oil spills to accelerate emergency response.

**66. What is a gradient descent optimizer?**  
**Answer:** Gradient descent is an optimization algorithm used to minimize the loss function by iteratively moving in the direction of steepest descent.

**67. Explain the concept of Data Augmentation in ML.**  
**Answer:** Data augmentation artificially expands the size of a training dataset by applying random transformations (rotations, flips, zooming) to improve model robustness.

**68. What is the vanishing gradient problem?**  
**Answer:** It is a difficulty in training deep neural networks where the gradients used to update the weights become exceedingly small, stopping the network from learning.

**69. How did you structure the labels for your oil spill dataset?**  
**Answer:** The dataset was labeled into binary categories: oil-spill and non-oil-spill classes for supervised machine learning training.

**70. What is transfer learning, and could it be applied to satellite image detection?**  
**Answer:** Transfer learning uses a pre-trained model (like ResNet trained on ImageNet) and fine-tunes it on a new task, which is highly effective for satellite imagery when labeled data is scarce.

---

### Cybersecurity, Penetration Testing & SOC

**71. What is the role of a Security Operations Center (SOC)?**  
**Answer:** A SOC continuously monitors, prevents, detects, investigates, and responds to cyber threats utilizing security technologies and processes.

**72. What are the key phases of an Incident Response plan?**  
**Answer:** The core phases are Preparation, Identification/Detection, Containment, Eradication, Recovery, and Lessons Learned.

**73. What is Ethical Hacking?**  
**Answer:** Ethical hacking involves legally breaking into computers and devices to test an organization's defenses and identify vulnerabilities before malicious hackers can exploit them.

**74. What is the difference between a Vulnerability Assessment and Penetration Testing (VAPT)?**  
**Answer:** A vulnerability assessment is an automated scan to identify security weaknesses, while penetration testing involves actively exploiting those vulnerabilities to determine their real-world impact.

**75. What is Cross-Site Scripting (XSS)?**  
**Answer:** XSS is a web vulnerability where attackers inject malicious client-side scripts into web pages viewed by other users.

**76. How do you prevent SQL Injection (SQLi)?**  
**Answer:** SQLi is prevented by using prepared statements with parameterized queries, input validation, and stored procedures instead of concatenating raw SQL strings.

**77. What is a Bug Bounty program?**  
**Answer:** A bug bounty is a crowdsourced initiative where organizations reward ethical hackers for discovering and responsibly reporting software vulnerabilities.

**78. Explain the concept of Hardware-Level Hacking.**  
**Answer:** It involves exploiting physical interfaces (like UART, JTAG, or SPI) and firmware vulnerabilities directly on the physical device or IoT component.

**79. What is the OWASP Top 10?**  
**Answer:** It is a standard awareness document that outlines the 10 most critical security risks to web applications, such as Broken Access Control and Injection.

**80. What is a SIEM, and how is it used in a SOC?**  
**Answer:** Security Information and Event Management (SIEM) systems aggregate and analyze log data from across the network in real-time to detect anomalous activity and generate alerts for the SOC team.

**81. Describe the difference between Symmetric and Asymmetric Encryption.**  
**Answer:** Symmetric encryption uses the same key for both encryption and decryption. Asymmetric encryption uses a pair of keys: a public key for encryption and a private key for decryption.

**82. What is a Man-in-the-Middle (MitM) attack?**  
**Answer:** A MitM attack occurs when a hacker intercepts and potentially alters communications between two parties who believe they are communicating directly with each other.

**83. How does a firewall differ from an Intrusion Detection System (IDS)?**  
**Answer:** A firewall blocks or allows traffic based on predefined rules, acting as a barrier. An IDS monitors network traffic for suspicious activity and issues alerts but does not block the traffic itself.

**84. What is the CIA Triad in information security?**  
**Answer:** The CIA Triad stands for Confidentiality (data is private), Integrity (data is unaltered), and Availability (data is accessible when needed).

**85. What tools are standard for identifying web vulnerabilities?**  
**Answer:** Industry-standard tools for web application testing include Burp Suite, OWASP ZAP, Nmap, and Metasploit.

**86. What is Cross-Site Request Forgery (CSRF)?**  
**Answer:** CSRF is an attack that forces an end user to execute unwanted actions on a web application in which they are currently authenticated.

**87. What is Threat Modeling?**  
**Answer:** Threat modeling is a structured process of identifying potential security threats and vulnerabilities, quantifying their criticality, and prioritizing mitigation strategies.

**88. Explain the concept of Least Privilege.**  
**Answer:** The principle of least privilege dictates that users and systems should only be granted the minimum level of access permissions necessary to perform their required tasks.

**89. What is Network Sniffing?**  
**Answer:** Network sniffing involves capturing and analyzing data packets transmitted over a network to monitor traffic or maliciously steal unencrypted data like passwords.

**90. How do you secure an API?**  
**Answer:** APIs are secured by using HTTPS for encryption, implementing strong authentication (like OAuth2), validating all input data, and applying rate limiting to prevent abuse.

---

### System Design & Advanced Tech

**91. What is the importance of System Design in scalable software?**  
**Answer:** System design defines the architecture, components, modules, interfaces, and data for a system to satisfy specific functional requirements while ensuring horizontal or vertical scalability.

**92. What is a Load Balancer?**  
**Answer:** A load balancer is a device or software that distributes network or application traffic across a cluster of servers to improve responsiveness and availability.

**93. Explain the difference between horizontal and vertical scaling.**  
**Answer:** Vertical scaling (scaling up) means adding more power (CPU, RAM) to an existing server. Horizontal scaling (scaling out) means adding more servers to your resource pool.

**94. What is caching, and why is it used?**  
**Answer:** Caching temporarily stores frequently accessed data in fast-access memory (like Redis or Memcached) to reduce database load and improve application response times.

**95. What are Microservices?**  
**Answer:** Microservices are an architectural style that structures an application as a collection of loosely coupled, independently deployable services organized around business capabilities.

**96. What is the CAP Theorem?**  
**Answer:** The CAP Theorem states that a distributed data store can only simultaneously provide two out of three guarantees: Consistency, Availability, and Partition tolerance.

**97. In AI-driven drug discovery (Bioinformatics), what is molecular docking?**  
**Answer:** Molecular docking is a computational technique used to predict the preferred orientation of one molecule to a second when bound to each other to form a stable complex.

**98. How do transformer architectures improve upon RNNs?**  
**Answer:** Transformers process entire sequences simultaneously using self-attention mechanisms rather than sequentially, which eliminates the vanishing gradient problem and allows for massive parallelization.

**99. What is a RESTful API?**  
**Answer:** A RESTful API is an architectural style for an application program interface that uses HTTP requests to access and use data, adhering to constraints like statelessness and a uniform interface.

**100. How does Docker contribute to a development environment?**  
**Answer:** Docker containerizes applications and their dependencies, ensuring that the software runs consistently across any environment, from a developer's local machine to cloud production.        