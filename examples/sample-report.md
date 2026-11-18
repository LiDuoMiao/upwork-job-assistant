# Upwork Screening Report · Anonymized Sample

> This sample comes from an actual screening run. It retains the original counts, scores, and earnings estimates. Job titles have been generalized. Posting links, application records, and personal experience claims are omitted. Job activity and fee assumptions reflect the original run.

## Run summary

The search returned about 130 results and 70 distinct jobs, mostly posted in the preceding two days. Eight new jobs were checked in detail, and five prior candidates were rechecked. The run produced one recommendation and one conditional recommendation.

## Recommended

| Score | Job | Client location | Budget | Estimated effort | Gross / after platform fees | Competition / Connects | Rationale |
|---:|---|---|---:|---|---|---|---|
| 79 | Payment recording and email receipt automation | United States | $250 fixed | 7–10 hours | $250 / $212.50–250 | Proposal count unknown. No interviews, offers, or hires at the time. 11 Connects | One workflow with clear acceptance criteria. Effective rate about $25–35.7/hour. Medium confidence in the estimate |

## Conditional recommendations

| Score | Job | Client location | Budget | Estimated effort | Gross / after platform fees | Competition / Connects | What to confirm or accept |
|---:|---|---|---:|---|---|---|---|
| 75 | PDF document Q&A assistant | Australia, as shown on the account | $500 fixed | 20–28 hours | $500 / $425–500 | 50+ proposals, three candidates interviewing. 11 Connects | Confirm that PDF parsing, citations, evaluation, and deployment fit within five days. If substantial OCR is needed, narrow the first release or re-estimate. The application costs 11 Connects, and the client may not reply. Low confidence in the estimate |

The original estimates used a 0%–15% platform fee and excluded taxes, currency conversion, and withdrawal costs. Confidence reflects the quality of the budget, scope, and effort information.

## Prior recommendations

All five prior jobs were still open when rechecked. Two had previously been recommended, and three were conditional. This sample shows the aggregate recheck results.

## Job analysis

### Payment recording and email receipt automation

**Project overview** — The client needs an importable n8n workflow that receives a payment webhook, validates fields, writes to Airtable, and sends an HTML receipt. It should handle repeated events and basic failures. Deliverables include the workflow JSON and setup notes.

- **Fit and score** — The job needs API integration and workflow automation. Before applying, confirm you can set up n8n, Airtable, and the email service. Technical fit 28/35, delivery confidence 17/20, budget value 12/15, client quality 10/15, competition and timing 8/10, scope clarity 4/5. Total 79.
- **Client and hiring activity** — The client had a new account with no visible hiring history. The job was open with no interviews, offers, or hires. Proposal count and payment verification were unknown.
- **Quote and earnings** — At the posted budget of $250 and 7–10 hours of work, the effective rate is about $25–35.7/hour, with estimated earnings of $212.50–250 after the platform fee. Quote gateway integration, extra receipt templates, or ongoing maintenance separately.
- **Application decision** — Worth considering. The job has a defined scope and the cost of 11 Connects is reasonable for this contract. Confirm the available tools can support every step.

#### Proposal draft

I would first check which webhook field uniquely identifies a payment, then make the Airtable write and the email step independently verifiable. When the same payment arrives twice, the workflow should recognize the existing record and avoid sending a second receipt. Before handing over the importable n8n workflow and setup notes, I would test valid events, missing fields, and duplicate deliveries.

Which payment system sends the webhook, and do you already have an email service set up? My fixed quote for the single workflow described is $250.

### PDF document Q&A assistant

**Project overview** — The client wants an internal assistant for several dozen product documents, procedures, and FAQs. It should extract text from PDFs, retrieve relevant passages, cite the file and page, and acknowledge when evidence is insufficient. The first version includes an API, a simple chat interface, Docker deployment, an evaluation summary, and a demo. The target is four to five days.

- **Fit and score** — The job needs PDF parsing, retrieval with citations, and application deployment. Check what share of the files are scanned, whether page-level citations are feasible, and whether the full scope fits the schedule. Technical fit 33/35, delivery confidence 12/20, budget value 8/15, client quality 10/15, competition and timing 7/10, scope clarity 5/5. Total 75.
- **Client and hiring activity** — The job was open with 50+ proposals and three candidates interviewing. The client account showed no hiring history.
- **Quote and earnings** — At $500 fixed and 20–28 hours, the effective rate is about $17.9–25/hour, with estimated earnings of $425–500 after the platform fee. Confidence is low because the share of scanned files, deployment environment, and acceptance questions were unknown.
- **What to confirm or accept** — Confirm what can be delivered in five days. If the PDFs are readable and the interface stays simple, propose the first release at $500. Extensive OCR or additional access controls require a revised scope and timeline. The application costs 11 Connects, and the client may not reply.

#### Proposal draft

I would start with a representative set of PDFs to check that text and page numbers survive extraction. Then I would use real questions to verify that retrieval points to the right pages before connecting it to the chat UI. I would also test questions the documents cannot answer to see whether the assistant makes the lack of evidence clear.

How many documents are scanned, and can you share a few typical questions and the target deployment environment? If most documents can be extracted directly and the UI stays simple, $500 is a workable budget for the first version. Extensive OCR or complex permissions would need a separate estimate.

## Screening appendix

| Job | Reason for skipping |
|---|---|
| E-commerce workflow automation | The only opening had already been filled. The application cost 27 Connects |
| AI SaaS product development | The role centered on coordination, light technical support, and client communication. Development tasks were unclear |
| Full-stack energy platform | The first release included a website, subscriptions, electronic agreements, administration, and AI reports. No budget was posted |

## Coverage

Some search and detail requests were interrupted. Retries recovered part of the results. Search pagination was limited, so the counts describe the results returned in this run.
