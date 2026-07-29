# LLM Wiki

**Status:** reference
**Last updated:** 2026-07-29

## Summary
A pattern by Andrej Karpathy for building personal knowledge bases using LLMs. Instead of RAG, the LLM incrementally builds and maintains a persistent wiki.

## Three Layers
1. Raw sources — immutable source documents
2. The wiki — LLM-generated markdown files
3. The schema — Configuration telling LLM how to maintain the wiki

## Related
- [[9mem]] — Implementation of this pattern
