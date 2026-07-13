<p align="center">
<pre>
888             888      d8b
888             888      Y8P
888             888
888888  .d88b.  88888b.  888  8888b.  .d8888b
888    d88""88b 888 "88b 888     "88b 88K
888    888  888 888  888 888 .d888888 "Y8888b.
Y88b.  Y88..88P 888 d88P 888 888  888      X88
 "Y888  "Y88P"  88888P"  888 "Y888888  88888P'
</pre>
</p>

<p align="center">
<img alt="model manager" src="https://img.shields.io/badge/model_manager-c4a7e7?style=flat-square&labelColor=191724"> <img alt="search engine" src="https://img.shields.io/badge/search_engine-9ccfd8?style=flat-square&labelColor=191724"> <img alt="web crawler" src="https://img.shields.io/badge/web_crawler-f6c177?style=flat-square&labelColor=191724"> <img alt="MCP server" src="https://img.shields.io/badge/MCP_server-ebbcba?style=flat-square&labelColor=191724"> <img alt="obsidian plugin" src="https://img.shields.io/badge/obsidian_plugin-908caa?style=flat-square&labelColor=191724">
</p>

I'm building [lilbee](https://github.com/tobocop2/lilbee), the whole local AI stack in a single executable: it runs and manages the models, and it's a search engine you can talk to. It indexes your files, notes, and code, crawls web pages into your library, and every answer cites the exact file and line. It started as me trying to build an Encarta 99 out of my own stuff that I could talk to privately, and that's still the mission.

## Why lilbee

Onboarding with local AI is painful. A typical stack is a model server, a vector database, a document ingestion pipeline, a web UI, and a Docker Compose file holding it all together. Every piece needs configuring before you can ask a single question.

lilbee is that whole stack in one self-contained executable: model manager, search engine over your own data, MCP for agents, HTTP for GUIs, and a TUI for the terminal. No containers, no networking, nothing else to install. It scales from one laptop to as many GPUs as you have.

I'm trying to democratize local AI, starting with talking to your own stuff, while building the tool I want for myself.

## What I'm building

### [lilbee](https://github.com/tobocop2/lilbee) ![★](https://img.shields.io/github/stars/tobocop2/lilbee?style=flat-square&label=%E2%98%85&labelColor=191724&color=c4a7e7) ![↓](https://img.shields.io/github/downloads/tobocop2/lilbee/total?style=flat-square&label=%E2%86%93%20downloads&labelColor=191724&color=9ccfd8)

Terminal-first, because I built it for myself and I knew that if the architecture stayed flexible, friendlier surfaces would come easily. TUI, CLI, REST API, MCP server, and Python library, with multi-GPU placement and integrations for opencode and hermes so programmers can put local AI behind their favorite agents. lilbee is its own model manager: you don't need Ollama or LM Studio at all, and the model families it runs are [tested end to end on real GPUs](https://github.com/tobocop2/lilbee/blob/main/docs/tested-models.md), the architectures behind most of the 190,000+ GGUF models on Hugging Face. Already running Ollama or LM Studio? lilbee connects to them and keeps your models.

![lilbee indexing its own source and answering with citations, with a model split across multiple GPUs](https://raw.githubusercontent.com/tobocop2/lilbee/gh-pages/demos/tui-multi-gpu-self-index.gif)

### [obsidian-lilbee](https://github.com/tobocop2/obsidian-lilbee) ![★](https://img.shields.io/github/stars/tobocop2/obsidian-lilbee?style=flat-square&label=%E2%98%85&labelColor=191724&color=c4a7e7) ![↓](https://img.shields.io/github/downloads/tobocop2/obsidian-lilbee/total?style=flat-square&label=%E2%86%93%20downloads&labelColor=191724&color=9ccfd8)

One of those friendlier surfaces, the gateway for Q&A with local models. My favorite story here is a completely non-technical user who went from the plugin store to talking to his solar panel docs in minutes, without ever opening a terminal.

![the same question answered inside Obsidian](https://raw.githubusercontent.com/tobocop2/obsidian-lilbee/gh-pages/demos/what_is_lilbee.gif)

## Upstream work

lilbee is built on a lot of open source projects, and the one I work on most is [xberg](https://github.com/xberg-io/xberg).

Extraction is the core of lilbee. You can't search what you can't read, and an answer is only as good as the text that came out of the document, so a scanned PDF that turns to mush or a table that loses its columns is a bad answer waiting to happen. Good extraction is what makes good search possible. That's why I'm on the [xberg team](https://github.com/search?q=org%3Axberg-io+author%3Atobocop2+is%3Apr+is%3Amerged&type=pullrequests), and where most of my open source work goes.

In early iterations of lilbee I built my own extraction layer. When I found xberg I gutted all of that work, and a lot of it became my earliest contributions there.

Stuff I've contributed that I'm pretty proud of:

| Project | Stars | What I did |
|---------|-------|------------|
| [xberg](https://github.com/xberg-io/xberg) / [alef](https://github.com/xberg-io/alef) <br>![team](https://img.shields.io/badge/-team-c4a7e7?style=flat-square&labelColor=191724) | ![★](https://img.shields.io/github/stars/xberg-io/xberg?style=flat-square&label=%E2%98%85&labelColor=191724&color=c4a7e7) ![★](https://img.shields.io/github/stars/xberg-io/alef?style=flat-square&label=%E2%98%85&labelColor=191724&color=c4a7e7) | The embedding backend plugin, semantic chunking, PDF page rendering across all bindings, new formats, scanned-PDF detection, and Intel-Mac support in xberg; typed trait callbacks and enum constructors in [alef](https://github.com/xberg-io/alef); language detection and new grammars in [tree-sitter-language-pack](https://github.com/xberg-io/tree-sitter-language-pack). [All my merged PRs](https://github.com/search?q=org%3Axberg-io+author%3Atobocop2+is%3Apr+is%3Amerged&type=pullrequests). |
| [lancedb](https://github.com/lancedb/lancedb) / [lance](https://github.com/lance-format/lance) <br>![in%20review](https://img.shields.io/badge/-in%20review-f6c177?style=flat-square&labelColor=191724) | ![★](https://img.shields.io/github/stars/lancedb/lancedb?style=flat-square&label=%E2%98%85&labelColor=191724&color=9ccfd8) ![★](https://img.shields.io/github/stars/lance-format/lance?style=flat-square&label=%E2%98%85&labelColor=191724&color=9ccfd8) | In review: [runtime SIMD dispatch](https://github.com/lance-format/lance/pull/6630) for pre-Haswell x86_64 builds, and [compat wheels](https://github.com/lancedb/lancedb/pull/3327) so older machines aren't left out. |
| [GPUStack](https://github.com/gpustack/gpustack) / [gguf-parser-go](https://github.com/gpustack/gguf-parser-go) <br>![merged](https://img.shields.io/badge/-merged-9ccfd8?style=flat-square&labelColor=191724) | ![★](https://img.shields.io/github/stars/gpustack/gpustack?style=flat-square&label=%E2%98%85&labelColor=191724&color=f6c177) ![★](https://img.shields.io/github/stars/gpustack/gguf-parser-go?style=flat-square&label=%E2%98%85&labelColor=191724&color=f6c177) | My work landed in [gguf-parser-go](https://github.com/gpustack/gguf-parser-go), the GGUF inspector and VRAM estimator GPUStack is built on. [Fixed](https://github.com/gpustack/gguf-parser-go/pulls?q=is%3Apr+author%3Atobocop2+is%3Amerged) multimodal projector VRAM estimates: unknown projector types, flash attention, audio, and models that don't declare an image size. |
| [huggingface_hub](https://github.com/huggingface/huggingface_hub) / [xet-core](https://github.com/huggingface/xet-core) <br>![merged](https://img.shields.io/badge/-merged-9ccfd8?style=flat-square&labelColor=191724) | ![★](https://img.shields.io/github/stars/huggingface/huggingface_hub?style=flat-square&label=%E2%98%85&labelColor=191724&color=ebbcba) ![★](https://img.shields.io/github/stars/huggingface/xet-core?style=flat-square&label=%E2%98%85&labelColor=191724&color=ebbcba) | [Fixed](https://github.com/huggingface/huggingface_hub/pull/4065) an `hf_hub_download` crash when stderr has no real file descriptor. Smoother progress for xet downloads is in review ([hub](https://github.com/huggingface/huggingface_hub/pull/4059), [xet-core](https://github.com/huggingface/xet-core/pull/791)). |
| [pdf_oxide](https://github.com/yfedoseev/pdf_oxide) <br>![merged](https://img.shields.io/badge/-merged-9ccfd8?style=flat-square&labelColor=191724) | ![★](https://img.shields.io/github/stars/yfedoseev/pdf_oxide?style=flat-square&label=%E2%98%85&labelColor=191724&color=ea9a97) | [3 merged PRs](https://github.com/yfedoseev/pdf_oxide/pulls?q=is%3Apr+author%3Atobocop2+is%3Amerged) fixing text extraction in scientific PDFs: subscript digits coming out as decimals, fractions fusing with the equals sign, fragmented words, and rotated pages extracting out of order. |

## Older stuff

Fixes I've landed over the years in things I'm not working with day to day anymore:

| Project | Stars | What I did |
|---------|-------|------------|
| [openapi-generator](https://github.com/OpenAPITools/openapi-generator) | ![★](https://img.shields.io/github/stars/OpenAPITools/openapi-generator?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | [Unity 2019 support](https://github.com/OpenAPITools/openapi-generator/pulls?q=is%3Apr+author%3Atobocop2) for the C# generator, with updated samples. |
| [llama-cpp-python](https://github.com/abetlen/llama-cpp-python) | ![★](https://img.shields.io/github/stars/abetlen/llama-cpp-python?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | [Fixed](https://github.com/abetlen/llama-cpp-python/pull/2226) models failing to load when their chat template uses HuggingFace generation tags. |
| [mercurius](https://github.com/mercurius-js/mercurius) | ![★](https://img.shields.io/github/stars/mercurius-js/mercurius?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | [Fixed a crash](https://github.com/mercurius-js/mercurius/pulls?q=is%3Apr+author%3Atobocop2) in encapsulated Fastify apps where a parent object defines loaders. |
| [screenshot-glb](https://github.com/Shopify/screenshot-glb) | ![★](https://img.shields.io/github/stars/Shopify/screenshot-glb?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | [Added](https://github.com/Shopify/screenshot-glb/pulls?q=is%3Apr+author%3Atobocop2) an optional timeout parameter to Shopify's GLB screenshot tool. |
| [MetalAPI](https://github.com/tobocop2/MetalAPI) | ![★](https://img.shields.io/github/stars/tobocop2/MetalAPI?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | My first project ever, from my last semester of college. Scraped the Metal Archives, the encyclopedic resource for heavy metal, and served the whole thing as a REST API. |
| [go-utils](https://github.com/Goldziher/go-utils) | ![★](https://img.shields.io/github/stars/Goldziher/go-utils?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | [Added](https://github.com/Goldziher/go-utils/pulls?q=is%3Apr+author%3Atobocop2) `unique` and fixed `reverse`, four years before Goldziher and I would end up on xberg together. |
| [simpler-cpp-json](https://github.com/tobocop2/simpler-cpp-json) | ![★](https://img.shields.io/github/stars/tobocop2/simpler-cpp-json?style=flat-square&label=%E2%98%85&labelColor=191724&color=6e6a86) | Generic `to_json`/`from_json` for arbitrary C++ structs and STL containers, built on nlohmann/json and Boost.Fusion. It saved my team at work a lot of time and keystrokes, and nlohmann/json later shipped the same idea as `NLOHMANN_DEFINE_TYPE_INTRUSIVE`. |

## Elsewhere

[![lilbee: the whole local AI stack in one executable, with a cited answer shown in the terminal UI](https://lilbee.sh/social-card.png)](https://lilbee.sh)

<p align="center">
<pre>
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|t|o|b|i|a|s|@|l|i|l|b|e|e|.|s|h|
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
</pre>
<a href="https://lilbee.sh">lilbee.sh</a> &nbsp;&#183;&nbsp; <a href="https://web.libera.chat/#lilbee">#lilbee on Libera.Chat</a>
</p>
