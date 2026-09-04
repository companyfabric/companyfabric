# CompanyFabric

[CompanyFabric](https://companyfabric.com/) is a developer-focused AI gateway
that provides one API for working with models from multiple providers. The
service is designed to make it easy to add AI capabilities to products,
internal tools, and agent workflows without integrating every provider
separately.

## Features

- **One API key for many models**: Access models from providers such as
  Anthropic, OpenAI, Google, DeepSeek, and others through one integration.
- **OpenAI-compatible API**: Existing OpenAI SDK integrations can be moved to
  CompanyFabric by changing the API base URL and key.
- **Flexible model selection**: Choose a specific model or let CompanyFabric
  select a model that is best, fastest, or most cost-effective for a request.
- **Transparent metering**: See token usage and request costs, including cost
  information in API responses.
- **Budget controls**: Set spending limits for API keys to help prevent
  unexpected usage.
- **Bring your own key (BYOK)**: Use provider credentials managed by your
  organization with no additional CompanyFabric platform fee.
- **Playground**: Test prompts and compare models before adding an integration
  to an application.
- **Agent and workflow friendly**: Use the API with agent frameworks,
  automation tools, and multimodal jobs for image, audio, and video workloads.

## How it works

1. **Create an account** at [companyfabric.com](https://companyfabric.com/)
   and create an API key. New accounts receive starter credits to try the
   service.
2. **Point your client at CompanyFabric** using
   `https://api.companyfabric.com/v1` as the API base URL.
3. **Send a normal OpenAI-compatible request**, selecting a model such as
   `companyfabric/auto` or a model from the [model library](https://companyfabric.com/models).
4. **Inspect usage and cost** in the response and monitor your balance and
   budget limits from the dashboard.

## Pricing

CompanyFabric uses usage-based pricing rather than a required subscription:

- Prepay a balance and use it across supported models.
- The price depends on the model and the amount of usage.
- The playground and dashboard show current model rates and estimated request
  costs before you run a request.
- BYOK usage has a **0% CompanyFabric platform fee**; the underlying provider's
  pricing still applies.
- Starter credits are available for new accounts.

Rates can change as providers update their pricing. See the
[CompanyFabric website](https://companyfabric.com/) and dashboard for current
model prices.

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

Keep API keys in environment variables or a secret manager; do not commit
them to source control.

## Documentation and integrations

- [Documentation](https://companyfabric.com/docs)
- [Quickstart](https://companyfabric.com/docs/quickstart)
- [Model library](https://companyfabric.com/models)
- [CompanyFabric website](https://companyfabric.com/)

The API can be used with the OpenAI SDK, cURL, Python, LangChain, the Vercel
AI SDK, Claude Code, n8n, and other clients that support an OpenAI-compatible
endpoint. Consult the documentation for authentication, supported models,
usage reporting, budget configuration, and asynchronous jobs.

## Repository

This repository contains the source for the
[companyfabric.com website](https://companyfabric.com/).

## License

Licensed under the [Apache License 2.0](LICENSE).
