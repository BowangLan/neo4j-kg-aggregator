# Introduction

## Problem

- Given large list of text, if you want to extract information from it and construct a knowledge graph, one thing you have to consider is the schema of the knowledge graph.
- The schema must be consistent. Therefore, we specify the schema directly in the prompt, asking LLM to extract knowledge graph according to our specified schema.
- However, one may not have sufficient knowledge to build the complete schema in the first place. Therefore, a schema discovery phase is necessary.

## Solution

During schema discovery, each text item is passed to LLM with a specific prompt. A schema variable is created to store the current schema, and will be passed to the prompt before each LLM query, and will be updated according to the new schema returned by the LLM after each query.

The entire operation acts like a reduce function, where the aggregate variable is the schema, and the function that is executed for each item is the LLM query.
