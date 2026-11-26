# UK VAT Identifier Discovery

## Project Overview

This project investigates methods for discovering UK company VAT registration numbers through publicly available sources.

The research combines manual investigation of company websites and public records with a Python-based proof of concept developed in Google Colab.

## Research Objectives

- Identify public sources that may contain UK VAT identifiers.
- Evaluate source accessibility, reliability and usefulness.
- Test automated extraction of potential VAT identifiers.
- Understand the limitations of public data and automated discovery.
- Assess the feasibility of scaling the process.

## Proof of Concept

A Python script was developed to extract potential UK VAT identifiers from publicly accessible webpage text using regular expressions.

The automated tests covered:
- Tesco PLC
- Sainsbury's Supermarkets Ltd
- BT Group
- National Express Limited

## Preliminary Results

- Companies investigated: 4
- VAT identifiers discovered through the investigated public sources: 2
- VAT identifiers reported as valid following manual HMRC checks: 2
- Observed discovery rate: 50%

These results are preliminary and are based on a small, non-random sample. They should not be interpreted as representative of all UK companies.

## Project Files

- `research/README.md` – detailed research, methodology, findings and limitations.
- `uk_vat_discovery.ipynb` – Python proof of concept and automated tests.
- `uk_vat_research_results.csv` – company-level research results.
- `automated_source_test_results.csv` – automated source testing results.

## Key Conclusion

Public company websites can provide useful VAT identification information, but availability varies significantly between companies. Automated extraction can identify potential VAT numbers, while independent validation and careful entity matching remain essential.

The project demonstrates that VAT identifier discovery is possible through public sources, but a scalable solution would require multiple data sources, validation procedures and ongoing quality controls.
