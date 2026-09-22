---
layout: ../../layouts/CaseStudy.astro
title: Evaluating an internal documentation assistant
category: Hewlett Packard Enterprise
summary: An evaluation scaffold for an existing RAG prototype, followed by work on document retrieval and the application’s backend structure.
role: Cloud Engineering Intern
period: June–September 2025
team: Four interns · Two mentoring engineers
tools: [Python, RAGAS, LangChain, LangGraph, Docling, Streamlit]
note: This was an internal company tool. Source code, documents, and product screenshots are not public.
---

## Starting with an existing prototype

At HPE, I worked with three other interns and two mentoring engineers on an internal question-answering tool for proprietary cloud documentation. A basic retrieval-augmented generation loop already existed, using LangChain, LangGraph, and Streamlit.

My initial focus was evaluation: building a way to examine the system’s retrieved context and generated answers, rather than relying only on individual demonstrations of the tool.

## My contribution

I built an evaluation scaffold using RAGAS. The work included synthetic test-set generation, reproducible benchmark runs, and a Gradio interface for exploring results. The framework examined measures including faithfulness, context precision, and retrieval quality, alongside the answers themselves.

This work sat between the retrieval pipeline and the people developing it. It provided a structured way to inspect behavior and compare runs as the system changed.

Later work focused on moving the application beyond its initial prototype structure. I contributed to refactoring toward an API-driven backend and improving document processing and retrieval using Docling. My work also included content-aware chunking and integration of Neo4j for graph-backed retrieval.

## The engineering focus

The project brought together two concerns: organizing an application so it could evolve, and evaluating whether its outputs were useful and grounded in the retrieved documentation. My contribution centered on the evaluation tooling and subsequent retrieval and backend work, within a larger team effort.
