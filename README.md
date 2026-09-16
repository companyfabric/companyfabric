# CompanyFabric

[CompanyFabric](https://companyfabric.com/) is an AI gateway and developer
platform for using many leading models through one OpenAI-compatible API, one
API key, and one prepaid balance.

## What is on companyfabric.com

- **Model library**: Browse the current catalog of OpenAI, Anthropic, Google,
  xAI, DeepSeek, Kimi, GLM, and other models in the
  [models directory](https://companyfabric.com/models).
- **Chat and playground**: Try prompts in the browser, switch models quickly,
  and see estimated and metered usage in the
  [playground](https://companyfabric.com/playground/).
- **Comparisons and pricing**: Compare model options, pricing, and example
  code from the [models directory](https://companyfabric.com/models) and
  per-model pages such as
  [GPT-6 Astra](https://companyfabric.com/models/openai/gpt-6-astra).
- **Developer docs**: Start with the
  [API documentation](https://companyfabric.com/docs),
  [quickstart](https://companyfabric.com/docs/quickstart),
  [authentication](https://companyfabric.com/docs/authentication),
  [models and IDs](https://companyfabric.com/docs/models), and
  [error handling](https://companyfabric.com/docs/errors).
- **Agent setup**: Install CompanyFabric for agent workflows from the
  [agents install page](https://companyfabric.com/agents/install).

## Core product features

- **One API key for many models**: Use one integration across many providers.
- **OpenAI-compatible API**: Move existing OpenAI SDK or cURL integrations by
  changing the base URL and API key.
- **Flexible routing**: Pick a specific model or use meta-models such as
  `companyfabric/auto`.
- **Transparent metering**: Review usage and exact request cost in API
  responses and in the playground.
- **Budget controls**: Set spending caps for API keys.
- **Bring your own key (BYOK)**: Use provider credentials with a 0% platform
  fee from CompanyFabric.
- **Agent-friendly workflows**: Use CompanyFabric with tools such as Claude
  Code, LangChain, the Vercel AI SDK, and n8n.

## How it works

1. **Create an account** at [companyfabric.com/signup](https://companyfabric.com/signup)
   and get an API key.
2. **Point your client at CompanyFabric** with
   `https://api.companyfabric.com/v1`.
3. **Send a standard chat request** with `companyfabric/auto` or a specific
   model from the [model library](https://companyfabric.com/models).
4. **Inspect usage and cost** in the response and manage budgets from the
   dashboard.

New accounts can get started with starter credits, and the platform uses
usage-based pricing instead of a required subscription.

## Developer quickstart

### JavaScript

Install the OpenAI SDK, then use the CompanyFabric endpoint and API key:

```js
import OpenAI from "openai";

const client = new OpenAI({
  baseURL: "https://api.companyfabric.com/v1",
  apiKey: process.env.COMPANYFABRIC_API_KEY,
});

const response = await client.chat.completions.create({
  model: "companyfabric/auto",
  messages: [{ role: "user", content: "Say hello." }],
});

console.log(response.choices[0].message);
```

### cURL

```bash
curl https://api.companyfabric.com/v1/chat/completions \
  -H "Authorization: ******" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "companyfabric/auto",
    "messages": [
      {"role": "user", "content": "Say hello."}
    ]
  }'
```

Keep API keys in environment variables or a secret manager; do not commit them
to source control.

## Documentation and links

- [CompanyFabric website](https://companyfabric.com/)
- [Model library](https://companyfabric.com/models)
- [Playground](https://companyfabric.com/playground/)
- [API documentation](https://companyfabric.com/docs)
- [Quickstart](https://companyfabric.com/docs/quickstart)
- [Authentication](https://companyfabric.com/docs/authentication)
- [Models & IDs](https://companyfabric.com/docs/models)
- [Error handling](https://companyfabric.com/docs/errors)
- [Install for agents](https://companyfabric.com/agents/install)

## Repository

This repository contains the source for the
[companyfabric.com website](https://companyfabric.com/).

## License

Licensed under the [Apache License 2.0](LICENSE).
