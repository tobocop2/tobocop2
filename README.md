# Hi, I'm Tobias

I'm building [lilbee](https://github.com/tobocop2/lilbee), a local search engine you can talk to. It's the whole local-AI stack in a single executable: it runs the models, indexes your files, notes, and code, crawls web pages into your library, and every answer cites the exact file and line. It started as me trying to build an Encarta 99 out of my own stuff that I could talk to privately, and that's still the mission.

![What is lilbee](https://raw.githubusercontent.com/tobocop2/obsidian-lilbee/gh-pages/demos/what_is_lilbee.gif)

Onboarding with local AI is painful. A typical stack is a model server, a vector database, a document ingestion pipeline, a web UI, and a Docker Compose file holding it all together, and every piece needs configuring before you can ask a single question. lilbee is that whole stack in one self-contained executable: model manager, search engine over your own data, MCP for agents, HTTP for GUIs, and a TUI for the terminal. No containers, no networking, nothing else to install, and it scales from one laptop to as many GPUs as you have. I'm trying to democratize local AI, starting with talking to your own stuff, while building the tool I want for myself.

## What I'm building

- **[lilbee](https://github.com/tobocop2/lilbee)** ![Stars](https://img.shields.io/github/stars/tobocop2/lilbee?style=flat-square): terminal-first, because I built it for myself and I knew that if the architecture stayed flexible, friendlier surfaces would come easily. TUI, CLI, REST API, MCP server, and Python library, with a built-in model manager, multi-GPU placement, and integrations for opencode and hermes so programmers can put local AI behind their favorite agents. Works with or without Ollama and LM Studio.
- **[obsidian-lilbee](https://github.com/tobocop2/obsidian-lilbee)** ![Stars](https://img.shields.io/github/stars/tobocop2/obsidian-lilbee?style=flat-square): one of those friendlier surfaces, the gateway for Q&A with local models. My favorite story here is a completely non-technical user who went from the plugin store to talking to his solar panel docs in minutes, without ever opening a terminal.

## Upstream work

lilbee sits on top of a deep stack: document extraction, model serving, vector storage, language bindings, download plumbing. When I hit an edge in one of those layers I fix it upstream instead of working around it, so a lot of my open source work lives in other people's repos. Most of it is in the [xberg](https://github.com/xberg-io/xberg) ecosystem, where at this point I've made [40+ PRs](https://github.com/search?q=org%3Axberg-io+author%3Atobocop2+is%3Apr+is%3Amerged&type=pullrequests) across the organization. In lilbee's earliest incarnation I accidentally reinvented a subset of it, reached out to [Goldziher](https://github.com/Goldziher) to thank him for tree-sitter-language-pack, got pointed at the real thing, and within a few weeks I was contributing my discoveries upstream. I've been a member of the xberg open source team ever since.

Stuff I've contributed that I'm pretty proud of:

| Project | Stars | What I did |
|---------|-------|------------|
| [lancedb](https://github.com/lancedb/lancedb) / [lance](https://github.com/lance-format/lance) | ![Stars](https://img.shields.io/github/stars/lancedb/lancedb?style=flat-square) ![Stars](https://img.shields.io/github/stars/lance-format/lance?style=flat-square) | In review: [runtime SIMD dispatch](https://github.com/lance-format/lance/pull/6630) for pre-Haswell x86_64 builds, and [compat wheels](https://github.com/lancedb/lancedb/pull/3327) so older machines aren't left out. |
| [xberg](https://github.com/xberg-io/xberg) | ![Stars](https://img.shields.io/github/stars/xberg-io/xberg?style=flat-square) | The embedding backend plugin, semantic chunking, PDF page rendering across all bindings, new formats, scanned-PDF detection, and Intel-Mac support in xberg; typed trait callbacks and enum constructors in [alef](https://github.com/xberg-io/alef) ![Stars](https://img.shields.io/github/stars/xberg-io/alef?style=flat-square); language detection and new grammars in [tree-sitter-language-pack](https://github.com/xberg-io/tree-sitter-language-pack). [All my merged PRs](https://github.com/search?q=org%3Axberg-io+author%3Atobocop2+is%3Apr+is%3Amerged&type=pullrequests). |
| [GPUStack](https://github.com/gpustack/gpustack) | ![Stars](https://img.shields.io/github/stars/gpustack/gpustack?style=flat-square) | My work landed in [gguf-parser-go](https://github.com/gpustack/gguf-parser-go), the GGUF inspector and VRAM estimator GPUStack is built on. [Fixed](https://github.com/gpustack/gguf-parser-go/pulls?q=is%3Apr+author%3Atobocop2+is%3Amerged) multimodal projector VRAM estimates: unknown projector types, flash attention, audio, and models that don't declare an image size. |
| [huggingface_hub](https://github.com/huggingface/huggingface_hub) / [xet-core](https://github.com/huggingface/xet-core) | ![Stars](https://img.shields.io/github/stars/huggingface/huggingface_hub?style=flat-square) ![Stars](https://img.shields.io/github/stars/huggingface/xet-core?style=flat-square) | [Fixed](https://github.com/huggingface/huggingface_hub/pull/4065) an `hf_hub_download` crash when stderr has no real file descriptor. Smoother progress for xet downloads is in review ([hub](https://github.com/huggingface/huggingface_hub/pull/4059), [xet-core](https://github.com/huggingface/xet-core/pull/791)). |
| [pdf_oxide](https://github.com/yfedoseev/pdf_oxide) | ![Stars](https://img.shields.io/github/stars/yfedoseev/pdf_oxide?style=flat-square) | [3 merged PRs](https://github.com/yfedoseev/pdf_oxide/pulls?q=is%3Apr+author%3Atobocop2+is%3Amerged) fixing text extraction in scientific PDFs: subscript digits coming out as decimals, fractions fusing with the equals sign, fragmented words, and rotated pages extracting out of order. |

## Older stuff

Fixes I've landed over the years in things I'm not working with day to day anymore:

| Project | Stars | What I did |
|---------|-------|------------|
| [openapi-generator](https://github.com/OpenAPITools/openapi-generator) | ![Stars](https://img.shields.io/github/stars/OpenAPITools/openapi-generator?style=flat-square) | [Unity 2019 support](https://github.com/OpenAPITools/openapi-generator/pulls?q=is%3Apr+author%3Atobocop2) for the C# generator, with updated samples. |
| [llama-cpp-python](https://github.com/abetlen/llama-cpp-python) | ![Stars](https://img.shields.io/github/stars/abetlen/llama-cpp-python?style=flat-square) | [Fixed](https://github.com/abetlen/llama-cpp-python/pull/2226) models failing to load when their chat template uses HuggingFace generation tags. |
| [mercurius](https://github.com/mercurius-js/mercurius) | ![Stars](https://img.shields.io/github/stars/mercurius-js/mercurius?style=flat-square) | [Fixed a crash](https://github.com/mercurius-js/mercurius/pulls?q=is%3Apr+author%3Atobocop2) in encapsulated Fastify apps where a parent object defines loaders. |
| [screenshot-glb](https://github.com/Shopify/screenshot-glb) | ![Stars](https://img.shields.io/github/stars/Shopify/screenshot-glb?style=flat-square) | [Added](https://github.com/Shopify/screenshot-glb/pulls?q=is%3Apr+author%3Atobocop2) an optional timeout parameter to Shopify's GLB screenshot tool. |
| [MetalAPI](https://github.com/tobocop2/MetalAPI) | ![Stars](https://img.shields.io/github/stars/tobocop2/MetalAPI?style=flat-square) | My first project ever, from my last semester of college. Scraped the Metal Archives, the encyclopedic resource for heavy metal, and served the whole thing as a REST API. |
| [go-utils](https://github.com/Goldziher/go-utils) | ![Stars](https://img.shields.io/github/stars/Goldziher/go-utils?style=flat-square) | [Added](https://github.com/Goldziher/go-utils/pulls?q=is%3Apr+author%3Atobocop2) `unique` and fixed `reverse`, four years before Goldziher and I would end up on xberg together. |

## Elsewhere

- Site: [lilbee.sh](https://lilbee.sh)
- IRC: `#lilbee` on [Libera.Chat](https://web.libera.chat/#lilbee)
