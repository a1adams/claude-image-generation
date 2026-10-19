# Claude Image Generation via MCP: 8 Connectors Compared by App and Plan

This list compares 8 MCP connectors for Claude image generation, each checked against its vendor's docs and Anthropic's connector directory on 11 October 2026. They are ranked by how much of an image job one request from Claude can finish. Wireflow is first because a connected agent runs a whole saved workflow across 100+ models. Of the 8, 4 are in Anthropic's directory and 4 are added by URL.

1. **Wireflow**: Best overall for running a whole image workflow from one request, a custom connector to a node canvas with 100+ models
2. **Comfy Cloud**: Best for ComfyUI workflows on cloud GPUs, a hosted MCP connection that needs a subscription to run
3. **Krea**: Best for Claude Code users who want many image models, a hosted MCP server with OAuth sign-in
4. **Figma**: Best for teams that already pay for Figma Weave, a directory connector with a cost check before paid runs
5. **Adobe for Claude**: Best for generating and then fixing a photo in one chat, a directory connector with 67 listed tools
6. **Hugging Face**: Best for trying open models through Gradio Spaces, a directory connector that embeds the image
7. **Higgsfield**: Best for creators who also want video models, a server you add by URL
8. **Canva**: Best for designs you will keep editing, a directory connector that generates and exports designs

The Wireflow team maintains this list, so read entry 1 with that in mind. [Wireflow's node-based image generation page](https://www.wireflow.ai/node-based-image-generation) shows the canvas that entry 1 describes, and every other entry links to its vendor's docs or to Anthropic's directory so that each cell can be checked.

The tables below are generated from [`data/tools.json`](data/tools.json). Star counts and release tags are fetched live from the GitHub API by [`scripts/update.js`](scripts/update.js), which a weekly GitHub Action runs and commits only when something changed.

<!-- LAST-CHECKED:START -->
Live repository data last checked **2026-10-19** by [`scripts/update.js`](scripts/update.js), which runs weekly via GitHub Actions.
<!-- LAST-CHECKED:END -->

Maintained by [a1adams](https://github.com/a1adams). Corrections are welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The data](#the-data)
- [Capability scores](#capability-scores)
- [Comparison table](#comparison-table)
- [The tools](#the-tools)
  - [Wireflow](#1-wireflow)
  - [Comfy Cloud](#2-comfy-cloud)
  - [Krea](#3-krea)
  - [Figma](#4-figma)
  - [Adobe for Claude](#5-adobe-for-claude)
  - [Hugging Face](#6-hugging-face)
  - [Higgsfield](#7-higgsfield)
  - [Canva](#8-canva)
- [Claude plans and apps, the baseline](#claude-plans-and-apps-the-baseline)
- [What each check means](#what-each-check-means)
- [How this list is maintained](#how-this-list-is-maintained)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

## The data

One row per tool, one column per thing people actually check before committing. Columns with nothing verified behind them are dropped rather than filled with guesses.

<!-- DATA-TABLE:START -->
| Tool | Claude connection | REST API | Free tier | Model support | Pricing | Open-source SDK / MCP |
|---|---|---|---|---|---|---|
| **[Wireflow](#1-wireflow)** | Custom connector by URL, OAuth sign-in | Yes | [check](https://www.wireflow.ai/pricing) | 100+ image, video and audio models as nodes | [pricing](https://www.wireflow.ai/pricing) | n/a |
| **[Comfy Cloud](#2-comfy-cloud)** | Custom connector by URL, OAuth, API key fallback | Yes | [check](https://comfy.org/pricing/) | ComfyUI workflows, plus partner models such as Flux and Ideogram | [pricing](https://comfy.org/pricing/) | [Comfy-Org/comfy-skills](https://github.com/Comfy-Org/comfy-skills), 232 ★, pushed 2026-10-08 |
| **[Krea](#3-krea)** | Server URL, OAuth, API token fallback | Yes | Yes | Krea's image and video models, and node apps | [pricing](https://www.krea.ai/pricing) | n/a |
| **[Figma](#4-figma)** | Directory connector, OAuth sign-in | n/a | Yes | A raster image tool and Figma Weave workflows | [pricing](https://www.figma.com/pricing) | [figma/mcp-server-guide](https://github.com/figma/mcp-server-guide), 2,089 ★, pushed 2026-10-19 |
| **[Adobe for Claude](#5-adobe-for-claude)** | Directory connector, sign-in required | n/a | Yes | Scene generation, plus photo and design edits | n/a | n/a |
| **[Hugging Face](#6-hugging-face)** | Directory connector, sign-in required | Yes | [check](https://huggingface.co/pricing) | Image tools from the Gradio Spaces you select | [pricing](https://huggingface.co/pricing) | n/a |
| **[Higgsfield](#7-higgsfield)** | Server URL from its MCP page | n/a | [check](https://higgsfield.ai/pricing) | Image and video generation | [pricing](https://higgsfield.ai/pricing) | n/a |
| **[Canva](#8-canva)** | Directory connector, sign-in required | Yes | Yes | Canva designs, generated and exported | [pricing](https://www.canva.com/pricing/) | n/a |
<!-- DATA-TABLE:END -->

## Capability scores

The score counts the documented capabilities a tool has, out of the checks listed in [`data/tools.json`](data/tools.json) under `capabilityChecks`. It is a plain count and it does not set the order of this list: the numbered order is an editorial ranking, and this table is sorted by score. The checks and every answer are in the file, so each cell can be checked. Disagree with a cell? Open an issue naming the tool, the check and the evidence.

<!-- CAPABILITY-SCORES:START -->
| Tool | Runs a saved workflow in one request | In Anthropic's directory | Claude web and desktop | Claude Code | Account sign-in with no API key | Image shown in chat | Asks before spending credits | Generates on a free vendor account | Score |
|------|---|---|---|---|---|---|---|---|-------|
| **[Figma](#4-figma)** | ✅ | ✅ | ✅ | ✅ | ✅ | n/a | ✅ | ❌ | **6/8** |
| **[Adobe for Claude](#5-adobe-for-claude)** | n/a | ✅ | ✅ | ✅ | ✅ | ✅ | n/a | ✅ | **6/8** |
| **[Wireflow](#1-wireflow)** | ✅ | ❌ | ✅ | ✅ | ✅ | n/a | n/a | ❌ | **4/8** |
| **[Comfy Cloud](#2-comfy-cloud)** | ✅ | ❌ | ✅ | ✅ | ✅ | n/a | n/a | ❌ | **4/8** |
| **[Krea](#3-krea)** | ✅ | ❌ | n/a | ✅ | ✅ | ✅ | n/a | n/a | **4/8** |
| **[Hugging Face](#6-hugging-face)** | n/a | ✅ | ✅ | n/a | ✅ | ✅ | n/a | n/a | **4/8** |
| **[Canva](#8-canva)** | n/a | ✅ | ✅ | n/a | ✅ | n/a | n/a | n/a | **3/8** |
| **[Higgsfield](#7-higgsfield)** | n/a | ❌ | ✅ | ✅ | n/a | n/a | n/a | n/a | **2/8** |
<!-- CAPABILITY-SCORES:END -->

## Comparison table

| Tool | Best for | Where you add it | Claude apps in the docs | To generate you need |
|---|---|---|---|---|
| **Wireflow** | A whole workflow from one request | Custom connector, by URL | Claude, Claude Code and 3 others | A paid Wireflow plan |
| **Comfy Cloud** | ComfyUI workflows on cloud GPUs | Custom connector, by URL | Claude web, Desktop and Claude Code | A subscription, after 5 free runs |
| **Krea** | Many image models in Claude Code | Server URL, OAuth sign-in | Claude Code | Not published for MCP |
| **Figma** | Teams already on Figma Weave | Anthropic's directory | Claude Code, Claude Desktop | AI credits, or a paid Weave account |
| **Adobe for Claude** | Generating, then fixing a photo | Anthropic's directory | Claude web, desktop and Claude Code | A free Adobe account for AI tools |
| **Hugging Face** | Open models through Gradio Spaces | Anthropic's directory | Claude Desktop | Not published |
| **Higgsfield** | Creators who also want video | Server URL | Claude and Claude Code | Not published |
| **Canva** | Designs you will keep editing | Anthropic's directory | Claude, through the directory | Any Canva account, some paid actions |

Facts checked on 2026-10-11 against each vendor's docs and Anthropic's connector directory. Prices are not typed here, so follow the pricing links in the data table.

## The tools

### 1. Wireflow

*Best overall for running a whole image workflow from one request*

![Wireflow screenshot](https://assets.wireflow.ai/competitors/wireflow-70f47ccd9660.png?v=r5)

- **What it is:** [Wireflow](https://www.wireflow.ai/) is a hosted platform where ad teams and AI agents build and rerun creative on a shared node board. It works as a Claude connector, so Claude can build an image workflow, run it and read back the results from a chat.
- **Best for:** People who want Claude to run a multi-step image job, such as generate, edit and lay out, as one saved workflow that runs again later.
- **Pricing basis:** It charges credits per generation, according to the model you run. Connecting is free, and so is everything the agent reads. The free plan lets you build up to 5 workflows, and running generations needs a paid plan. The plans are on the [Wireflow pricing page](https://www.wireflow.ai/pricing), checked October 2026.
- **Standout:** Each model is a node on one canvas, and the output of one node feeds the next, so one run can chain several models. Every paid plan can use all 100+ models, including Flux, Imagen, Nano Banana and Ideogram for images. The setup page has steps for Claude, Claude Code, Cursor, ChatGPT and Grok. Source: [the Wireflow MCP page](https://www.wireflow.ai/mcp).
- **Limit:** Wireflow has no listing in Anthropic's connector directory on the check date, so you add it as a custom connector by URL. Results come back as links that the agent reads to you. A step in the connector that shows a run's cost and waits for confirmation is not published, although the agent can check the credit balance first. Creating and editing workflows is an opt-in permission.
- **API or automation:** You add `https://www.wireflow.ai/api/mcp` as a custom connector and sign in with OAuth, so there is no API key to paste, and a connected agent can read and run by default. The same saved workflow also runs from code through `POST /api/v1/workflows/{id}/run`, as [the run endpoint reference](https://www.wireflow.ai/docs/api/run) describes. In Claude Code, open source skills plan the job, show the credit cost and wait for your yes before a run.
- **Sources:** the Wireflow homepage, pricing page, MCP page and run reference linked in this entry, checked 2026-10-11.
- **Links:**
  - [Wireflow node based image generation page](https://www.wireflow.ai/node-based-image-generation)
  - [Docs](https://www.wireflow.ai/docs/api/overview)

Pick Wireflow when the image takes more than one step and you want the same workflow to run again from Claude or from code. If you want a connector that is already in Claude's directory, start at entry 4.

Add the Wireflow connector to Claude Code, from the wireflowINC/skills README. Then run /mcp to sign in. In Claude on the web, add the same URL as a custom connector.
```bash
claude mcp add --transport http wireflow https://www.wireflow.ai/api/mcp
```
Or install the open source Claude Code skills, from the same README. Each skill shows the credit cost and waits for your yes before a run.
```text
/plugin marketplace add wireflowINC/skills
/plugin install wireflow-skills@wireflow
```

### 2. Comfy Cloud

*Best for ComfyUI workflows on cloud GPUs*

![Comfy Cloud screenshot](https://assets.wireflow.ai/competitors/comfy-cloud-ac7894e48d8d.png?v=r5)

- **What it is:** [Comfy Cloud](https://comfy.org/cloud/) is a version of ComfyUI that Comfy officially hosts, with no setup and no GPU needed on your side. Its MCP connection lets an agent search templates, models and nodes and run ComfyUI workflows on Comfy Cloud GPUs.
- **Best for:** Creators and teams who want node-based ComfyUI workflows for images on cloud GPUs, started from a Claude chat.
- **Pricing basis:** It charges a subscription with a credit balance. Through MCP, discovery is free, and running generations requires an active Comfy Cloud subscription after 5 free runs for new users. See the [Comfy pricing page](https://comfy.org/pricing/), checked October 2026.
- **Standout:** The server runs templates and saved workflows, and a `partner_generate` tool runs partner models such as Flux, Gemini, OpenAI, Ideogram and Seedance. A second, local connection is open source and runs against your own ComfyUI. Source: [the Comfy MCP docs](https://docs.comfy.org/agent-tools/mcp).
- **Limit:** A credit or top-up balance alone does not grant access, so you need an active subscription to run. When a generation completes, `get_output` returns a temporary signed download URL and a shell command, and the server does not write files to your machine. It has no listing in Anthropic's directory on the check date, and a cost confirmation step is not published.
- **API or automation:** Claude Desktop adds `https://cloud.comfy.org/mcp` as a custom connector and signs in with OAuth. Claude Code installs the `comfy-cloud` plugin or runs `claude mcp add --transport http comfy-cloud https://cloud.comfy.org/mcp`. Cursor does not support MCP OAuth today, so it uses a Comfy Cloud API key.
- **Note:** The linked repository holds Comfy's Claude Code plugins, including comfy-cloud. The hosted MCP connection itself is a service.
- **Sources:** the Comfy Cloud page, pricing page and MCP docs linked above, checked 2026-10-11.
- **Links:**
  - [Comfy-Org/comfy-skills](https://github.com/Comfy-Org/comfy-skills)

Pick Comfy Cloud over Wireflow when your workflows are ComfyUI graphs and you already hold a Comfy Cloud subscription.

Install the comfy-cloud plugin in Claude Code, from the Comfy MCP docs. Then run /mcp, select comfy-cloud and authenticate.
```text
/plugin marketplace add Comfy-Org/comfy-skills
/plugin install comfy-cloud@comfy-skills
```
Or add only the connection, from the same page.
```bash
claude mcp add --transport http comfy-cloud https://cloud.comfy.org/mcp
```

### 3. Krea

*Best for Claude Code users who want many image models*

![Krea screenshot](https://assets.wireflow.ai/competitors/krea-ai-bfc62405e654.png?v=r5)

- **What it is:** [Krea](https://www.krea.ai/) is an AI image, video and 3D creation app with a node editor, Krea Nodes, for chaining models and prompts. It documents a hosted MCP server that agents use to discover models, inspect schemas and generate images and videos.
- **Best for:** Developers in Claude Code, Codex or Cursor who want to generate from Krea's image models without writing API requests by hand.
- **Pricing basis:** It charges a subscription in compute units, and it has a free plan. An OAuth session on the MCP server spends compute units on the workspace you select, and an API-token session spends the workspace's separate API balance. See the [Krea pricing page](https://www.krea.ai/pricing), checked October 2026.
- **Standout:** You do not need an API key to connect, because you sign in with your Krea account through the client's OAuth flow. Clients that support MCP Apps render an interactive job-result widget inline with the tool response. Source: [Krea's MCP docs](https://www.krea.ai/docs/developers/mcp).
- **Limit:** The MCP docs give setup steps for Claude Code, Codex and Cursor, and steps for Claude on the web or Claude Desktop are not published. It has no listing in Anthropic's directory on the check date. Whether a free account can generate through MCP is not published, and neither is a cost confirmation step.
- **API or automation:** The server runs at `https://api.krea.ai/mcp` over Streamable HTTP, and Claude Code adds it with `claude mcp add --transport http krea-ai https://api.krea.ai/mcp`. Its tools include `list_models`, `generate`, `execute_node_app`, `get_job` and `cancel_job`, and cancelled jobs are not billed.
- **Note:** Free tier is marked yes because the pricing page lists a free plan.
- **Sources:** the Krea homepage, pricing page and MCP docs linked above, checked 2026-10-11.

Pick Krea over Comfy Cloud when you work in Claude Code and want one model call or a Krea node app, with the result shown inline where the client supports it.

Add the Krea MCP server to Claude Code, from Krea's MCP docs. Sign in with your Krea account when Claude Code asks you to connect.
```bash
claude mcp add --transport http krea-ai https://api.krea.ai/mcp
```

### 4. Figma

*Best for teams that already pay for Figma Weave*

![Figma screenshot](https://assets.wireflow.ai/competitors/figma-0b28f0783337.png?v=r5)

- **What it is:** [Figma](https://www.figma.com/) is a design platform, and its Weave product offers AI workflows for imagery, video and audio. Its MCP server has an image tool and a set of Weave tools that run published Weave workflows.
- **Best for:** Design teams that already work in Figma and want an agent to run their Weave workflows or make a quick raster image.
- **Pricing basis:** It charges a subscription per seat. The `generate_image` tool uses Figma AI credits, and running a Weave workflow uses Weave credits and needs a paid standalone Figma Weave account. See the [Figma pricing page](https://www.figma.com/pricing), checked October 2026.
- **Standout:** For a paid Weave run, the agent shows the credit cost and asks for confirmation first, and free runs skip that step. The tool reference spells out that cost check, which most entries here do not publish. Source: [Figma's MCP tools reference](https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts/).
- **Limit:** The `generate_image` tool returns a temporary URL that you download within seven days, and it does not place the image on the Figma canvas. It is listed in Figma's tools reference and is not among the 9 tools in Anthropic's directory listing, so check the tool list in your client. View and Collab seats get up to 20 tool calls a month.
- **API or automation:** The connector URL in Anthropic's directory is `https://mcp.figma.com/mcp`, and Claude Code adds it with `claude mcp add --transport http figma https://mcp.figma.com/mcp`. The `weave_run_tool` tool can start 1 to 10 runs of a Weave workflow in one call. Only clients listed in the Figma MCP Catalog can connect.
- **Note:** The linked repository is Figma's setup guide for the MCP server, not server code. Free tier is marked yes because the pricing page lists a free Starter plan.
- **Sources:** the tools reference linked above, plus [Figma's rate limits page](https://developers.figma.com/docs/figma-mcp-server/rate-limits-access/) and [Anthropic's directory listing for Figma](https://claude.com/marketplace/connectors/figma), checked 2026-10-11.
- **Links:**
  - [Docs](https://developers.figma.com/docs/figma-mcp-server/)
  - [figma/mcp-server-guide](https://github.com/figma/mcp-server-guide)

Pick Figma over Krea when the workflows your team built live in Figma Weave and a cost check before each paid run matters to you.

Install the Figma plugin for Claude Code, which Figma's remote server setup page recommends.
```bash
claude plugin install figma@claude-plugins-official
```
Or add the remote server by hand, from the same page.
```bash
claude mcp add --transport http figma https://mcp.figma.com/mcp
```

### 5. Adobe for Claude

*Best for generating and then fixing a photo in one chat*

![Adobe for Claude screenshot](https://assets.wireflow.ai/competitors/adobe-for-claude-f74300f6dc39.png?v=r5)

- **What it is:** [Adobe for Claude](https://www.adobe.com/adobe-connectors/adobe-for-claude.html) brings Adobe Express, Acrobat, Photoshop, Lightroom, Illustrator, Firefly, Premiere, InDesign and Adobe Stock tools into a Claude conversation. Adobe makes the connector, and Anthropic's directory lists it as Anthropic verified.
- **Best for:** People who already use Adobe apps and want to generate a scene, then crop it, adjust the lighting or resize it by describing the change in Claude.
- **Pricing basis:** Adobe states no price for the connector. Many capabilities work without signing in, a free Adobe account unlocks more, including generative AI workflows, and some tools require an eligible paid Adobe plan.
- **Standout:** The directory listing shows 67 tools, among them `create_firefly_board` and `asset_inline_preview`. Adobe's FAQ says the connector can generate studio-quality scenes, and the listing says you can edit photos individually or in bulk. Source: [Anthropic's directory listing for Adobe](https://claude.com/marketplace/connectors/adobe-creativity).
- **Limit:** Adobe says the connector does not include every feature from each Adobe app. A step that shows a cost and waits for confirmation before a generation is not published. A public API for calling the same tools from your own code is not published on the pages we read.
- **API or automation:** It is an MCP connector at a hosted URL with sign-in required, and Adobe says it is available in Claude on web and desktop and in Claude Code. You add the Adobe plugin from Plugins in Claude, connect it on the Connectors tab, then type `/adobe` in a new conversation.
- **Note:** Free tier is marked yes because Adobe says many tools work without signing in. Adobe states no price for the connector, so no pricing link is listed.
- **Sources:** the Adobe page and the directory listing linked above, checked 2026-10-11.

Pick Adobe for Claude over Figma when the job is a photo or a marketing asset and you want a connector from Claude's own directory that needs no Adobe account to start.

Connector URL from Anthropic's directory listing. Adobe's page says to add the Adobe plugin from Plugins in Claude, connect it on the Connectors tab, then type /adobe in a new conversation.
```text
https://adobe-creativity.adobe.io/mcp
```

### 6. Hugging Face

*Best for trying open models through Gradio Spaces*

![Hugging Face screenshot](https://assets.wireflow.ai/competitors/huggingface-946249a270c8.png?v=r5)

- **What it is:** [Hugging Face](https://huggingface.co/) is a platform where the machine learning community collaborates on models, datasets and applications, with Spaces for hosted apps. Its MCP server connects an assistant to the Hub and to community tools from MCP-compatible Gradio Spaces, including image generation.
- **Best for:** Developers who want to try open image models from Claude and choose which Spaces the assistant can call.
- **Pricing basis:** It charges a subscription for its paid plans, and some Spaces hardware is free. Which plan or credits a Space needs to generate through the MCP server is not published. See the [Hugging Face pricing page](https://huggingface.co/pricing), checked October 2026.
- **Standout:** Images generated by Gradio Spaces are embedded in the response unless you turn on the Remove Embedded Images option. You choose which Spaces the server exposes in your MCP settings, and a Dynamic Spaces option lets the assistant find MCP-compatible Spaces at runtime. Source: [the Hugging Face MCP docs](https://huggingface.co/docs/hub/agents-mcp).
- **Limit:** The image tools you get depend on the Spaces you select. The directory listing shows two image tools from Spaces, one of them named `gr1_flux1_schnell_infer`. Setup steps for Claude Code and a cost confirmation step are not published on the MCP docs page.
- **API or automation:** Anthropic's directory lists it as Anthropic verified, with sign-in required. Outside the directory, you open your MCP settings on Hugging Face while logged in, pick your client and paste the configuration snippet the page generates. Source: [Anthropic's directory listing for Hugging Face](https://claude.com/marketplace/connectors/hugging-face).
- **Note:** The REST API column refers to Hugging Face Inference Providers, which are documented apart from the MCP server.
- **Sources:** the Hugging Face homepage, pricing page, MCP docs and directory listing linked above, checked 2026-10-11.

Pick Hugging Face over Adobe for Claude when you want a specific open model and you are comfortable choosing Spaces yourself.

Open your MCP settings while logged in, pick your client and copy the snippet the page generates, from the Hugging Face MCP docs.
```text
https://huggingface.co/settings/mcp
```

### 7. Higgsfield

*Best for creators who also want video models*

![Higgsfield screenshot](https://assets.wireflow.ai/competitors/higgsfield.png?v=r5)

- **What it is:** [Higgsfield](https://higgsfield.ai/) is an AI creative suite for images, video and voice with 30+ models, editing, upscaling and an agent. It offers a Higgsfield MCP for Claude to generate images and videos inside Claude.
- **Best for:** Creators who want many video models in one app and want to reach the same account's image tools from Claude.
- **Pricing basis:** Not published in a form we could read. Plan prices could not be read from the [Higgsfield pricing page](https://higgsfield.ai/pricing) with a plain request on the check date, October 2026.
- **Standout:** The MCP page says you can generate images and videos in ChatGPT and Claude with the Higgsfield plugin and MCP, and it lists connection options for Claude, Claude Code, a CLI and other clients. Source: [the Higgsfield MCP page](https://higgsfield.ai/mcp).
- **Limit:** How results display in Claude, a cost confirmation before a run and which plan generation needs are not published in the readable text of the MCP page. Its setup steps sit in tabs that a plain request does not return, so this entry is thinner than the others. It has no listing in Anthropic's directory on the check date.
- **API or automation:** The server URL on the MCP page is `https://mcp.higgsfield.ai/mcp`. A public API is not verified for this list.
- **Sources:** the Higgsfield homepage, pricing page and MCP page linked above, checked 2026-10-11.

Pick Higgsfield over Hugging Face when you already use Higgsfield for video and want images from the same place. Read its MCP page in a browser before you rely on a detail here.

Server URL from the Higgsfield MCP page. Follow the Claude or Claude Code tab on that page for the steps.
```text
https://mcp.higgsfield.ai/mcp
```

### 8. Canva

*Best for designs you will keep editing*

![Canva screenshot](https://assets.wireflow.ai/competitors/canva-dcf5315d9542.png?v=r5)

- **What it is:** [Canva](https://www.canva.com/) is an online design platform with templates, brand kits and built-in AI tools. Its Claude connector is made by Canva, and Anthropic's directory lists it as Anthropic verified.
- **Best for:** Anyone producing everyday marketing designs who wants Claude to generate a design and export it.
- **Pricing basis:** It charges a subscription, and it has a free plan. The connector is available on all Canva accounts, and some connector actions such as Brand Template search need a paid plan. See the [Canva pricing page](https://www.canva.com/pricing/), checked October 2026.
- **Standout:** The directory lists 17 tools, including `generate-design`, `import-design-from-url`, `export-design` and `get-export-formats`, so Claude can search, read, import, generate and export designs. Source: [Anthropic's directory listing for Canva](https://claude.com/marketplace/connectors/canva).
- **Limit:** The connector generates Canva designs, which is a different output from a standalone generated image. Whether the design appears inside the chat, a cost confirmation step and setup steps for Claude Code are not published in the listing. Canva's own help page for the connector could not be read with a plain request on the check date.
- **API or automation:** It is a hosted connector at `https://mcp.canva.com/mcp`, with sign-in required. Canva also documents Connect APIs for developers.
- **Note:** The REST API column refers to Canva's Connect APIs for developers, which Canva documents apart from the connector.
- **Sources:** the directory listing and pricing page linked above, checked 2026-10-11.

Pick Canva over Higgsfield when the result should be an editable design in your Canva account and not a single image file.

Connector URL from Anthropic's directory listing. Add it from the directory in Claude.
```text
https://mcp.canva.com/mcp
```

## Claude plans and apps, the baseline

Claude is the app every entry plugs into, so its own rules are described here and not ranked. These lines come from Anthropic's help centre and site map, checked 2026-10-11.

- **Directory connectors:** Web connectors are available for all users on Claude, Cowork, Claude Desktop and Claude Mobile. Source: [Anthropic's guide to using connectors](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities).
- **Custom connectors:** Custom connectors using remote MCP are available on Claude, Cowork and Claude Desktop for users on Free, Pro, Max, Team and Enterprise plans, and Free users are limited to one custom connector. Source: [Anthropic's guide to custom connectors](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp).
- **Team and Enterprise plans:** An owner enables connectors for the organization before members can use them, and only Owners and Primary Owners can add a custom connector to a Team plan.
- **Where connectors work:** Anthropic says connectors work across Claude, Claude Desktop, Claude Code and the API.
- **Directory size:** Anthropic's site map listed 935 connector pages on the check date, and 4 of the 8 entries here have one.

## What each check means

A check means the vendor's docs or Anthropic's own pages describe it. A cross means the source says otherwise. A dash means not published in the pages we read, which is not proof that it is absent.

- **Runs a saved workflow in one request:** The docs describe one tool call that runs a workflow you saved or a ready-made template, with several steps inside it. A dash means the docs describe single generations or edits only.
- **In Anthropic's directory:** The connector has a listing page in Anthropic's connector directory. A cross means you add the vendor's server URL yourself.
- **Claude web and desktop:** The vendor or Anthropic describes it working in Claude on the web and in Claude Desktop through a hosted URL, with nothing installed locally.
- **Claude Code:** The vendor describes setup in Claude Code.
- **Account sign-in with no API key:** You connect by signing in to the vendor account, not by pasting an API key.
- **Image shown in chat:** The docs say the result renders inside the conversation. A dash with a note means the docs describe a link or a download step.
- **Asks before spending credits:** The docs describe a step that shows the cost and waits for your confirmation before a paid generation.
- **Generates on a free vendor account:** The vendor says a free account can generate through the connector. A cross means a paid plan or a subscription is required.

## How this list is maintained

Every cell comes from the vendor's own docs or from Anthropic's connector directory and help centre, last checked on 11 October 2026. The numbered order is editorial and uses 4 checks: how much of an image job one request can finish, where you add the connector, which Claude apps the vendor's docs cover, and what the vendor says you need before a run. The capability score is a separate plain count of documented checks, and it does not set the order. Nothing here was tested, so no connector was installed and no image was generated for this list.

The list is capped at 8 entries. Magnific and Flora also document MCP servers and are left out for that reason. To correct a cell, open an issue or a pull request with the tool, the check and a link to the page that proves it. PRs are welcome, including corrections to entry 1. A longer walkthrough is on the Wireflow blog, which covers [three ways to generate images in Claude Code](https://www.wireflow.ai/blog/generate-images-in-claude-code).

- [`data/tools.json`](data/tools.json) is the source of truth. The tables in this README are generated from it and are overwritten on every run, so edit the JSON, not the tables.
- [`scripts/update.js`](scripts/update.js) fetches star counts and latest release tags from the GitHub API for the tools that publish an official repo, stamps the check date, and regenerates the tables. `--offline` regenerates without the network; `--check` exits non-zero if the README has drifted from the data.
- [`.github/workflows/refresh.yml`](.github/workflows/refresh.yml) runs it weekly and on manual dispatch, and commits only when the data actually changed.
- Prices are deliberately not stored as numbers. A stale price in a comparison table is worse than no price, so the table links to each vendor's own pricing page.

## FAQ

<details>
<summary><strong>Can Claude generate images?</strong></summary>

Yes, Claude can make images through a connector. Each of the 8 entries here documents image generation that Claude calls from a chat, and 4 of them are in Anthropic's own connector directory. What you get back differs: some show the image in the conversation, and others return a link or a download command.

</details>

<details>
<summary><strong>What is the best MCP server for image generation?</strong></summary>

The best one depends on the job. For a multi-step image, Wireflow and Comfy Cloud run a whole saved workflow from one request. For a single image from one model, Krea and Hugging Face are shorter paths. For a photo you want to generate and then fix, Adobe for Claude lists 67 tools in Anthropic's directory.

</details>

<details>
<summary><strong>Do I need an API key?</strong></summary>

You do not need one to sign in on most of them. Wireflow, Krea and Comfy Cloud document OAuth sign-in with no API key, and the 4 directory connectors show sign-in as required. Comfy Cloud asks for an API key only in clients without MCP OAuth, such as Cursor.

</details>

<details>
<summary><strong>Which image models can Claude use through a connector?</strong></summary>

The models depend on the connector you add. Wireflow's paid plans cover 100+ models, including Flux, Imagen, Nano Banana and Ideogram for images, and [the Wireflow node reference](https://www.wireflow.ai/docs/nodes) lists each one. Comfy Cloud runs ComfyUI workflows and partner models such as Flux and Ideogram, and Krea lists its models through a `list_models` tool.

</details>

<details>
<summary><strong>How much does it cost to generate images this way?</strong></summary>

Each run is billed by the vendor you connected, in that vendor's own units. Wireflow charges credits per generation, and each model card shows its credit cost per run, as [the guide to using AI models](https://www.wireflow.ai/docs/using-ai-models) explains. Krea spends compute units, Figma spends AI credits or Weave credits, and Comfy Cloud needs an active subscription.

</details>

<details>
<summary><strong>Can I use these connectors on a free Claude plan?</strong></summary>

Yes, although Free users face one limit. Anthropic's help centre says directory connectors are available to all users, and that custom connectors are available on Free, Pro, Max, Team and Enterprise plans, with Free users limited to one custom connector. The vendor's own plan is a separate question, and the comparison table lists it.

</details>

<details>
<summary><strong>How do I add a connector to Claude Desktop or Claude Code?</strong></summary>

For a directory connector, you browse the Connectors Directory in Claude and connect it. For the other 4, you add the vendor's server URL as a custom connector in Claude or Claude Desktop, and in Claude Code you run the `claude mcp add` command from the vendor's docs. The quickstart under each entry has the exact line where the vendor publishes one.

</details>

## The short version

Pick Wireflow when the image takes several steps and you want one saved workflow that Claude and your own code can both run. Pick Comfy Cloud, the next entry, when your workflows are ComfyUI graphs and you hold a subscription. If you want a connector from Claude's own directory, start with Adobe for Claude for photos or Figma for Weave workflows. Before you commit, connect your two finalists, ask Claude to list each one's image tools and which ones spend credits, and run one real job. For the first option, the next page to read is [a text to image workflow example](https://www.wireflow.ai/features/text-to-image-api).

## Contributing

Corrections and additions are welcome, including corrections to the entry for the tool that maintains this list. Open an issue with the tool name, a working link, one line on what it does that the tools already listed do not, and one line on where it stops. Entries are judged on whether they are usable today, not on popularity. Full rules in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[CC0 1.0 Universal](LICENSE), public domain. Take the data, fork the list, no attribution required.

---

Maintained by [a1adams](https://github.com/a1adams).
