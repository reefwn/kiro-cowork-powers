# /research

Multi-source research on a customer question, product topic, or account-related inquiry. Synthesizes findings from all available sources with clear attribution.

## Usage

```
/research [question or topic]
```

## Workflow

### 1. Parse the Research Request

Identify what type of research is needed:
- **Customer question**: Something a customer has asked that needs an answer
- **Issue investigation**: Background on a reported problem
- **Account context**: History with a specific customer
- **Topic research**: General topic relevant to support work

### 2. Search Available Sources

Search in priority order, adapting to what is connected:

**Tier 1 — Internal Documentation (highest confidence):**
- ~~knowledge base: product docs, runbooks, FAQs
- ~~cloud storage: internal documents, specs, guides
- ~~CRM notes: previous answers, account context

**Tier 2 — Team Communications:**
- ~~chat: relevant channels, teammate discussions
- ~~email: previous correspondence on this topic
- ~~support platform: check if this has been asked/resolved before

**Tier 3 — External Sources:**
- Web search: official documentation, blog posts, community forums

### 3. Synthesize Findings

```
## Research: [Question/Topic]

### Answer
[Clear, direct answer — lead with the bottom line]

**Confidence:** [High / Medium / Low]
[Explain what drives the confidence level]

### Key Findings

**From [Source 1]:**
- [Finding with specific detail]

**From [Source 2]:**
- [Finding with specific detail]

### Context & Nuance
[Any caveats, edge cases, or additional context]

### Sources
1. [Source name/link] — [what it contributed]

### Gaps & Unknowns
- [What couldn't be confirmed]
- [What might need verification from a subject matter expert]

### Recommended Next Steps
- [Action if the answer needs to go to a customer]
- [Who to consult for verification if needed]
```

### 4. Handle Insufficient Sources

If no connected sources yield results:
- Perform web research on the topic
- Ask the user for internal context
- Be transparent about limitations

### 5. Customer-Facing Considerations

If the research is to answer a customer question:
- Flag if the answer involves product roadmap, pricing, legal, or security topics that may need review
- Note if the answer differs from what may have been communicated previously
- Offer to draft the customer response

### 6. Knowledge Capture

After research is complete, suggest capturing the knowledge:
- "Should I save these findings to your knowledge base for future reference?"
- "Want me to create a FAQ entry based on this research?"
