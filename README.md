# End-to-End-LLM-Prototype-for-Automated-Car-Review-Analytics-QA
This project is an end-to-end LLM prototype developed to streamline the analysis and management of automotive customer feedback. It provides a suite of automated tools designed to extract actionable insights from unstructured customer reviews, assisting in corporate-level reporting and product quality monitoring.


Pipeline Breakdown
🎯 Stage 1: Customer Sentiment Analytics
Objective: Quantify user satisfaction automatically across product tiers.
Process: Ingests textual feedback, sanitizes encoding or formatting discrepancies, and executes batch predictions via a fine-tuned DistilBERT model. Text labels are dynamically mapped onto integer vectors (predictions and true_labels) to generate hard metrics like Accuracy and F1-Score.

🌍 Stage 2: Localization & Translation Quality Control
Objective: Support expanding operations in Spain by translating English inputs while monitoring quality.
Process: Isolates key contextual sentences and passes them through a MarianMT translation network. The generated translated_review is statistically cross-verified against human-certified ground truths via the Hugging Face evaluate framework, returning an explicit results dictionary containing exact BLEU score metrics.

🔍 Stage 3: Semantic Knowledge Extraction (Extractive QA)
Objective: Enable the chatbot to query specific points of interest from long paragraphs instantaneously.
Process: Feeds specific target questions alongside raw review contexts into a specialized MiniLM model trained on SQuAD 2.0. The architecture pinpoints exact character spans to deliver targeted, isolated answers (answer) without running generic keywords.

📝 Stage 4: Abstractive Feedback Condensation
Objective: Shorten verbose, rambling customer stories into high-density briefings for corporate review.
Process: Implements a heavy sequence-to-sequence BART model to read entire paragraphs and re-write them dynamically. The text generation engine is bounded by precise constraints (min_length=50, max_length=55) and set to deterministic decoding to guarantee consistent, highly accurate summaries (summarized_text).
