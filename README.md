# RAG-based AI Powered HR Assistant
<p align="center">
  <img src="https://github.com/akhilchibber/RAG-based-AI-Powered-HR-Assistant/blob/main/hr-assistant.jpg?raw=true" alt="earthml Logo">
</p>

Retrieval-Augmented Generation (RAG) to analyze and respond to queries about company HR policies using natural language processing.

## Dataset
The dataset used in this project consists of comprehensive HR policy documents including leave policies, remote work guidelines, expense reimbursement, parental leave, performance reviews, training and development, code of conduct, and working hours policies.

## Objective
The goal is to develop a Q&A system capable of delivering informed responses on company HR policies, demonstrating RAG's application in combining semantic data retrieval with generative language models for NLP analysis in enterprise HR management. Employees can query policies in plain English and receive accurate, grounded answers instantly.

## Key Components
- **Groq LLM**: Employs llama-3.3-70b-versatile for generating text responses that mimic human conversation.
- **Supabase**: Acts as a vector database (with pgvector extension) for storing and retrieving HR policy data semantically.
- **Google AI Studio**: Generates semantic embeddings for policy document chunks using Google's embedding models.
- **LangChain**: Orchestrates the interaction between components, facilitating the RAG process.
- **React Frontend**: Provides an intuitive chat interface for employees to query HR policies in natural language.

## Functionality
The system retrieves information from Supabase based on employee queries about HR policies, then uses Groq LLM to generate responses. This ensures accuracy and broader contextual understanding, resulting in precise and enriched answers grounded in actual company policy documents.
https://github.com/akhilchibber/RAG-based-AI-Powered-HR-Assistant/blob/main/hr-assistant.jpg

## Use Case
Ideal for HR departments, employees, and organizations seeking to streamline HR query resolution through natural language interfaces. It showcases how retrieval and generation can be integrated in NLP to improve information access, reduce HR workload, and enhance employee experience in understanding company policies.

## Getting Started
To get started with this project:

1. Clone this repository to your local machine.
2. Install the required dependencies: `pip install -r requirements.txt`
3. Configure your API keys in `.env` file (see `.env.example`)
4. Setup Supabase database (see `ARCHITECTURE.md` for SQL setup)
5. Index the HR policies: `python chatbot_final.py index`
6. Run the chatbot: `python chatbot_final.py` (CLI) or `python app.py` (Web)

## Contributing
We welcome contributions to enhance the functionality and efficiency of this script. Feel free to fork, modify, and make pull requests to this repository. To contribute:

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request against the main branch.

## License
This project is licensed under the MIT License - see the `LICENSE` file for details.

## Contact

Author: Akhil Chhibber  

LinkedIn: https://www.linkedin.com/in/akhilchhibber/  

Medium Blogs: https://medium.com/@akhil.chibber

Live Deployment: https://rag-biden-speech--akhilchibber.replit.app/
Medium Blogs: https://medium.com/@akhil.chibber  
Portfolio: https://akhil-portfolio.vercel.app/
