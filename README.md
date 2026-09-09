# 🎨 LLM Wiki Concept with Obsidian & Quartz

> **AI와 인간이 협업하는 개인용 지식 위키** - LLM과 관련도구를 활용해, 흩어진 단어와 생각을 정형화된 지식 그래프로 만들기.

![My Wordplay Cover](./content/assets/_cover.png)

## 🌟 Concept: LLM-Driven Incremental Build

**LLM(Gemini)이 지식의 유지보수 도우미(Maintainer)로 참여**하고 knowledge base를 구축하고, 이를 quartz SSG로 구워서 personal website를 만듭니다. 사용자가 거친 형태의 소스(`raw/`)를 던지면, LLM은 미리 정의된 스키마에 따라 이를 분해, 정제, 연결하여 최종 콘텐츠(`content/`)를 점진적으로 구축(Incremental Build)합니다.

## 🏗 Knowledge Schema & Architecture

LLM과의 원활한 협업을 위해 엄격한 디렉토리 구조와 프론트매터 스키마를 따릅니다.

### 1. Multi-Layer Structure

- `raw/`: **Immutable Source.** 웹 클리핑, 노션 수출본 등 가공되지 않은 원천 데이터.
- `content/term/`: **Atomic Knowledge.** 단일 용어나 구문이 담긴 최소 지식 단위.
- `content/concept/`: **Relational Knowledge.** 용어 간의 비교(`vs`), 클러스터(`cluster`), 원리 등을 담은 고차원 지식.

### 2. Frontmatter Schema (The LLM Contract)

LLM은 다음 필드를 기준으로 지식을 분류하고 연결합니다:

- `my_word`: **User-Owned.** 사용자의 고유한 생각이나 번역어 (LLM 수정 불가).
- `domain`: 지식의 영역 (political, economic, cultural 등).
- `related`: 지식 그래프 구성을 위한 양방향 링크 (`synonym`, `antonym`, `contrast` 등).

## 🤖 Operational Workflow (The Ingest Process)

LLM은 `GEMINI-llm-wiki.md`에 정의된 운영 지침에 따라 작업을 수행합니다.

1. **Read & Extract**: `raw/`에 새로 추가된 소스를 읽고 핵심 키워드 추출.
2. **Decomposition**: 단일 용어는 `term/`으로, 대조군이나 그룹은 `concept/`로 자동 분리.
3. **Graph Linking**: 기존 문서들을 스캔하여 새로운 문서와 관계를 맺고 `related` 필드 업데이트.
4. **Indexing**: `index.md`와 `log.md`를 갱신하여 전체 지식 지도를 최신화.

## 🛠 Tech Stack

- **Source**: Chrome Web Clipper, Notion Export
- **Brain**: Google Gemini (via Custom Schema & Instructions)
- **Editor**: Obsidian (Human-AI Interface)
- **SSG Engine**: Quartz 4 (Visual Rendering & Graph)
- **Deployment**: Github Pages

## ⚙️ Execution

### Ingesting New Sources

사용자가 `raw/`에 파일을 추가한 후 LLM에게 명령:

```text
"Ingest 해줘"
```

### Local Visualization

```bash
npx quartz build --serve
```

---

**LLM Wiki Concept**는 파편화된 정보를 체계적인 지식 자산으로 전환하는 효율적인 방법에 대한 개념입니다.
