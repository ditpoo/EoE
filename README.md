<div align="center">
<h1>Ensemble of Experts (EoE) / Mesh of Experts (MeoE)</h1>
<p style="font-size: 1.5em; font-weight: bold;">Ditesh Poojari</p>
</div>

Ensemble of Experts (EoE) / Mesh of Experts (MeoE): A Conceptual Architecture for Long-Context Models.

The EoE / MeoE architecture is a scalable neural netwrok (transformers based/inspired) architecture that enables large (1–10 million and beyond) context windows using a distributed, sharded Mixture of Experts (MoE) approach.

This architecture represents a paradigm for handling extremely long contexts. With shared context that can act as independent shards of (mini) contexts, i.e Sub-global attention blocks or "sub-context experts" that can operate somewhat independently (as independent different sets of expert pathways) and then scale up or compose into a larger global attention (as full expert pathway operating on the entire context window).

This model represents a fundamental evolution of transformer architecture.

Using a shared, distributed context that’s sharded across chips, that can act as Independent shards of (mini) Contexts.

Only activating a subset of specialized subnetworks (experts) for each request,while accessing parts (shard) of the shared context acting like a mini-context or sub-context, based on requirement, relevance and complexity.

The long context is sharded and managed via parallelism, and with ability to handle concurrent requests simultaneously by independent different sets of expert pathways, while accessing parts of the shared context.

When needed, a full expert pathway and entire context window (with its multiple shards) can be used for one single request.

The architecture may use sub-context experts that process parts of the input independently but compose into a coherent global representation—kind of like sub-global attention blocks.

## This setup draws inspiration from:

    * MoE: Only a few parts of the model activate for a given input.
    * Sparse attention + parallelism: Efficient handling of very long sequences.
    * Modern hardware (gpu's/tpu's): High bandwidth, interconnected, with large memory.

## Key Characteristics

    * A global context window (1M–10M tokens) is sharded across multiple chips.
    * Experts access relevant shards dynamically.
    * Supports both sub-global processing and global coherence.
    * Experts operate in parallel, isolated execution pathways.
    * Each request uses its own subset of experts and parts of the context.

## It’s Sub-Quadratic or Even Linear:

    Traditional transformers have O(n²) time and memory complexity. EoE/MeoE avoids this:

    Resulting in:
        * O(n) or O(n·log n) runtime
        * Massive context lengths with tractable compute
        * Global semantic coherence without quadratic blowup

## Engineering Significance

    If implemented as hypothesized, this architecture would be a engineering achievement:

    With Following Achievements:
        * Solves Long-Context Modeling
        * Redefines Transformer Scalability
        * Paves the Road to AGI-like Systems

## Key Trade-offs & Challenges:

    * Latency from cross-chip attention and memory fetching.
    * Complexity of shared, sharded context window, routing and expert.
    * Coherence and consistency at sub-global and global level with shared (sharded) context window

## References

    Original twitter/x threads by author.

        * https://x.com/ditpoo/status/1923966380854157434
        * https://x.com/ditpoo/status/1924149753417527661


## Citation

```bibtex
@misc{ditpoo2025EoE/MeoE,
    title={Ensemble of Experts (EoE) / Mesh of Experts (MeoE): A Conceptual Architecture for Long-Context Models},
    author={Ditesh Poojari},
    publication={github github.com/ditpoo},
    howpublished = {\url{https://github.com/ditpoo/EoE}},
    year={2025}
}
```
