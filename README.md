<h1 align = "center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=Plus+Jakarta+Sans&weight=500&size=22&pause=800&color=F7F7F7&background=0D1117FF&center=true&random=false&width=500&lines=Hello+I'm+Bima+Ilyasa+Rachmanditya;I'm+an+AI+Engineer;I'm+a+Data+Scientist;I'm+a+Geophysics+Engineer" alt="Typing SVG" />
  </a>
</h1>
<br>
<div align="center"> 
  <a href="mailto:bimoilyasa@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-333333?style=for-the-badge&logo=gmail&logoColor=red" />
  </a>
  <a href="https://www.linkedin.com/in/bima-ilyasa/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank" />
  </a>
  <a href="https://www.pourterra.com" target="_blank">
     <img src="https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=todoist&logoColor=white" target="_blank" /> <!-- sqlite, safari, google-chrome are other good icon options -->
  </a>
</div>
<br/>
<h2 align="center">Languages-Frameworks-Tools</h2>
<div align="center">
    <img src="https://skillicons.dev/icons?i=python,supabase,gcp,docker,github,vscode,mongodb,obsidian,postgres" />
    <img src="https://skillicons.dev/icons?i=sklearn,tensorflow,fastapi,tailwind,opencv,nextjs,mongodb,mysql" /><br>
</div>

<h2 align="center">Github Statistics</h2>
<div align="center">
<!--     <img src="https://github-readme-stats.vercel.app/api?username=pour-le-hommes&theme=vue-dark&show_icons=true&hide_border=true&count_private=true" alt="pour-le-hommes's Stats"> -->
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=pour-le-hommes&theme=vue-dark&show_icons=true&hide_border=true&layout=compact" alt="pour-le-hommes's Top Languages">
</div>
<div align="center"; display: flex>
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=pour-le-hommes&theme=vue-dark&hide_border=true" alt="pour-le-hommes's Streaks">
</div>

<div align="center">
  <br>
  <h2>🐍 My Contributions 🐍</h2>

  <img alt="snake eating my contributions" src="https://raw.githubusercontent.com/pour-le-hommes/pour-le-hommes/output/github-contribution-grid-snake.svg" />
  
  <br/><br/><br/>
</div>

# My Personal System Architecture
```mermaid
graph TD
    subgraph Clients["Clients"]
        TauriApp["Desktop App and Mobile App (full I/O)"]
        AppData["AppData (Local Conversations & Triggers)"]
        Website["Personal Website pourterra.com"]
    end
    subgraph Backends["Serverless Backends"]
        BE1["First Serverless Backend (LLMs)"]
        BE2["Second Serverless Backend (LifeUp)"]
        BlogBE["Blog Serverless Backend"]
    end
    subgraph Agents["Agent Tooling"]
        TerraCode["TerraCode (AI Coding Agent)"]
        TerraMCP["TerraMCP (Personal MCP Hub)"]
        LifeUpMCP["LifeUp MCP (Local Network Bridge)"]
    end
    subgraph Libraries["Libraries"]
        AreteEngine["Arete Engine (Gamification Rules)"]
    end
    subgraph External["External Services"]
        LifeUpSDK["LifeUp SDK"]
        Supabase["Supabase"]
        LLMProviders["Groq, Gemini, OpenRouter, Cloudflare"]
        EmailService["Email Service (Mailgun)"]
        Obsidian["Obsidian Vaults"]
        GitHubAction["GitHub Action (Daily Report)"]
    end

    LifeUpSDK -- Fetch LifeUp Data --> TauriApp
    TauriApp -- Send Tasks --> LifeUpSDK
    TauriApp -- Send LifeUp Data Sync --> BE2
    TauriApp <-- For LLM Conversations --> BE1
    TauriApp <-- For LifeUp Analytics & Pending Tasks Drain --> BE2
    TauriApp <-- For LLM and Analytics Caching --> AppData
    Website <-- For LLM Conversations --> BE1
    BlogBE -- Fetch Blog Posts --> Website
    BlogBE <-- For Blog Data --> Supabase
    BE1 <-- For GenAI Generation --> LLMProviders
    BE1 <-- For GenAI Data --> Supabase
    BE2 -- Fetch Tasks for LLM Tools --> BE1
    BE2 <-- For Email Report Generation --> BE1
    BE2 <-- For LifeUp Data --> Supabase
    BE2 -- Send Email Report --> EmailService
    GitHubAction -- Send Email Report Request --> BE2
    TerraCode <-- For Agent Tools --> TerraMCP
    TerraCode <-- For Agent Tools --> LifeUpMCP
    TerraCode <-- For GenAI Generation --> LLMProviders
    TerraCode -- Fetch Sessions, Memory & Metrics --> TerraMCP
    TerraMCP -- Send Pending Tasks --> BE2
    BE2 -- Fetch Tasks & Skills --> TerraMCP
    TerraMCP <-- For Notes --> Obsidian
    LifeUpSDK -- Fetch Tasks & Skills --> LifeUpMCP
    LifeUpMCP -- Send Tasks --> LifeUpSDK
    AreteEngine -. Reward Formulas .-> TauriApp
    AreteEngine -. Reward Formulas .-> LifeUpMCP
```
#### Connection Semantics

- `Send`: Subject A owns the data and actively transmits it to Subject B without solicitation. B does not request anything—A initiates the transfer. B only acknowledges receipt (success/failure), not transformation or response.
- `Fetch`: Subject B owns the data, and Subject A initiates a request to receive it. B does not learn anything about A in the process—it simply fulfills the request. The interaction is one-way in function but initiated by the consumer.
- `For`: A and B engage in mutual processing. The request leads to transformation or computation on both ends. Data, context, or state changes are involved in either or both systems. This is a purpose-driven collaboration.
- `Dotted line`: A is a library that B bundles at build time. No request happens at runtime; B runs A's logic locally, so B only picks up A's changes when it upgrades to a newer version.
- `LLM (Large Language Model)`: Narrow-scope, text-focused generative AI. Includes dialogue, summarization, and RAG operations like vector embedding or function calling—as long as they remain in the service of textual reasoning or output. Image, speech, or video tasks are excluded.
- `GenAI (Generative AI)`: Broad-scope, multi-modal generation. Encompasses all generative domains: text, audio, image, video. LLMs are a subset of GenAI, but not synonymous with it. Use when referring to the infrastructure or request path involving any generative capability.

#### Device Context

- **TauriApp (Desktop and Mobile)**: Full read/write access to LifeUp SDK, and writes to Supabase through both serverless backends

#### Agent Context

- **TerraMCP**: Never touches the LifeUp SDK directly. It queues tasks in the Second Serverless Backend, and the TauriApp drains that queue into LifeUp on its next sync.
- **LifeUp MCP**: Talks to the LifeUp SDK directly over the local network, so it only works when the phone is reachable.
- **Arete Engine**: The single source of truth for EXP and Gold. Both the TauriApp and LifeUp MCP calculate rewards with it before sending a task.

<!--
**pour-le-hommes/pour-le-hommes** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:



- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
