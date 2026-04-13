<div align="center">

<img
  src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,12,24&height=200&section=header&text=Deepak%20Pathik&fontSize=60&fontColor=fff&animation=twinkling&fontAlignY=35&desc=Full-Stack%20Developer%20%E2%80%A2%20AI%20Engineer%20%E2%80%A2%20Open-Source%20Contributor&descAlignY=55&descSize=18"
  width="100%"
  alt="Header Banner"
/>

<img
  src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=21&duration=3000&pause=800&color=22C55E&center=true&vCenter=true&repeat=true&width=750&height=50&lines=Patch+Merged+into+Linux+Kernel+erofs-utils;GSoC+2026+Applicant+%E2%80%94+Linux+Kernel+EROFS;Building+AI-Powered+Full-Stack+Applications;Engineering+RAG+%26+Agentic+AI+Pipelines"
  alt="Typing SVG"
/>

<br/>

<img src="https://komarev.com/ghpvc/?username=deepakpathik&label=Profile+Views&color=22C55E&style=flat-square&abbreviated=true" alt="Profile Views"/>
&nbsp;
<img src="https://img.shields.io/github/followers/deepakpathik?label=Followers&style=flat-square&color=0EA5E9&labelColor=0f172a" alt="Followers"/>
&nbsp;
<img src="https://img.shields.io/badge/GSoC_2026-Proposal_Submitted-F97316?style=flat-square&logo=google&logoColor=white" alt="GSoC 2026"/>
&nbsp;
<img src="https://img.shields.io/badge/Status-Open_To_Work-22C55E?style=flat-square&logo=checkmarx&logoColor=white" alt="Open To Work"/>

<br/><br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/deepakpathik)
[![Portfolio](https://img.shields.io/badge/Portfolio-0f172a?style=for-the-badge&logo=vercel&logoColor=22C55E)](https://deepakpathik.dev)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:deepakpathik2005@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/deepakpathik)
[![LeetCode](https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/deepakpathik)

</div>

---

<img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExbjRiaXQybXdrdGtsMG1rdmlqdHFxMHc2d2Q4NWpxM3g5d3E0dG5nOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/MD0svLSDeudszrNrp0/giphy.gif" alt="Developer Banner" width="100%" />

## <img src="https://cdn.simpleicons.org/files/22C55E" width="20" height="20" valign="middle"/> About

```python
class DeepakPathik:
    role     = "Full-Stack Developer & AI Engineer"
    location = "Pune, Maharashtra, India"
    school   = "Newton School of Technology (ADYPU) — B.Tech AI & ML (2024–2028)"

    specialization = [
        "MERN Stack · Next.js · REST APIs · Real-Time Systems",
        "AI-Powered Applications & Agentic Pipelines (RAG, LangChain)",
        "Linux Kernel Systems Programming (C, POSIX Threads)",
        "Mobile Development with React Native & Expo",
    ]

    currently = [
        "AI Agent Developer Intern  @ Apogee Tech Global Inc. (Feb 2026 – Present)",
        "GSoC 2026 Applicant        @ Linux Kernel Org — EROFS Filesystem (Results: May 8)",
        "Summer of Bitcoin 2026     @ Developer Track — Reached Week 3 Challenge Round",
    ]

    open_source = [
        "Linux Kernel erofs-utils  — Patch MERGED: fix fd leak in erofs_metamgr_init() [d6d0b8a]",
        "Linux Kernel erofs-utils  — GSoC 2026: Multi-threaded fsck.erofs decompression",
        "Turborepo                 — Monorepo tooling contributions",
        "GoFr                      — Go application framework contributions",
    ]

    open_to = "Full-Stack AI Engineering · Systems Programming · Open-Source Collaboration"
```

---

## <img src="https://cdn.simpleicons.org/linux/22C55E" width="20" height="20" valign="middle"/> Google Summer of Code 2026 — Proposal Submitted

> **Project:** Multi-threaded Decompression Support in `fsck.erofs`
> **Organisation:** Linux Kernel — EROFS Filesystem
> **Mentors:** Yifan Zhao `@SToPire`, Chunhai Guo `@speedan1`, Gao Xiang `@hsiangkao`
> **Results:** May 8, 2026

### ✅ Merged Patch — Pre-GSoC Upstream Contribution

> **[`erofs-utils: lib: fix fd leak in erofs_metamgr_init()`](https://github.com/erofs/erofs-utils/commit/d6d0b8a31354104ede464568fc1253c51b9ec36c)**
> Commit `d6d0b8a` · authored by `deepakpathik` · signed-off by `hsiangkao` (Gao Xiang, core EROFS maintainer)

In `erofs_metamgr_init()`, `erofs_tmpfile()` stores a file descriptor in `m2gr->vf.fd`. If the subsequent `erofs_buffer_init()` call fails, the function returns `-ENOMEM` without closing that fd — leaking it permanently. The caller `erofs_metadata_init()` only frees the `m2gr` struct at `err_free`, leaving no remaining reference to close the fd.

**Fix:** Mirror the success path's `erofs_io_close(&m2gr->vf)` call on the error path before returning.

```diff
  if (!m2gr->bmgr) {
+     erofs_io_close(&m2gr->vf);
      return -ENOMEM;
  }
```

<div align="center">
  <img src="https://img.shields.io/badge/File-lib%2Fmetabox.c-A8B9CC?style=flat-square&logo=c&logoColor=white"/>
  <img src="https://img.shields.io/badge/+3_−1_lines-Merged-22C55E?style=flat-square&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/Signed--off--by-hsiangkao-F97316?style=flat-square&logo=linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Mailing_List-lore.kernel.org%2Fr%2F202604021...-0EA5E9?style=flat-square"/>
</div>

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <b>The Problem</b><br/>
      <code>fsck.erofs</code> runs all decompression on a single thread — leaving multi-core CPUs massively underutilized on production Android images, OTA pipelines, and container runtimes.
    </td>
    <td width="50%" valign="top">
      <b>The Solution</b><br/>
      Wire the existing <code>erofs_workqueue</code> thread pool into the decompression path, enabling N pclusters to decompress concurrently across N worker threads with a new <code>--jobs=N</code> flag.
    </td>
  </tr>
  <tr>
    <td valign="top">
      <b>Key Technical Insight</b><br/>
      <code>z_erofs_decompress()</code> operates on a self-contained <code>z_erofs_decompress_req</code> — no shared mutable state. Output written via <code>pwrite()</code> to non-overlapping offsets. Zero inter-thread locks during decompression.
    </td>
    <td valign="top">
      <b>Expected Impact</b><br/>
      3–4× extraction speedup on 4-core systems for CPU-bound images. Mirrors parallel decompression already present in the Linux kernel EROFS driver, closing the gap in userspace tools.
    </td>
  </tr>
</table>

<div align="center">
  <img src="https://img.shields.io/badge/Language-C-A8B9CC?style=flat-square&logo=c&logoColor=white"/>
  <img src="https://img.shields.io/badge/POSIX_Threads-pthreads-22C55E?style=flat-square"/>
  <img src="https://img.shields.io/badge/Project_Size-350_Hours-0EA5E9?style=flat-square"/>
  <img src="https://img.shields.io/badge/Algorithms-LZ4_·_LZMA_·_DEFLATE_·_Zstd-F97316?style=flat-square"/>
  <img src="https://img.shields.io/badge/Testing-TSAN_%2F_ASAN-EC4899?style=flat-square"/>
</div>

---

## <img src="https://cdn.simpleicons.org/bitcoin/F7931A" width="20" height="20" valign="middle"/> Summer of Bitcoin 2026 — Developer Track

> **Program:** Summer of Bitcoin 2026 · Competitive Bitcoin open-source internship
> **Track:** Developer Track · Challenge Round (Feb 16 – Mar 15, 2026)

One hard Bitcoin project challenge per week, evaluated against a competitive percentile cutoff. Only top-scoring candidates advance each week.

| Round | Status | Period |
|-------|--------|--------|
| Challenge Round Invite | ✅ Qualified | Feb 16, 2026 |
| Week 1 Challenge | ✅ Passed | Feb 26, 2026 |
| Week 2 Challenge | ✅ Passed | Mar 9, 2026 |
| Week 3 Challenge | Eliminated | Mar 21, 2026 |

<div align="center">
  <img src="https://img.shields.io/badge/Bitcoin-Developer_Track-F7931A?style=flat-square&logo=bitcoin&logoColor=white"/>
  <img src="https://img.shields.io/badge/Week_1-Passed_✓-22C55E?style=flat-square"/>
  <img src="https://img.shields.io/badge/Week_2-Passed_✓-22C55E?style=flat-square"/>
  <img src="https://img.shields.io/badge/Week_3-Reached-0EA5E9?style=flat-square"/>
  <img src="https://img.shields.io/badge/Grokking_Bitcoin-Studied-F97316?style=flat-square"/>
</div>

---

## <img src="https://cdn.simpleicons.org/todoist/22C55E" width="20" height="20" valign="middle"/> Currently Building

| Project | Stack | Status |
|---------|-------|--------|
| `fsck.erofs` Multi-threaded Decompression | C · POSIX · erofs-utils · Linux Kernel | ![PROPOSED](https://img.shields.io/badge/GSoC_Proposed-F97316?style=flat-square) |
| SaaS AI Agent Platform | Docker · VPS · OpenClaw · SaaS Architecture | ![ACTIVE](https://img.shields.io/badge/ACTIVE-22C55E?style=flat-square) |
| Agentic RAG Pipelines | LangGraph · Pinecone · Google Embeddings | ![EXPLORING](https://img.shields.io/badge/EXPLORING-0EA5E9?style=flat-square) |

---

## <img src="https://cdn.simpleicons.org/stackblitz/22C55E" width="20" height="20" valign="middle"/> Tech Stack

<table>
  <tr>
    <td align="center" width="130"><b>Languages</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=ts,js,python,c,html,css&theme=dark" height="36" alt="Languages"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>AI &amp; ML</b></td>
    <td>
      <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white" height="28"/>
      <img src="https://img.shields.io/badge/LangGraph-F97316?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/RAG_Pipelines-22C55E?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/Pinecone-0EA5E9?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/Gemini_API-4285F4?style=flat-square&logo=google&logoColor=white" height="28"/>
      <img src="https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white" height="28"/>
      <img src="https://img.shields.io/badge/AI_Safety_Guardrails-EC4899?style=flat-square" height="28"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>Backend</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=nodejs,express,fastapi,nestjs&theme=dark" height="36" alt="Backend"/>
      &nbsp;
      <img src="https://img.shields.io/badge/REST_APIs-22C55E?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/WebSockets-010101?style=flat-square&logo=socketdotio&logoColor=white" height="28"/>
      <img src="https://img.shields.io/badge/JWT-black?style=flat-square&logo=JSON%20web%20tokens" height="28"/>
      <img src="https://img.shields.io/badge/OAuth_2.0-EB5424?style=flat-square&logo=auth0&logoColor=white" height="28"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>Frontend &amp; Mobile</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=react,nextjs,tailwind,flutter&theme=dark" height="36" alt="Frontend"/>
      &nbsp;
      <img src="https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black" height="28"/>
      <img src="https://img.shields.io/badge/Expo-1C1E24?style=flat-square&logo=expo&logoColor=white" height="28"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>Databases</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=postgres,mongodb,mysql,firebase,supabase&theme=dark" height="36" alt="Databases"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Prisma_ORM-3982CE?style=flat-square&logo=prisma&logoColor=white" height="28"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>Cloud &amp; DevOps</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=aws,gcp,docker,vercel,netlify,git,githubactions&theme=dark" height="36" alt="Cloud and DevOps"/>
      &nbsp;
      <img src="https://img.shields.io/badge/VPS-SaaS_Arch-22C55E?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/Turborepo-EF4444?style=flat-square&logo=turborepo&logoColor=white" height="28"/>
    </td>
  </tr>
  <tr>
    <td align="center"><b>Systems</b></td>
    <td>
      <img src="https://img.shields.io/badge/Linux_Kernel-FCC624?style=flat-square&logo=linux&logoColor=black" height="28"/>
      <img src="https://img.shields.io/badge/POSIX_Threads-22C55E?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/EROFS_Filesystem-0EA5E9?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/Atomics_%2F_Mutexes-F97316?style=flat-square" height="28"/>
      <img src="https://img.shields.io/badge/TSAN_%2F_ASAN-EC4899?style=flat-square" height="28"/>
    </td>
  </tr>
</table>

---

## <img src="https://cdn.simpleicons.org/github/22C55E" width="20" height="20" valign="middle"/> Featured Projects

<table>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/deepakpathik/askmynotes">AskMyNotes — AI Study Assistant</a></h3>
      <p>Corrective RAG (CRAG) pipeline · semantic search with Pinecone · real-time chat + voice (STT/TTS) · quiz generation · persistent memory via LangGraph</p>
      <img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white"/>
      <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white"/>
      <img src="https://img.shields.io/badge/Pinecone-0EA5E9?style=flat-square"/>
      <img src="https://img.shields.io/badge/Google_Gemini-4285F4?style=flat-square&logo=google&logoColor=white"/>
      <br/><br/>
      <a href="https://github.com/deepakpathik/askmynotes"><img src="https://img.shields.io/badge/Source-181717?style=flat-square&logo=github&logoColor=white"/></a>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/deepakpathik/web-rag">WEB-RAG AI Research Assistant</a></h3>
      <p>Tool-augmented agent · real-time web search + LLM synthesis · Google Custom Search API · graceful handling of insufficient data</p>
      <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
      <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
      <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white"/>
      <br/><br/>
      <a href="https://github.com/deepakpathik/web-rag"><img src="https://img.shields.io/badge/Source-181717?style=flat-square&logo=github&logoColor=white"/></a>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/deepakpathik/adaptive-fitness-ai">Adaptive Fitness AI Chatbot</a></h3>
      <p>Mobile-first AI coaching · context-aware conversations · session memory + prompt orchestration · AI safety guardrails filtering non-fitness queries</p>
      <img src="https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black"/>
      <img src="https://img.shields.io/badge/Node.js-6DA55F?style=flat-square&logo=node.js&logoColor=white"/>
      <img src="https://img.shields.io/badge/Gemini_API-4285F4?style=flat-square&logo=google&logoColor=white"/>
      <br/><br/>
      <a href="https://github.com/deepakpathik/adaptive-fitness-ai"><img src="https://img.shields.io/badge/Source-181717?style=flat-square&logo=github&logoColor=white"/></a>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/erofs/erofs-utils/commit/d6d0b8a31354104ede464568fc1253c51b9ec36c">erofs-utils — Upstream Kernel Patch</a></h3>
      <p>✅ <b>MERGED</b> · Fix fd leak in <code>erofs_metamgr_init()</code> · commit <code>d6d0b8a</code> · signed-off by core maintainer <code>hsiangkao</code> · +3 −1 lines in <code>lib/metabox.c</code></p>
      <img src="https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=white"/>
      <img src="https://img.shields.io/badge/Linux_Kernel-FCC624?style=flat-square&logo=linux&logoColor=black"/>
      <img src="https://img.shields.io/badge/EROFS-0EA5E9?style=flat-square"/>
      <br/><br/>
      <a href="https://github.com/erofs/erofs-utils/commit/d6d0b8a31354104ede464568fc1253c51b9ec36c"><img src="https://img.shields.io/badge/View_Commit-d6d0b8a-22C55E?style=flat-square&logo=github&logoColor=white"/></a>
      <a href="https://lore.kernel.org/r/20260402112645.49711-1-deepakpathik2005@gmail.com"><img src="https://img.shields.io/badge/Mailing_List-linux--erofs-F97316?style=flat-square&logo=linux&logoColor=white"/></a>
    </td>
  </tr>
</table>

<div align="center">
  <a href="https://github.com/deepakpathik?tab=repositories">
    <img src="https://img.shields.io/badge/View_All_Repositories-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
</div>

---

## <img src="https://cdn.simpleicons.org/githubactions/22C55E" width="20" height="20" valign="middle"/> GitHub Analytics

<div align="center">

<img
  src="https://github-readme-stats-bsaonsnye-deepakpathiks-projects.vercel.app/api?username=deepakpathik&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github&include_all_commits=true&count_private=true"
  height="195"
  alt="GitHub Stats"
/>
&nbsp;&nbsp;
<img
  src="https://github-readme-stats-bsaonsnye-deepakpathiks-projects.vercel.app/api/top-langs/?username=deepakpathik&layout=compact&theme=tokyonight&hide_border=true&langs_count=8"
  height="195"
  alt="Top Languages"
/>

<br/>

<img
  src="https://streak-stats.demolab.com?user=deepakpathik&theme=tokyonight&hide_border=true&border_radius=8&ring=22C55E&fire=F97316&currStreakLabel=22C55E"
  height="195"
  alt="GitHub Streak"
/>

<br/>

<img
  src="https://github-readme-activity-graph.vercel.app/graph?username=deepakpathik&bg_color=1a1b27&color=22C55E&line=0EA5E9&point=F97316&area=true&hide_border=true&radius=8"
  width="100%"
  alt="Activity Graph"
/>

</div>

---

## <img src="https://cdn.simpleicons.org/speedtest/22C55E" width="20" height="20" valign="middle"/> Key Metrics

<div align="center">

<img src="https://img.shields.io/badge/Kernel_Patch-MERGED_d6d0b8a-22C55E?style=for-the-badge&labelColor=0f172a" alt="Patch Merged"/>
<img src="https://img.shields.io/badge/GSoC_2026-Proposal_Submitted-F97316?style=for-the-badge&labelColor=0f172a" alt="GSoC"/>
<img src="https://img.shields.io/badge/Speedup_Target-3–4×_on_4_Cores-22C55E?style=for-the-badge&labelColor=0f172a" alt="Speedup"/>
<img src="https://img.shields.io/badge/Project_Size-350_Hours-0EA5E9?style=for-the-badge&labelColor=0f172a" alt="Hours"/>
<img src="https://img.shields.io/badge/Open_Source-Turborepo_%26_GoFr-EC4899?style=for-the-badge&labelColor=0f172a" alt="OSS"/>
<img src="https://img.shields.io/badge/Game_Jam-1st_Place_Hyperlume-FCC624?style=for-the-badge&labelColor=0f172a" alt="Game Jam"/>

</div>

---

## <img src="https://cdn.simpleicons.org/linkedin/22C55E" width="20" height="20" valign="middle"/> Experience & Open-Source

<table width="100%">
  <tr>
    <td>
      <img src="https://img.shields.io/badge/Patch_MERGED-erofs--utils_lib%2Fmetabox.c-22C55E?style=flat-square&logo=linux&logoColor=white"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Commit_d6d0b8a-Signed_off_by_hsiangkao-0f172a?style=flat-square"/>
      &nbsp;
      <a href="https://github.com/erofs/erofs-utils/commit/d6d0b8a31354104ede464568fc1253c51b9ec36c"><img src="https://img.shields.io/badge/View-Commit-F97316?style=flat-square&logo=github&logoColor=white"/></a>
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/GSoC_2026_Applicant-Linux_Kernel_%2F_EROFS-F97316?style=flat-square&logo=linux&logoColor=white"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Results_May_8_2026-Proposal_Submitted-0f172a?style=flat-square"/>
      &nbsp;
      <img src="https://img.shields.io/badge/May_2026–Sep_2026-Remote-0f172a?style=flat-square"/>
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/AI_Agent_Developer_Intern-Apogee_Tech_Global_Inc.-22C55E?style=flat-square&logo=google&logoColor=white"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Feb_2026–Present-Hybrid_Bangalore-0f172a?style=flat-square"/>
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/Summer_of_Bitcoin_2026-Developer_Track_·_Reached_Week_3-F7931A?style=flat-square&logo=bitcoin&logoColor=white"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Feb_2026–Mar_2026-Competitive_Challenge_Round-0f172a?style=flat-square"/>
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/Open_Source_Contributor-Turborepo_%26_GoFr-0EA5E9?style=flat-square&logo=github&logoColor=white"/>
      &nbsp;
      <img src="https://img.shields.io/badge/Large--Scale_Codebases-Ongoing-0f172a?style=flat-square"/>
    </td>
  </tr>
</table>

---

## <img src="https://cdn.simpleicons.org/github/22C55E" width="20" height="20" valign="middle"/> Contribution Graph

<div align="center">
  <picture>
    <source
      media="(prefers-color-scheme: dark)"
      srcset="https://raw.githubusercontent.com/deepakpathik/deepakpathik/output/github-contribution-grid-snake-dark.svg"
    />
    <source
      media="(prefers-color-scheme: light)"
      srcset="https://raw.githubusercontent.com/deepakpathik/deepakpathik/output/github-contribution-grid-snake.svg"
    />
    <img
      alt="Contribution Snake Animation"
      src="https://raw.githubusercontent.com/deepakpathik/deepakpathik/output/github-contribution-grid-snake-dark.svg"
      width="100%"
    />
  </picture>
</div>

---

## <img src="https://cdn.simpleicons.org/maildotru/22C55E" width="20" height="20" valign="middle"/> Connect

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/deepakpathik)
[![Email](https://img.shields.io/badge/Email-deepakpathik2005%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:deepakpathik2005@gmail.com)
[![Mailing List](https://img.shields.io/badge/linux--erofs-Mailing_List-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://lore.kernel.org/linux-erofs/)

</div>

---

<img
  src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,12,24&height=100&section=footer"
  width="100%"
  alt="Footer"
/>
