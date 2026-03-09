# Architectural Blueprint: [CORE-INTENT]

### 1. The Neural Partition
To prevent "OS Exhaustion," the system requires a tiered SSD partitioning strategy:
* **Zone 0 (Reflex):** Ultra-fast boot core for the Orchestrator.
* **Zone 1 (Lobe):** Model weights pinned to high-IOPS sectors.
* **Zone 2 (Synapse):** Vector Database for local, long-term memory.

### 2. The Direct Lane
Implementation requires **Zero-Copy DMA** paths. Data flows from **Zone 1** directly to the NPU Memory Tiles, skipping the CPU-managed RAM-copy cycle.

### 3. The Synaptic Bridge
A kernel-level file-watcher that translates changes in the `{CONTEXT_DATASET}` into neural tokens. 
* **Weighting:** Recent personal entries carry a weight of **0.9**, overriding base model knowledge (**0.2**) to ensure personal truth always wins.

### 4. Intent Orchestration
The system monitors hardware sensors (thermals, NPU load) and user inputs to switch between:
* **Concise Mode:** Logical/Logistical briefing.
* **Deep-Dive Mode:** High-parameter creative brainstorming.
* **Guardian Mode:** Proactive fatigue management and safety filtering.
