## Project Overview

Modern healthcare environments increasingly leverage autonomous AI agents to perform complex clinical reporting, operational analytics, and decision support. However, granting generative systems direct read access to health databases introduces severe data leakage risks, directly impacting HIPAA compliance. To reduce unauthorized exposure of PHI, this risk assessment evaluates a Multi-Tier Sanitization Enclave. Positioned between a database and querying agents, the enclave deploys a defense-in-depth pipeline consisting of:

- Tier 1: Deterministic Sanitization Rules (Regex) for structured, standardized identifiers.
- Tier 2: Named Entity Recognition (NER) models for semi-structured text.
- Tier 3: Agentic Generative AI to resolve edge cases.

## Scope

The assessment is purely being conducted on the information system described above, and findings align with the NIST AI Risk Management Framework and incorporates threat profiles detailed in NIST AI 100-2e2023 (Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations).

## System Architecture

This Information System is designed to intercept database queries made by autonomous AI agents and require the corresponding payload to be sanitized of all PHI before being returned to the agent. 

<img width="650" height="650" alt="enclave_topology" src="https://github.com/user-attachments/assets/a03327f8-abed-41cb-aaa7-fb6592269e8b" />

*Sanitization Enclave Data Flow*

### How it Works

1. An authenticated user or AI agent queries the patient database to retrieve information. The request is evaluated at a Policy Enforcement Point, and the user status is determined based on the JWT claims (human user or AI agent). If the user is a human, they can access un-sanitized data. If not, the request is forwarded to the enclave.

2. The enclave queries the database with the forwarded request, and information is retrieved on behalf of the agent.

3. The raw, un-sanitized data passes through the sanitization pipeline, scrubbing user PHI. Regex handles structured data, NER models catch more complex sentences and information, and AI handles edge cases.

4. After the data is confirmed to be sanitized, it is returned to the agentic for it to continue its workflow.


## Assessing the Risk

This risk assessment was performed using qualitative descriptions (from Low to Critical), based on threats detailed in the NIST AI RMF 1.0 and NIST AI 100-2e2023

## Conclusion

Completing this project helped me understand more about AI's integration with identity, and how risk is assessed revolving around all different types of Artificial Intelligence. Conducting this on a hypothetical system will aid me in future assessments on potential and active systems in the workforce.

