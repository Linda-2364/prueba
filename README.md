# LegalMatch AI

Final project for the Building AI course

## Summary

LegalMatch AI is an AI-powered system that analyzes a client's legal situation from a short text description, automatically classifies the type of case (labor, civil, criminal, family law), and recommends the most suitable lawyer within a law firm based on their track record with similar cases. The goal is to make legal guidance faster, fairer, and more accessible for people who don't know where to start.

## Resumen

LegalMatch AI es un sistema impulsado por IA que analiza la situación legal de un cliente a partir de una breve descripción en texto, clasifica automáticamente el tipo de caso (laboral, civil, penal, familiar) y recomienda al abogado más adecuado dentro de un estudio jurídico según su historial de éxito en casos similares. El objetivo es hacer que la orientación legal sea más rápida, justa y accesible para personas que no saben por dónde empezar.

## Background

### Problems this solution addresses

* **Lack of initial guidance** — Most people facing a legal issue for the first time don't know which type of lawyer or legal area applies to their situation, which causes delays and frustration.
* **Inefficient manual case assignment** — Law firms often assign cases to lawyers based on availability rather than specialization or track record, which can lead to worse outcomes for clients.
* **Difficulty finding specialized lawyers** — Even within a single firm, clients rarely have visibility into which lawyer has the best success rate for a case like theirs.
* **Unequal access to legal information** — Legal jargon and unclear processes disproportionately affect people with lower income or education, widening the access-to-justice gap.

### Personal motivation

While working as a frontend developer intern for a legal services company, I noticed that case intake was handled manually: staff read client descriptions and assigned cases to lawyers based on personal judgment and availability, with no systematic use of the historical case data already stored in the system. This showed me a clear opportunity where even a simple AI classifier could meaningfully improve both the client experience and the firm's internal efficiency — using techniques I directly studied in this course, like Naive Bayes text classification and nearest-neighbor recommendation.

### Why this matters

Access to timely, well-matched legal advice is a basic component of a functioning justice system. In many countries, including Bolivia, there is no dedicated infrastructure to help ordinary citizens understand their legal options quickly. A tool like LegalMatch AI would not replace lawyers, but would lower the first barrier — knowing where to start — while also helping law firms operate more efficiently and fairly distribute cases among their staff.

## How is it used?

### User flow

1. The client fills out a short web form describing their situation in plain language (e.g., "My employer didn't pay my severance when I was let go").
2. The system processes the text using a bag-of-words representation and a Naive Bayes classifier trained on previously labeled case descriptions, predicting the legal area (labor, civil, criminal, family).
3. Based on the predicted category, the system compares the new case's characteristics against the firm's historical case database using the nearest-neighbor method, identifying which lawyers have handled the most similar cases successfully.
4. The system presents the client with the recommended legal area and a shortlist of 2–3 lawyers best suited to their case, along with a brief explanation of why they were selected.
5. Internally, firm administrators also see this same recommendation when manually assigning or reviewing case load, helping balance workload and specialization.

### Who uses it

| User type | Description | Needs |
|---|---|---|
| First-time legal clients | People unfamiliar with legal processes | Simple language, clear next steps |
| Returning clients | People with an ongoing case wanting a second opinion or additional service | Fast, accurate matching |
| Law firm administrative staff | Responsible for assigning cases to lawyers | Data-backed assignment suggestions, workload balancing |
| Lawyers | Specialists who want relevant cases matched to their expertise | Better case-fit, less time spent on unsuitable cases |

## Data sources and AI methods

The training data would come from the firm's existing case management system, which already logs case type, assigned lawyer, and case outcome — the same kind of structured data I work with directly in my current frontend internship project. To bootstrap the text classifier, an initial labeled dataset of case descriptions and their correct legal category would be needed, ideally reviewed by an actual lawyer for accuracy.

Planned techniques, all covered in this course:

* **Bag-of-words + Naive Bayes classifier** — to classify the free-text case description into a legal category, similar to the spam-filtering exercise from Chapter 3 of Building AI.
* **Nearest-neighbor method (Euclidean or Manhattan distance)** — to compare a new case's numeric and categorical features (case type, estimated complexity, region, etc.) against historical cases and recommend the most similar successful outcomes.
* **TF-IDF weighting** — to improve the text classifier by giving more importance to distinctive words in the case description ("dismissed", "custody", "eviction") rather than common ones.

A simple working prototype would use Python with scikit-learn for the Naive Bayes classifier and a small Flask API to connect it to a basic web form, similar to the architecture I'm already familiar with from my internship work.

## Challenges

* **This tool does not replace legal advice.** A human lawyer must always make the final decision — the system only assists with orientation and internal case routing.
* **Bias risk.** If the historical case data is imbalanced (e.g., mostly labor cases, or mostly handled by senior lawyers), the model could unfairly under-recommend certain lawyers or case types. Regular auditing of recommendations would be necessary.
* **Data privacy.** Case descriptions and outcomes are sensitive personal and legal information. Any real implementation would need strict access controls, anonymization where possible, and compliance with local data protection regulations.
* **Cold start problem.** For a firm with little historical data, or a completely new type of case, the recommendation quality would initially be poor until enough data accumulates.
* **Language and dialect variation.** Legal Spanish varies by country and region; a classifier trained on one country's case data may not generalize well to another without retraining.

## What next?

Future versions of this project could include:

* A conversational chatbot front-end that asks clarifying follow-up questions before making a final classification, improving accuracy for ambiguous cases.
* Integration with publicly available court records or legal precedent databases to also predict a rough probability of case success, not just lawyer matching.
* A feedback loop where lawyers confirm or correct the AI's classification after reviewing a case, continuously improving the model over time.
* Expanding beyond a single firm into a public-facing tool that helps connect any citizen with an appropriate lawyer or legal aid organization, particularly in underserved regions.

To move forward, I would need deeper experience with Spanish-language NLP, access to a larger and better-labeled dataset of real (anonymized) case data, and collaboration with practicing lawyers to validate that the model's recommendations are legally sound and unbiased.

## Acknowledgments

* Inspired by the Building AI course by Reaktor and the University of Helsinki, particularly the chapters on Naive Bayes classification, the nearest-neighbor method, and TF-IDF text representation.
* Conceptually inspired by my ongoing frontend development internship at a legal services company, which highlighted the real-world gap this project addresses.
* [Building AI course README template](https://buildingai.elementsofai.com) used as the base structure for this document.
