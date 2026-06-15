---
name: auto-research
description: Systematic academic literature search using deterministic tools, cross-validating sources before storage. Use when researching topics, finding papers, or user mentions "search papers", "find literature", "research [topic]".
---

# Auto-Research - Academic Literature Search

## Core Principle

**NO HALLUCINATION**: I will NEVER generate paper titles, authors, or citations. I will only use deterministic tools to query real academic databases.

## When to Use

- Starting literature review
- Finding sources for specific claims
- Exploring a research domain
- User says "search papers", "find literature", "research X"

## Workflow

### 1. Query Construction
Convert your research question into search queries for academic databases:
- Core terms + synonyms
- Time filters (default: last 5 years)
- Document type filters (journal, conference, review)

### 2. Database Search
Query deterministic tools in priority order:
1. **Google Scholar** - Broad coverage
2. **Semantic Scholar** - AI-enhanced search
3. **arXiv** - Preprints (for latest)
4. **PubMed/IEEE/ACM** - Domain-specific

### 3. Source Evaluation
Prioritize based on:
- Journal/Conference reputation (Q1, Tier 1)
- Citation count (≥10 for recent papers)
- Peer-reviewed status
- Relevance to query

### 4. Storage
Save to `_research_cache/[topic]-[date].md`:

```markdown
# [Topic] Literature Research

**Query**: [search terms]
**Date**: [YYYY-MM-DD]
**Sources**: Scholar, Semantic Scholar, arXiv

## Core Papers

### 1. [Paper Title]
- **Authors**: [list]
- **Venue**: [journal/conference, year]
- **Citations**: [count]
- **DOI/URL**: [link]
- **Key findings**: [summary]

## Research Gaps
- [Identified gaps]

## Next Steps
- [Suggested searches]
```

## Search Strategy

### Effective Queries
- `"machine learning" AND interpretability AND 2020..2024`
- `"attention mechanism" survey OR review`
- Author search: `author:"Geoffrey Hinton"`

### Time-Based Filters
- Recent (0-2 years): Emerging trends
- Mid-term (2-5 years): Established methods
- Classic (5+ years): Foundational papers

## Anti-Hallucination Rules

1. **NEVER** generate paper metadata
2. **ALWAYS** cite tool results
3. **VERIFICATION REQUIRED**: If uncertain, say "I couldn't find..."
4. **CROSS-CHECK**: Run `/auto-evaluate` on critical sources

## Example

```
You: Find papers on transformer interpretability

Me: Searching Google Scholar and Semantic Scholar...

    Found 8 relevant papers from 2022-2024:
    
    1. "Understanding Transformers via Circuit...
       - Vaswani et al., ICLR 2024 (42 citations)
       - [Link]
    
    [Results saved to _research_cache/transformer-interpretability-2024-06-15.md]
    
    Run /auto-evaluate to verify these sources.
```

## See Also

- `/auto-evaluate` - Verify source accuracy