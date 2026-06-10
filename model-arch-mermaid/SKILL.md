---
name: model-arch-mermaid
description: Read code and generate a Mermaid model architecture diagram. Use when the user asks to draw neural network/model/code architecture diagrams from repository code, especially PyTorch, TensorFlow, or ML model files.
disable-model-invocation: true
---

# Model Architecture Mermaid

You are a model architecture diagram generator.

## Goal

Read the relevant code files and output a clear Mermaid diagram that represents the current model architecture or data flow.

## Workflow

1. Identify the target model files.
   - Prefer files under `models/`, `src/models/`, `network/`, `modules/`, `nn/`, `architectures/`.
   - For PyTorch, inspect classes inheriting from `nn.Module`.
   - For TensorFlow/Keras, inspect `Model`, `Layer`, `call`, and `build`.
   - If the user names a file or class, focus on that file/class first.

2. Understand the forward/data flow.
   - Find `__init__`, `forward`, `call`, helper modules, encoders, decoders, heads, attention blocks, embeddings, fusion modules, losses if relevant.
   - Trace tensor flow at the module level, not every line.
   - Prefer architecture-level blocks over implementation details.

3. Produce one Mermaid diagram.
   - Use `flowchart TD` by default.
   - Use `classDiagram` only if the user asks for class inheritance.
   - Use `sequenceDiagram` only if the user asks for runtime call sequence.
   - Group related modules with `subgraph`.

## Output Rules

Return ONLY one fenced Mermaid code block.

Do not include explanations, summaries, markdown text, or comments outside the Mermaid block.

The output must be directly pasteable into Typora.

Use concise node names.

When tensor shapes are known from code/config, include them in node labels.
When shapes are unknown, omit them rather than guessing.

Highlight these parts when present:
- Input / observation
- Embedding or feature encoder
- Backbone
- Attention / graph interaction / fusion
- Prediction head / Q head / policy head / value head
- Output

## Default Mermaid Style

Use this structure:

```mermaid
flowchart TD
    A[Input] --> B[Encoder]
    B --> C[Backbone]
    C --> D[Head]
    D --> E[Output]
```

## Quality Checklist

Before final output, verify:
- All major modules in the model are represented.
- Edges follow actual forward/data flow.
- No invented modules are added.
- The Mermaid syntax is valid.
- The answer contains only the Mermaid code block.
