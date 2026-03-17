# Workshop Presentation Slides Outline
**AI Workshop: Practical Prompt Engineering for Marketing & Sales**

---

## Slide Deck Structure
**Total Duration:** ~50 minutes of presentation content (2:00–2:50 PM)
**Recommended Format:** Google Slides, PowerPoint, or Reveal.js

---

## Section 1: Welcome & Introduction (5 minutes)
**Time:** 2:00–2:05 PM

### Slide 1: Title Slide
- **Workshop Title:** AI Workshop: Practical Prompt Engineering for Marketing & Sales
- **Date:** April 2, 2024
- **Time:** 2:00–5:00 PM
- Instructor name/credentials
- Red Hat logo / company branding

### Slide 2: Welcome & Objectives
- Welcome message
- What you'll learn today:
  - How Large Language Models work
  - Prompt engineering techniques
  - Real-world marketing/sales applications
  - Hands-on practice with Open WebUI
- **Key message:** "You'll leave with practical skills you can use Monday morning."

### Slide 3: Agenda Overview
- Visual timeline of the afternoon
- Highlight hands-on lab time (emphasize practical focus)
- "This is not a lecture—you'll be doing, not just listening."

### Slide 4: Housekeeping
- WiFi credentials
- Open WebUI URL (share on screen)
- How to access materials
- Break schedule (if any)
- Questions: save for Q&A or ask anytime?

---

## Section 2: AI Foundations (15 minutes)
**Time:** 2:05–2:20 PM

### Slide 5: What is AI? (High-Level)
- Brief definition: "Artificial Intelligence"
- Types of AI:
  - Rule-based systems
  - Machine learning
  - **Generative AI** ← focus here
- Visual: AI landscape diagram

### Slide 6: What is a Large Language Model (LLM)?
- Definition: Models trained on vast text data to predict next words
- **Not** search engines
- **Not** databases
- **ARE** pattern recognition systems trained on text
- Examples: GPT-4, Claude, Llama, Granite

### Slide 7: How LLMs Work (Simplified)
- Visual diagram:
  - Input (prompt) → Model → Output (completion)
- **Key concept:** They predict the next "token" (word/subword)
- Trained on trillions of words from books, websites, code, etc.
- "Think autocomplete on steroids."

### Slide 8: Key LLM Concepts
- **Tokens:** Units of text (words, subwords, punctuation)
- **Context Window:** How much text the model can "remember" at once
- **Temperature:** Creativity dial (0.0 = predictable, 1.0 = creative)
- **System Prompts:** Instructions that guide model behavior

### Slide 9: What LLMs Are Good At
- Text generation (writing, summaries, drafts)
- Analysis (sentiment, themes, categorization)
- Translation and transformation
- Question answering (when grounded in data)
- Creative brainstorming

### Slide 10: What LLMs Are NOT Good At
- Factual precision (without grounding)
- Real-time data (knowledge cutoff dates)
- Math/logic (without tools)
- Consistency across sessions (unless designed for it)
- **Key takeaway:** "You bring domain expertise. AI amplifies it."

### Slide 11: Red Hat AI – Enterprise AI Done Right
- **Challenge:** Most AI = cloud, external APIs, data leaves your control
- **Solution:** Red Hat AI enables on-premises or hybrid deployment
- **Benefits:**
  - Host models in your own OpenShift cluster
  - Keep sensitive data internal
  - Control governance, compliance, security
  - Customize models for your industry
- Visual: Diagram showing cloud vs. on-prem vs. hybrid architecture

### Slide 12: Why This Matters for You
- **Control:** Your data, your models, your policies
- **Customization:** Fine-tune for textiles, fashion, your brand
- **Governance:** Meet regulatory requirements
- **Integration:** Plug into existing enterprise systems
- "AI doesn't have to mean giving up control."

---

## Section 3: What is Prompt Engineering? (15 minutes)
**Time:** 2:20–2:35 PM

### Slide 13: Section Divider
- **"What is Prompt Engineering?"**
- Subtitle: "The art and science of talking to AI"

### Slide 14: Prompt Engineering Defined
- **Definition:** The practice of designing inputs to get better outputs from AI
- **Why it matters:** Same model, better results—just by asking better
- **Analogy:** "Like asking a consultant a question. Vague question = vague answer."

### Slide 15: Bad Prompt vs. Good Prompt (Example 1)
**Split slide:**

**Left (Bad):**
```
"Analyze this product."
```
→ Generic, vague, unhelpful output

**Right (Good):**
```
You are a retail analyst.
Analyze this jacket for:
- Target demographic
- Pricing tier signals
- Trend alignment
Return as a table.
```
→ Specific, actionable, structured output

### Slide 16: The Anatomy of a Great Prompt
**Visual breakdown:**

```
[ROLE] You are a senior marketing strategist.
[CONTEXT] Focus on premium fashion brands.
[TASK] Improve this product description.
[CONSTRAINTS] Target audience: women 25–35.
[OUTPUT FORMAT] Return 3 headlines and 1 description.
```

**Formula:** Role + Context + Task + Constraints + Format = Great Prompt

### Slide 17: Core Technique #1 – Role Prompting
- Give the AI an identity and expertise
- Examples:
  - "You are a VP of Sales..."
  - "You are a fashion trend forecaster..."
  - "You are a competitive intelligence analyst..."
- **Why it works:** Focuses the model's "knowledge" and tone

### Slide 18: Core Technique #2 – Clear Task Definition
- Be specific about what you want
- Use action verbs: analyze, summarize, compare, generate, recommend
- Avoid vague requests: "Tell me about this."
- Better: "Identify the top 3 competitive advantages of this product."

### Slide 19: Core Technique #3 – Output Constraints
- Define structure and format:
  - Bullet points
  - Tables
  - JSON
  - Word limits
  - Number of items
- **Example:** "Return exactly 5 bullet points, each under 20 words."

### Slide 20: Core Technique #4 – Few-Shot Prompting
- Show examples of what you want
- **Template:**
  ```
  Here are examples of our brand voice:
  - Example 1: "Bold. Minimal. Architectural."
  - Example 2: "Designed for movement."

  Write a description in the same style.
  ```
- **Why it works:** AI learns patterns from examples

### Slide 21: Core Technique #5 – Iterative Refinement
- **Don't accept the first answer!**
- Refine through follow-up prompts:
  - "Make it shorter."
  - "Add more emotion."
  - "Focus on sustainability."
- Think of it as a conversation, not a one-shot query

### Slide 22: Temperature Settings (Advanced)
- **What is temperature?** Creativity control knob
- **Low (0.0–0.3):** Predictable, safe, consistent
  - Use for: data analysis, compliance, factual content
- **High (0.7–1.0):** Creative, varied, bold
  - Use for: campaigns, brainstorming, storytelling
- Visual: Slider graphic showing spectrum

---

## Section 4: Open WebUI Demo (15 minutes)
**Time:** 2:35–2:50 PM

### Slide 23: Section Divider
- **"Open WebUI Platform Demo"**
- Subtitle: "Your AI workspace for today"

### Slide 24: What is Open WebUI?
- Open-source AI chat interface
- Connects to multiple AI models (GPT, Claude, Granite, etc.)
- Features:
  - File uploads (images, PDFs, CSVs)
  - Conversation history
  - Model switching
  - Multi-user support

### Slide 25: Accessing Open WebUI
- **Display URL prominently on screen**
- Login instructions
- Account creation (if self-registration enabled)
- "Let's all log in together—don't start yet!"

### Slide 26: Interface Tour (Screenshot)
**Annotated screenshot showing:**
- Chat window
- Model selector dropdown
- Attachment button (📎)
- New chat button (+)
- Conversation history (sidebar)
- Settings (if relevant)

### Slide 27: Workspace Features
**Open WebUI provides powerful workspace tools:**

**Models**
- Create custom model configurations
- Adjust parameters (temperature, system prompts)
- Save presets for different use cases

**Knowledge**
- Upload documents for RAG (Retrieval Augmented Generation)
- Build knowledge bases from your files
- Query uploaded documents in conversations

**Prompts**
- Save and reuse effective prompts
- Create templates with variables
- Share prompts with your team

**Skills & Tools**
- Extend AI capabilities with functions
- Web search integration
- Code execution and file analysis

### Slide 28–30: Live Demo
**Note:** These are placeholders for live demonstration. Prepare to show:

**Demo 1: Basic Prompt**
- Type a simple prompt live
- Show the output
- "Notice how it responded—pretty generic, right?"

**Demo 2: Improved Prompt**
- Use the same prompt but add role, context, constraints
- Show improved output side-by-side
- "Same model, way better result. That's prompt engineering."

**Demo 3: File Upload**
- Upload a sample image (product photo)
- Ask: "Analyze this product image. Identify colors, style, and target demographic."
- Show output
- "This is multimodal AI—it can see and analyze images."

### Slide 31: Tips for Using Open WebUI Today
- **Start simple, then refine**
- **Upload files using the 📎 button**
- **Experiment freely—there are no wrong questions**
- **Save your successful prompts**
- **If stuck, raise your hand!**

---

## Section 5: Transition to Labs (2 minutes)
**Time:** 2:50–2:52 PM

### Slide 31: Lab Time Overview
- **Lab 1 (40 min):** Prompt Engineering Fundamentals
  - Learn the core techniques hands-on
  - Compare weak vs. strong prompts
  - Experiment with temperature
- **Lab 2 (40 min):** Industry Use Cases
  - Product image analysis
  - Competitor analysis
  - Sentiment analysis
  - Trend forecasting
  - Sales data analysis
- **Lab 3 (20 min):** Document Upload & RAG
  - Upload PDFs and CSVs
  - Extract insights from your data
  - Multi-document analysis

### Slide 32: Lab Guidelines
- **Follow the workshop guide** (share link or handout)
- **Work at your own pace** (skip ahead if comfortable)
- **Ask questions anytime**
- **Share interesting results** with the group
- **Take notes** on prompts that work well

### Slide 33: Let's Begin!
- **"Open your workshop guide"**
- **"Navigate to Lab 1"**
- **"Let's get hands-on!"**
- Instructor available for questions

---

## Section 6: Advanced Techniques (Optional, 10 minutes)
**Time:** 4:40–4:50 PM (if time allows)

### Slide 34: Advanced Technique #1 – Chain-of-Thought
- Ask AI to think step-by-step
- **Template:**
  ```
  Think step by step:
  1. First, analyze colors
  2. Then, correlate with sales
  3. Finally, form conclusion
  ```
- **Why it works:** Forces structured reasoning

### Slide 35: Advanced Technique #2 – Structured Outputs (JSON)
- Get machine-readable results
- **Example:**
  ```
  Return as JSON:
  {
    "colors": [],
    "price_tier": "",
    "confidence": 0.0
  }
  ```
- **Use cases:** Automation, dashboards, databases

### Slide 36: Advanced Technique #3 – Multi-Document RAG
- Upload multiple files
- Cross-reference data sources
- "Compare sales data with customer feedback—what misalignments exist?"

### Slide 37: Beyond Textiles – Cross-Industry Applications
**Table showing:**

| Use Case | Other Industries |
|----------|------------------|
| Product analysis | CPG, automotive, real estate |
| Sentiment analysis | SaaS, finance, healthcare |
| Trend forecasting | Media, stocks, consumer goods |
| Document RAG | Legal, consulting, research |

**Message:** "These are universal skills."

---

## Section 7: Wrap-Up (5 minutes)
**Time:** 4:55–5:00 PM

### Slide 38: Key Takeaways
- **AI amplifies your expertise, doesn't replace it**
- **Prompt quality = output quality**
- **Experimentation is key**
- **Start small, iterate, scale**
- **Red Hat AI enables enterprise control**

### Slide 39: What to Do Next
- Build your prompt library
- Try AI with your real data (check company policy!)
- Share learnings with your team
- Measure time savings
- Stay curious

### Slide 40: Resources You're Taking Home
- Workshop guide (PDF)
- Prompt engineering cheat sheet
- Sample data files
- Slide deck
- Prompt library templates

### Slide 41: Reflection Questions
Before you leave, think about:
- What surprised you most?
- Which use case will save you the most time?
- What data do you need to make this work internally?
- Where does governance matter for your org?

### Slide 42: Questions & Discussion
- Open floor for questions
- Share interesting prompts/results from labs
- Discuss real-world applications
- Address concerns

### Slide 43: Thank You!
- **Contact information** for follow-up questions
- **Feedback form** (optional QR code)
- **LinkedIn / email** for staying connected
- "Now go build something amazing with AI!"

### Slide 44: Bonus Slide – Additional Resources (Optional)
- Red Hat AI documentation
- Open WebUI GitHub repo
- Prompt engineering guides
- Community forums
- Recommended reading

---

## Design Recommendations

### Visual Style:
- **Clean, professional layout** (avoid clutter)
- **High contrast** for readability
- **Minimal text per slide** (use visuals)
- **Consistent branding** (Red Hat colors/fonts)
- **Code examples** in monospace font on shaded background

### Key Visuals to Include:
1. **AI architecture diagram** (user → Open WebUI → model → output)
2. **Before/after prompt comparisons** (bad vs. good)
3. **Temperature slider graphic**
4. **Prompt anatomy breakdown** (color-coded sections)
5. **Screenshot of Open WebUI interface** (annotated)
6. **Cross-industry use case table**

### Engagement Tips:
- **Use polls/questions** to check understanding
- **Live demo mistakes on purpose** to show iteration
- **Encourage participation** during demos
- **Share attendee results** during labs (if willing)

---

## Presenter Notes

### Timing Tips:
- **Build in buffer time** (don't rush)
- **Skip slides if running late** (prioritize demos and labs)
- **Extend lab time** if audience is engaged

### Common Questions to Prepare For:
1. "Can I use this with my company's proprietary data?"
   - Answer: Check your company's AI usage policy. Red Hat AI enables on-prem deployment for sensitive data.

2. "Which AI model is best?"
   - Answer: Depends on the task. GPT-4 and Claude excel at nuanced tasks; smaller models for speed/cost.

3. "How do I prevent hallucinations?"
   - Answer: Use RAG (upload documents), lower temperature, ask for citations.

4. "Is this going to replace my job?"
   - Answer: No. AI amplifies your expertise. You bring domain knowledge; AI accelerates execution.

5. "What about copyright/IP concerns?"
   - Answer: Valid concern. Use enterprise AI with proper licensing. Red Hat AI provides governance controls.

---

## Materials Checklist

Before the workshop, ensure you have:
- [ ] Slide deck finalized and tested
- [ ] Open WebUI URL accessible
- [ ] Sample data files uploaded and ready
- [ ] Workshop guide printed or digitally shared
- [ ] Prompt cheat sheet ready to distribute
- [ ] Demo prompts prepared and tested
- [ ] Backup screenshots in case live demo fails
- [ ] Feedback form/QR code ready
- [ ] Contact info for follow-up

---

**You're ready to deliver an amazing workshop! Good luck!**
