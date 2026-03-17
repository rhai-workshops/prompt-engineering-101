# AI Workshop: Practical Prompt Engineering for Marketing & Sales
**Welcome!** This hands-on workshop will teach you how to use AI effectively for real-world marketing and sales tasks.

---

## What You'll Learn Today

By the end of this workshop, you'll be able to:
- Understand how Large Language Models (LLMs) work
- Write effective prompts that get better results
- Upload and analyze images, documents, and data
- Apply AI to marketing, sales, and competitive analysis
- Extract insights from customer feedback and sales data

**No coding required.** Just your expertise and curiosity.

---

## Workshop Agenda

| Time | Activity |
|------|----------|
| 2:00–2:20 | Intro to AI & Large Language Models |
| 2:20–2:35 | What is Prompt Engineering? |
| 2:35–2:50 | Open WebUI Platform Demo |
| 2:50–3:40 | **LAB 1:** Prompt Engineering Basics |
| 3:40–4:20 | **LAB 2:** Industry Use Cases |
| 4:20–4:40 | **LAB 3:** Working with Documents (RAG) |
| 4:40–4:55 | Advanced Techniques |
| 4:55–5:00 | Wrap-up & Next Steps |

---

## Getting Started

### Accessing the Platform

1. Open your browser and navigate to: **[Workshop URL will be shared]**
2. Create an account or log in with provided credentials
3. You'll see the Open WebUI interface with a chat window

### Open WebUI Quick Tour

**Key features:**
- **Chat window:** Type your prompts here
- **Model selector:** Choose different AI models (top of screen)
- **Attachment button (📎):** Upload images, PDFs, or CSV files
- **New chat (+):** Start fresh conversations
- **History (sidebar):** Return to previous conversations

---

## Lab 1: Prompt Engineering Fundamentals

**Goal:** Learn how the *way* you ask matters more than *what* you ask.

### Exercise 1.1: Basic Prompt (The Wrong Way)

Copy and paste this prompt:

```
Analyze this product description and suggest improvements.

Product: "Our jacket is made from high-quality materials. It's stylish and comfortable."
```

**What happens?**
- Generic, vague suggestions
- No specific direction
- Could apply to any product

---

### Exercise 1.2: Add Role + Context (Better!)

Now try this:

```
You are a senior fashion marketing strategist with 10 years of experience in premium urban brands.

Improve the following product description for a women's jacket targeting urban professionals aged 25–35. Focus on emotional appeal and lifestyle fit.

Product: "Our jacket is made from high-quality materials. It's stylish and comfortable."
```

**What changed?**
- More targeted suggestions
- Tone matches your audience
- Specific improvements

**Key Takeaway:** Give the AI a role and context.

---

### Exercise 1.3: Add Output Constraints (Even Better!)

Now add structure:

```
You are a senior fashion marketing strategist with 10 years of experience in premium urban brands.

Improve the following product description for a women's jacket targeting urban professionals aged 25–35.

Product: "Our jacket is made from high-quality materials. It's stylish and comfortable."

Return:
- 3 headline options (max 10 words each)
- 1 optimized product description (max 100 words)
- 5 SEO keywords
- 1 Instagram caption suggestion
```

**What changed?**
- Structured, actionable output
- Ready to use immediately
- Predictable format

**Key Takeaway:** Tell the AI exactly what format you want.

---

### Exercise 1.4: Few-Shot Prompting (Show Examples)

Try this approach:

```
You are a copywriter for a minimalist fashion brand.

Our brand voice is:
- "Architectural. Refined. Made for movement."
- "Less is more. Every detail counts."
- "Designed for the modern professional."

Write a product description for a black merino wool sweater in the same voice.
```

**What changed?**
- AI matches your brand voice
- Consistent tone across outputs
- Feels authentic to your brand

**Key Takeaway:** Show examples of what you want.

---

### Exercise 1.5: Temperature Settings (Bonus)

**What is Temperature?**
- Controls creativity vs. consistency
- Low (0.0–0.3): Predictable, conservative
- High (0.7–1.0): Creative, varied

**Try this experiment:**

1. Set temperature to **0.2** (if available in settings)
2. Run: "Write 3 product taglines for a luxury handbag."
3. Set temperature to **0.9**
4. Run the same prompt again

**Notice the difference?**
- Low temp = safe, professional
- High temp = bold, unexpected

**When to use which?**
- Low: Product specs, data analysis, compliance
- High: Creative campaigns, brainstorming, storytelling

---

## Lab 2: Industry Use Cases

**Goal:** Apply prompt engineering to real marketing and sales scenarios.

Choose one or more scenarios that interest you:

---

### Scenario A: Product Image Analysis

**Use Case:** Analyze which visual elements drive sales.

**Step 1:** Upload 3–5 product images (clothing, accessories, etc.)

**Step 2:** Use this prompt:

```
You are a retail data analyst specializing in visual merchandising.

Analyze the uploaded product images and identify:
- Dominant colors and color palettes
- Silhouette types (fitted, oversized, structured, etc.)
- Key design details (buttons, zippers, patterns, textures)
- Likely target demographic

Return results in a table format.
```

**Step 3:** Follow-up question:

```
Based on this analysis, what visual patterns might correlate with higher sales performance? What should we test in our next collection?
```

**What you're learning:** Visual analysis at scale without manual tagging.

---

### Scenario B: Competitor Analysis

**Use Case:** Understand competitor positioning from product photos.

**Step 1:** Upload competitor product images from their website

**Step 2:** Use this prompt:

```
You are a competitive intelligence analyst in fashion retail.

Analyze these competitor product images and identify:
- Pricing signals (luxury vs. mass market indicators)
- Trend alignment (which current trends are they following?)
- Differentiation opportunities (gaps we could exploit)
- Target audience signals

Provide 3 actionable recommendations for our product team.
```

**What you're learning:** Fast competitive research without manual review.

---

### Scenario C: Customer Feedback Sentiment Analysis

**Use Case:** Extract insights from customer reviews or feedback.

**Step 1:** Upload `customer-feedback.csv` (provided)

**Step 2:** Use this prompt:

```
You are a customer insights analyst.

Analyze this customer feedback dataset and return:

1. Top 5 positive themes (what customers love)
2. Top 5 complaints or issues
3. Sentiment breakdown (% positive, neutral, negative)
4. Suggested product improvements (prioritized by frequency)

Format as a clear, actionable report.
```

**What you're learning:** Turn qualitative data into quantitative insights.

---

### Scenario D: Fashion Trend Forecasting

**Use Case:** Identify emerging trends before they hit mass market.

**Step 1:** Upload street-style or fashion show images

**Step 2:** Use this prompt:

```
You are a fashion trend forecaster with expertise in translating runway trends to commercial products.

Analyze these images and identify emerging signals:
- Color trends (specific hex codes or palettes if possible)
- Fabric and texture trends
- Silhouette and fit trends
- Accessory trends

For each trend, predict:
- Time to mass market adoption (3 months, 6 months, 12 months)
- Potential customer segments
- Price point suitability

Return as a trend report.
```

**What you're learning:** Data-driven trend analysis.

---

### Scenario E: Virtual Prototyping (Text-Based)

**Use Case:** Explore design variations quickly.

**Step 1:** Use this prompt (no upload needed):

```
You are a fashion designer specializing in outerwear.

Generate 3 detailed design variations for a women's trench coat:

1. **Minimalist Version:** Clean lines, monochrome, architectural
2. **Streetwear Version:** Oversized, utilitarian details, bold
3. **Luxury Version:** Premium fabrics, refined details, timeless

For each, describe:
- Fabric choices
- Key design details
- Color palette
- Hardware/finishing
- Target price point
- Ideal customer profile
```

**What you're learning:** Fast ideation and prototyping.

---

### Scenario F: Sales Data Analysis

**Use Case:** Analyze sales trends from CSV data.

**Step 1:** Upload `sales-data.csv` (provided)

**Step 2:** Use this prompt:

```
You are a sales operations analyst.

Based on the uploaded sales data, analyze:
- Top 5 performing products (by revenue and units sold)
- Geographic trends (which regions over/under-perform?)
- Seasonal patterns
- Product categories with declining sales

Suggest 3 proactive actions for distribution or inventory management.
```

**What you're learning:** Turn spreadsheets into strategic insights.

---

## Lab 3: Document Upload & RAG (Retrieval Augmented Generation)

**Goal:** Use AI to analyze your internal documents.

### What is RAG?

**RAG = Retrieval Augmented Generation**
- Upload a document
- AI reads and references it
- Responses are *grounded* in your data
- Reduces hallucination

---

### Exercise 3.1: Upload a Sales Report

**Step 1:** Upload `quarterly-sales-report.pdf` (provided)

**Step 2:** Use this prompt:

```
Based only on the uploaded document, answer the following:

1. What were the top-performing product categories last quarter?
2. What geographic trends stand out?
3. Which customer segments showed growth vs. decline?

Cite specific data points from the report.
```

**Key difference:** The AI will reference *your* data, not make things up.

---

### Exercise 3.2: Strategic Analysis

**Step 1:** Continue with the same uploaded PDF

**Step 2:** Use this prompt:

```
You are the VP of Sales reviewing this quarterly report.

Given the data in this document, suggest 3 proactive actions we should take:
- Distribution strategy changes
- Inventory adjustments
- Marketing focus shifts

For each, explain the data-driven rationale.
```

**What you're learning:** Turn reports into action plans.

---

### Exercise 3.3: Multi-Document Context (Advanced)

**Step 1:** Upload both:
- `sales-data.csv`
- `customer-feedback.csv`

**Step 2:** Use this prompt:

```
You are a business analyst.

Cross-reference the sales data and customer feedback:
- Do high-selling products have positive or negative feedback?
- Are there low-selling products with strong positive feedback? (opportunity?)
- What misalignments exist between what sells and what customers want?

Provide 3 strategic recommendations.
```

**What you're learning:** Connect multiple data sources.

---

## Advanced Techniques

### 1. Chain-of-Thought Prompting

Ask the AI to "think step by step."

**Example:**

```
Analyze the uploaded product images and sales data.

Think step by step:
1. First, identify the dominant visual patterns in high-selling products
2. Then, correlate those patterns with sales performance
3. Finally, form a hypothesis about which visual elements drive sales

Explain your reasoning at each step.
```

**Why it works:** Forces structured analysis, not just pattern matching.

---

### 2. Structured JSON Output

Get machine-readable output for dashboards or databases.

**Example:**

```
Analyze this product image and return results in valid JSON format:

{
  "dominant_colors": ["color1", "color2", "color3"],
  "silhouette": "fitted | oversized | structured",
  "target_demographic": "description",
  "estimated_price_tier": "budget | mid | premium | luxury",
  "confidence_score": 0.0-1.0
}
```

**Why it works:** Enables automation and integration.

---

### 3. Multi-Turn Refinement

Don't accept the first answer—iterate!

**Turn 1:**
```
Write a product description for a minimalist leather tote bag.
```

**Turn 2:**
```
Make it more emotional and aspirational.
```

**Turn 3:**
```
Now shorten it to under 50 words and add a call-to-action.
```

**Why it works:** Incremental improvement, like working with a human writer.

---

## Cross-Industry Applications

**These techniques aren't just for textiles:**

| Use Case | Other Industries |
|----------|------------------|
| Product image analysis | CPG, automotive, electronics, real estate |
| Sentiment analysis | SaaS, hospitality, finance, healthcare |
| Trend forecasting | Media, stock trading, consumer goods |
| Document RAG | Legal, consulting, government, research |
| Competitor analysis | Every industry |

**Key Insight:** You're learning a universal capability, not a niche tool.

---

## Tips for Success

### Do's
- Be specific about what you want
- Give context and role
- Use examples (few-shot)
- Iterate and refine
- Experiment with temperature
- Constrain the output format

### Don'ts
- Don't ask vague questions
- Don't assume it knows your brand voice
- Don't trust the first answer blindly
- Don't upload sensitive data without checking company policy
- Don't skip validation—always review outputs

---

## Common Pitfalls

| Problem | Solution |
|---------|----------|
| Output too generic | Add role, context, and constraints |
| Wrong tone | Provide examples of your brand voice |
| Hallucinations (made-up facts) | Use RAG with uploaded documents |
| Inconsistent results | Lower temperature for consistency |
| Output too long | Specify word/character limits |

---

## What to Do After the Workshop

1. **Save your best prompts** — Build a personal prompt library
2. **Experiment with your own data** — Upload real internal documents (following your company's AI policy)
3. **Share with your team** — Teach colleagues what you learned
4. **Track time saved** — Measure which tasks AI accelerates
5. **Stay curious** — Try new use cases every week

---

## Resources You're Taking Home

- This workshop guide
- Prompt engineering cheat sheet
- Sample data files (CSV, PDF)
- Slide deck (PDF)
- Prompt library with 20+ ready-to-use templates

---

## Reflection Questions

Before you leave, think about:

- **What surprised you most?**
- **Which use case would save you the most time?**
- **What data would you need to make this work at your company?**
- **Where would AI governance matter most for your team?**

---

## Support & Next Steps

**Questions?** Ask during the workshop or reach out to [your contact info].

**Want to go deeper?**
- Explore Claude, GPT-4, and other models
- Learn about fine-tuning for custom use cases
- Investigate Red Hat AI for enterprise deployment

---

**Thank you for participating! Now go build something amazing.**
