# UK VAT Identifier Discovery
## 1. Project Overview
This project investigates whether UK company VAT numbers can be discovered using publicly available online sources.
The objective is to identify reliable sources, evaluate their coverage and usefulness, and determine whether a practical process can be developed to discover VAT numbers for UK companies.

## 2. Research Objectives
The research aims to:
- Identify publicly available sources that may contain UK company VAT numbers.
- Evaluate the accessibility, reliability and coverage of each source.
- Understand the limitations of available verification methods.
- Identify possible approaches for discovering VAT numbers.
- Assess the feasibility and potential costs of building a scalable solution.

## 3. Research Methodology
Each potential source will be evaluated based on:
- Information available.
- Accessibility and technical limitations.
- Data coverage.
- Reliability and accuracy.
- Potential for automation.
- Legal and practical limitations.

## 4. Sources Investigated
This section will document each source investigated, the research process, observations and results.

## 5. Findings and Limitations
This section will summarize the findings, including unsuccessful approaches, data gaps and limitations.

## 6. Conclusions
The final conclusions will assess whether UK company VAT identifier discovery is feasible and under what conditions.

## 7. Case Study: Tesco PLC
### Company identification
- Company name: Tesco PLC
- Companies House company number: 00445790
- Initial source: Companies House
### VAT number discovery
- Source: Tesco official website – General Terms & Conditions
- URL: https://www.tesco.com/shop/en-GB/zone/general-terms-and-conditions
- VAT number discovered: GB220430231
### VAT number validation
- Validation source: HMRC – Check a UK VAT number
- URL: https://www.tax.service.gov.uk/check-vat-number/enter-vat-details
- Validation result: Valid UK VAT number
- HMRC registered business name: TESCO PLC
- HMRC registered business address: Cirrus A, Shire Park, Kestrel Way, Welwyn Garden City, AL7 1GA, GB
- Validation date: 26 November 2026
### Conclusion
The Tesco case study demonstrates that a UK company's VAT identifier can be discovered through its official website and subsequently validated using HMRC's VAT checking service.
The HMRC result confirmed that VAT number 220430231 belongs to TESCO PLC. This also highlights the importance of matching VAT identifiers to the correct legal entity rather than assuming that all companies within the same corporate group share the same VAT registration.
### Limitation
This is one successful test case. Further testing across companies of different sizes and sectors is required before drawing conclusions about discovery coverage or scalability.

## 8. Comparative Testing of Public Sources
Four UK companies from different sectors were selected to test whether VAT identifiers could be discovered through publicly available company websites.
| Company | Sector | Sources Investigated | VAT ID Discovered | HMRC Validation |
|---|---|---|---|---|
| Tesco PLC | Retail | Companies House, official website – General Terms & Conditions | Yes | Valid |
| Sainsbury's Supermarkets Ltd | Retail | Official website – Terms & Conditions | Yes | Valid |
| BT Group | Telecommunications | BT Business Terms & Conditions, Supplier Information | No | Not applicable |
| National Express Limited | Transport | Terms & Conditions, Contact page | No | Not applicable |

### 8.1 Tesco PLC
- Company number: 00445790
- VAT number discovered: GB220430231
- Discovery source: https://www.tesco.com/shop/en-GB/zone/general-terms-and-conditions
- Validation source: HMRC VAT Checker
- Result: Valid
- HMRC confirmed business name: TESCO PLC

### 8.2 Sainsbury's Supermarkets Ltd
- Company number: 03261722
- VAT number discovered: GB660454836
- Discovery source: https://help.sainsburys.co.uk/help/terms-and-conditions/terms-conditions
- Validation source: HMRC VAT Checker
- Result: Valid
- HMRC confirmed business name: SAINSBURY'S SUPERMARKETS LTD

### 8.3 BT Group
- Sector: Telecommunications
- Sources investigated:
  - https://business.bt.com/terms-and-conditions/
  - https://www.bt.com/about/selling-to-bt/how-to-get-paid/bt-uk-business
- VAT identifier discovered: No
- Observation: BT states that the relevant entity and its VAT registration number are provided on the purchase order issued by BT.
- Limitation: The investigated pages did not provide a specific VAT identifier or a company registration number.

### 8.4 National Express Limited
- Company number: 00232767
- Sources investigated:
  - https://www.nationalexpress.com/en/help/terms-conditions
  - https://www.nationalexpress.com/en/help/contact
- VAT identifier discovered: No
- Observation: The investigated pages did not reveal a VAT registration number.
- Limitation: The absence of a VAT number on these pages does not mean that the company is not VAT registered.

## 9. Preliminary Findings
The initial tests demonstrate that official company websites can be useful sources for discovering UK VAT identifiers.
Two companies out of the four tested had VAT identifiers publicly available in the investigated sources. Both identifiers were subsequently confirmed as valid through HMRC.
The other two cases illustrate an important limitation: VAT identifiers are not necessarily published on general terms and conditions or customer support pages. In the BT case, the relevant VAT registration number is associated with the specific BT entity issuing a purchase order.

### 9.1 Initial Results
- Companies tested: 4
- VAT identifiers discovered: 2
- VAT identifiers successfully validated: 2
- Companies with no VAT identifier discovered in the investigated pages: 2
The observed discovery rate was 50% (2 out of 4 companies).
This result is preliminary and should not be interpreted as representative of the entire UK company population because the sample is small and was not randomly selected.

### 9.2 Key Limitations
- VAT identifiers may be published on different pages or documents depending on the company.
- Corporate groups may contain several legal entities with different VAT registrations.
- A company name or Companies House registration number cannot automatically be treated as a VAT identifier.
- HMRC validation confirms a candidate VAT number but does not discover unknown VAT numbers.
- Failure to find a VAT identifier on one or two public pages does not establish that the company has no VAT registration.

## 10. Automated Testing and Technical Results
A Python-based proof of concept was developed in Google Colab to extract potential UK VAT identifiers from publicly accessible web page text.

### 10.1 Automated Source Testing
| Source | HTTP Status | Characters Extracted | VAT Identifier Found |
|---|---:|---:|---|
| Tesco official website | 403 | 0 | No |
| Companies House | 200 | 2,210 | No |
| Sainsbury's official website | 200 | 53,803 | Yes |

The Tesco website returned HTTP 403, indicating that automated access was forbidden. This prevented the extraction process from accessing its page content.

Companies House was accessible, but the extracted company overview did not contain a VAT identifier.

Sainsbury's website returned accessible page text containing its VAT registration number.

### 10.2 Extraction Method
The proof of concept uses Python regular expressions to identify strings matching the expected UK VAT identifier format.
The extraction process identifies potential VAT number candidates. It does not independently establish whether a candidate is genuine or belongs to the company being investigated.

### 10.3 Technical Limitations
- Some websites restrict automated access.
- Page structure and dynamically loaded content can affect text extraction.
- A matching number format does not guarantee that the identifier is valid.
- Automated extraction must be followed by independent validation.
- The current implementation is a proof of concept and requires further testing before large-scale use.

### 10.4 Technical Conclusion
The automated tests demonstrate that Python can extract potential VAT identifiers from accessible website text. However, access restrictions and differences in website content limit the reliability of a fully automated discovery process.
