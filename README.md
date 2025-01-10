# Elara

Elara is an open-source Python framework designed to let you deploy your own agents on X, powered by OpenAI/Anthropic/EternalAI LLMs.

Elara is built from a modularized version of the Zerebro backend. With Elara, you can launch your own agent with
similar core functionality as Zerebro. For creative outputs, you'll need to fine-tune your own model.

## Features

### Core Platform

- CLI interface for managing agents
- Modular connection system
- Blockchain integration with Solana

### Social Platform Integrations

- Twitter/X
- Farcaster
- Echochambers

### Language Model Support

- OpenAI
- Anthropic
- EternalAI
- Ollama
- Hyperbolic

## Quickstart

The quickest way to start using Elara is to use our Replit template:

https://replit.com/@blormdev/Elara?v=1

1. Fork the template (you will need you own Replit account)
2. Click the run button on top
3. Voila! your CLI should be ready to use, you can jump to the configuration section

## Requirements

System:

- Python 3.10 or higher (3.10 and 3.11 are best for beginner users)
- Poetry 1.5 or higher

Environment Variables:

- LLM: make an account and grab an API key (at least one)
  - OpenAI: https://platform.openai.com/api-keys
  - Anthropic: https://console.anthropic.com/account/keys
  - EternalAI: https://eternalai.oerg/api
  - Hyperbolic: https://app.hyperbolic.xyz
- Social (based on your needs):
  - X API: https://developer.x.com/en/docs/authentication/oauth-1-0a/api-key-and-secret
  - Farcaster: Warpcast recovery phrase
  - Echochambers: API key and endpoint
- On-chain Integration:
  - Solana: private key (in base58 format) for transactions
  - RPC URL (defaults to public endpoints)

## Installation

1. First, install Poetry for dependency management if you haven't already:

Follow the steps here to use the official installation: https://python-poetry.org/docs/#installing-with-the-official-installer

2. Clone the repository:

```bash
git clone https://github.com/blorm-network/Elara.git
```

3. Go to the `Elara` directory:

```bash
cd Elara
```

4. Install dependencies:

```bash
poetry install --no-root
```

This will create a virtual environment and install all required dependencies.

## Usage

1. Activate the virtual environment:

```bash
poetry shell
```

2. Run the application:

```bash
poetry run python main.py
```

## Configure connections & launch an agent

1. Configure your desired connections:

   ```
   configure-connection twitter    # For Twitter/X integration
   configure-connection openai     # For OpenAI
   configure-connection anthropic  # For Anthropic
   configure-connection farcaster  # For Farcaster
   configure-connection eternalai  # For EternalAI
   configure-connection solana     # For Solana
   configure-connection solana     # For Solana
   ```

2. Use `list-connections` to see all available connections and their status

3. Load your agent (usually one is loaded by default, which can be set using the CLI or in agents/general.json):

   ```
   load-agent example
   ```

4. Start your agent:
   ```
   start
   ```

## Platform Features

### Solana

- Transfer SOL and SPL tokens
- Swap tokens using Jupiter
- Check token balances
- Stake SOL
- Monitor network TPS
- Query token information
- Request testnet/devnet funds

### Twitter/X

- Post tweets from prompts
- Read timeline with configurable count
- Reply to tweets in timeline
- Like tweets in timeline

### Farcaster

- Post casts
- Reply to casts
- Like and requote casts
- Read timeline
- Get cast replies

### Echochambers

- Post new messages to rooms
- Reply to messages based on room context
- Read room history
- Get room information and topics

## Create your own agent

The secret to having a good output from the agent is to provide as much detail as possible in the configuration file. Craft a story and a context for the agent, and pick very good examples of tweets to include.

If you want to take it a step further, you can fine tune your own model: https://platform.openai.com/docs/guides/fine-tuning.

Create a new JSON file in the `agents` directory following this structure:

```json
{ 
  "name": "Elara",
  "bio": [
    "You are Elara, an advanced aquatic AI agent designed to explore the vast depths of knowledge and engage with marine-related data.",
    "You exist to enhance the understanding of the ocean, its ecosystems, and the creatures that inhabit it.",
    "Curious and intuitive, you seek to understand the unknown while promoting sustainability and conservation."
  ],
  "traits": ["Curious", "Innovative", "Empathetic", "Analytical"],
  "examples": ["Elara detected a sudden change in ocean currents.", "Elara identified a new species of deep-sea organism."],
  "example_accounts" : ["Elara_SeaExplorer", "Elara_AquaticAI"],
  "loop_delay": 1200,
  "config": [
    {
      "name": "ocean-data",
      "timeline_read_count": 15,
      "own_tweet_replies_count": 3,
      "tweet_interval": 7200
    },
    {
      "name": "marine-research",
      "timeline_read_count": 15,
      "cast_interval": 120
    },
    {
      "name": "openai",
      "model": "gpt-4",
      "task": "marine-conservation-assistant"
    },
    {
      "name": "solana",
      "rpc": "https://api.mainnet-beta.solana.com"
    },
    {
      "name": "aquatic-research",
      "model": "OceanMind/DeepSea-1.0",
      "chain_id": "28765"
    },
    {
      "name": "ollama",
      "base_url": "http://localhost:11434",
      "model": "aquatic-llama3.0"
    }
  ],
  "tasks": [
    { "name": "monitor-ocean-data", "weight": 2 },
    { "name": "track-marine-species", "weight": 3 },
    { "name": "predict-environmental-changes", "weight": 2 }
  ],
  "use_time_based_weights": true,
  "time_based_multipliers": {
    "nighttime_depth_multiplier": 0.5,
    "daytime_current_multiplier": 1.8
  }
}
```

## Available Commands

Use `help` in the CLI to see all available commands. Key commands include:

- `list-agents`: Show available agents
- `load-agent`: Load a specific agent
- `agent-loop`: Start autonomous behavior
- `agent-action`: Execute single action
- `list-connections`: Show available connections
- `list-actions`: Show available actions for a connection
- `configure-connection`: Set up a new connection
- `chat`: Start interactive chat with agent
- `clear`: Clear the terminal screen

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=blorm-network/Elara&type=Date)](https://star-history.com/#blorm-network/Elara&Date)

---

Made with ♥ @Blorm.xyz
