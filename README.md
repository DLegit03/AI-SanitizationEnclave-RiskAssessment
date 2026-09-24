## Project Overview

Modern healthcare environments increasingly leverage autonomous AI agents to perform complex clinical reporting, operational analytics, and decision support. However, granting generative systems direct read access to health databases introduces severe data leakage risks, directly impacting HIPAA compliance. To reduce unauthorized exposure of PHI, this risk assessment evaluates a Multi-Tier Sanitization Enclave. Positioned as an intermediary between a database and querying agents, the enclave deploys a defense-in-depth pipeline consisting of:

- Tier 1: Deterministic Sanitization Rules (Regex) for structured, standardized identifiers.
- Tier 2: Named Entity Recognition (NER) models for semi-structured text.
- Tier 3: Agentic Generative AI to resolve edge cases.

## Scope

The assessment aligns with the NIST AI Risk Management Framework and incorporates threat profiles detailed in NIST AI 100-2e2023 (Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations).

## System Architecture

This Information System is designed to intercept database queries made by autonomous AI agents and require the corresponding payload to be sanitized of all PHI before being returned to the agent. 

<img width="650" height="650" alt="enclave_topology" src="https://github.com/user-attachments/assets/a03327f8-abed-41cb-aaa7-fb6592269e8b" />

*Sanitization Enclave Topology*

