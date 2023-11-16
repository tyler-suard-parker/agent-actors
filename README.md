# Agent Actors: Plan-Do-Check-Adjust with Parallelized LLM Agent Trees

Create your own trees of AI agents that work towards a common objective. Together, let's explore the potential of Agent Actors and inspire the LLM community to delve deeper into this exciting realm of possibilities!

**Watch this 2-minute demo walkthrough — https://www.loom.com/share/8e60585f069c4a9f8ac9f01204b41704**

Here's a sample generated execution plan:

![Execution Plan for Parallel LLM Application](https://user-images.githubusercontent.com/1880797/234443312-8a006245-25bc-47c0-b35b-2c623ed2e300.png)

## Key Features

* **Time Weighted Long-Term Memory** using `langchain.retrievers.TimeWeightedVectoreStoreRetriever`
* **Synthesized Working Memory**: An agent draws insights from and synthesizes their relevant memories into a "working memory" of 1–12 items for use with zero-shot prompts.
* Implements the **Plan-Do-Check-Adjust (PDCA)** operational framework for continuous improvement.
* **Automatic Planning and Distribution of Tasks to Agents** Our `ParentAgent` class plans tasks for its children to do and distributes them to be completed in parallel.
* **Parallel Execution of Agents** `ChildAgent`s work in parallel to Do and Check their results. Before running, they wait for all task dependencies to be resolved and inject that into their context.
* **Create your own trees of autonomous AI agents** You can nest `ParentAgent`s under `ParentAgent`s, or comingle them with `ChildAgent`s. Use your own vector store, retriever, or embedding function with our `ParentAgent` and `ChildAgent` classes. See how easy it is in [`test_system.py`](./agent_actors/test_system.py).

## What will you build?

0. Terminating auto-GPTs that converges across successive runs
1. Your own research and reporting teams of agents
2. Simulation-driven organizational behaviour research
3. Create a developer *team* of AutoGPTs that code for you together

## Limitations

1. Proof of Concept, not production ready
2. We've only tested used GPT3.5

## Installation

Requires Python: ^3.10

Install through your choice of package manager:

```bash
poetry add git+https://github.com/shaman-ai/agent-actors.git
git clone https://github.com/shaman-ai/agent-actors
cd agent-actors
poetry install --with dev --with typing
```

## Learn Agent Actors in 5 minutes

```python
from agent_actors import (
  Agent, # subclass and replace with your own `run` method
  ChildAgent, # Do and Check
  ParentAgent, # Plan and Adjust
  ConsolePrettyPrinter, # Helpful for printing JSON task outputs, pass as a handler to CallbackManager
)
```

**Read [`test_system.py`](./agent_actors/test_system.py)!**

## Run Agent Actors

NOTE: You MUST include your OpenAI API Key (openai.com), your Wolfram Alpha API Key, and Serper API Key (Serper.dev) in your environment variables.

1. Modify [`test_system.py`](./agent_actors/test_system.py) to your own needs
2. Run `poetry run pytest -s -k 'test_system.py'`

You can also run all tests with `poetry run pytest`, but this may take a while to execute, and is likely to hit into API rate limits.

## Contribute to Agent Actors

Check out this diagram to understand how the system works: https://beta.plectica.com/maps/W26XSGD28

### Requests for Pull Requests

1. **Improved Agent Prompts**: Develop better prompts for the Plan, Do, Check, and Adjust chains
2. **Visualization Tooling**: Develop an interface for exploring first, then composing, an execution tree of Agent Actors, allowing researchers to better understand and visualize the interaction between the supervisory agent and worker agents.
3. **Evaluation Data**: Understanding how this performs in different contexts is key to developing a better AGI architecture.
4. **Unlock Talking to Agents**: The dialogue functions are there, and we're looking for help on how we can "talk" to these agents from another, say, IPython, to get a look into their state.
5. **Unlock Inter-Agent Communication**: What happens if agents can talk to each other, not just return results to their parents and write memories to the global store?

## License (LGPLv3)

Our project is licensed under the [GNU Lesser General Public License v3 (LGPLv3)](https://www.gnu.org/licenses/lgpl-3.0.en.html). This provides a balance between open-source values and flexibility for developers. Key points include:

- You can use this as a library in your closed-source software.
- Modifications to our library must be released under an LGPLv3 license, the easiest way to do this is to submit a PR to this project.
- Contributors benefit from patent protection.

For the full legal text, see the [LICENSE](./LICENSE) file.

## Gratefulness

We extend our gratitude to the contributors of the Python packages [langchain](https://langchain.com) and [ray](https://ray.io), without which this wouldn't be possible. We extend our gratitude to the amazing researchers who wrote Generative Simulacra [TODO], ReAct [TODO], and Jeremy Howard [TODO] and FastAI, without which this wouldn't be possible. And to BabyAGI and AutoGPT for inspiring us.

## Citation

Citation
Please cite the repo if you use the data or code in this repo.

```
@misc{agentactors,
  author = {Shaman AI},
  title = {Agent Actors: Plan-Do-Check-Adjust with Parallelized LLM Agent Trees},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/shaman-ai/agent-actors}},
}
```
