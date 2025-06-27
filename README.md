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
    LifeUpSDK["LifeUp SDK"]
    TauriApp["Desktop App and Mobile App (full I/O)"]
    Website["Personal Website pourterra.com"]
    BE2["Second Serverless Backend (LifeUp)"]
    BE1["First Serverless Backend (LLMs + LifeUp DB)"]
    Supabase["Supabase"]
    AppData["AppData (Local Conversations & Triggers)"]
    GroqGemini["Groq, Gemini"]
    GitHubAction["GitHub Action (Daily Report)"]

    LifeUpSDK -- Fetch LifeUp Data --> TauriApp
    TauriApp -- Send Tasks (Only Desktop) --> LifeUpSDK
    TauriApp <-- For LLM Conversations --> BE1
    TauriApp <-- For LifeUp Analytics --> BE2
    TauriApp <-- For LLM and Analytics Caching --> AppData
    Website <-- For LLM Conversations --> BE1
    BE1 <-- For GenAI Generation --> GroqGemini
    BE1 <-- For GenAI Data --> Supabase
    BE2 <-- For Email Report Generation --> BE1
    BE2 <-- For LifeUp Data --> Supabase
    GitHubAction -- Send Email Report Request --> BE2
```
#### Connection Semantics

- `Send`: Subject A owns the data and actively transmits it to Subject B without solicitation. B does not request anything—A initiates the transfer. B only acknowledges receipt (success/failure), not transformation or response.
- `Fetch`: Subject B owns the data, and Subject A initiates a request to receive it. B does not learn anything about A in the process—it simply fulfills the request. The interaction is one-way in function but initiated by the consumer.
- `For`: A and B engage in mutual processing. The request leads to transformation or computation on both ends. Data, context, or state changes are involved in either or both systems. This is a purpose-driven collaboration.
- `LLM (Large Language Model)`: Narrow-scope, text-focused generative AI. Includes dialogue, summarization, and RAG operations like vector embedding or function calling—as long as they remain in the service of textual reasoning or output. Image, speech, or video tasks are excluded.
- `GenAI (Generative AI)`: Broad-scope, multi-modal generation. Encompasses all generative domains: text, audio, image, video. LLMs are a subset of GenAI, but not synonymous with it. Use when referring to the infrastructure or request path involving any generative capability.

#### Device Context

- **TauriApp (Desktop only)**: Full read/write access to LifeUp SDK
- **TauriApp (Mobile)**: Read-only to LifeUp SDK

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
