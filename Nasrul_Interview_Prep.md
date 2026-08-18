# Data Analyst Interview Prep — Nasrul Khair

Built from your resume and background. Use this to rehearse out loud before interviews.
Add your own notes under each answer as you practice.

---

## HOW TO USE THIS
- Rehearse answers **out loud**, not just in your head — you'll catch where you freeze.
- For every technical claim, be ready to explain *how* you did it, not just that you did.
- Keep the "why I left PPNJ" answer clean and neutral. Never mention the new boss, politics, GCP cost, or Excel rollback.
- Lead with ownership and judgment — that's your edge over analysts from big-stack companies.

---

## SECTION 1 — ABOUT YOU / OPENING

**Q: Tell me about yourself.**
Keep it to ~60 seconds. Structure: who you are → what you did most recently → what you're looking for.
> "I'm a data analyst with hands-on experience across the full data lifecycle — ETL, data modelling, dashboards, and reporting. Most recently at PPNJ Tours & Travel, I was responsible for the company's data function end-to-end. I built a cloud-based medallion architecture on GCP, developed Python ETL workflows, and delivered Power BI and Excel dashboards that cut manual reporting by 25–30 hours a week. I'm now looking for a role where I can keep growing as an analyst on a stronger data team."

**Q: Walk me through your resume / career path.**
Acknowledge the pivot honestly — you came from aeronautical engineering and moved deliberately into data.
> "My background started in engineering, but over the last few years I made a deliberate transition into data analytics — through structured training, certifications, freelance projects, and then full-time analyst roles. The engineering foundation actually helps: strong analytical thinking, structured problem-solving, and comfort with numbers."

**Q: Why data analytics after an engineering degree?**
> "Engineering trained me to solve problems with data and structure. I realized the part I enjoyed most was working with data itself — finding patterns and turning them into decisions — so I moved into analytics intentionally, backing it with training and certifications."

---

## SECTION 2 — THE "WHY DID YOU LEAVE" QUESTION (HANDLE WITH CARE)

**Q: Why did you leave PPNJ? / Why are you looking?**
This is the one to keep clean. Your rehearsed answer:
> "There was a restructuring and a change in leadership, which shifted the company's direction and priorities away from the data modernization work I'd been driving. Rather than move backward, I decided it was the right time to look for a role where I could keep growing in data analytics."

If they probe further:
> "The data infrastructure I'd built wasn't going to be maintained under the new direction, so staying wouldn't have let me keep developing. I'd rather be somewhere investing in its data capability."

**DO NOT SAY:** anything about the new GM's ego, political connections, refusing to pay for GCP, calling your work "too advanced," or rolling back to Excel. All true, all harmful in an interview. Stay neutral.

**Q: You're currently unemployed — what have you been doing?**
> "I've been taking on freelance data projects while searching for the right full-time analyst role, so I've stayed hands-on with cleaning, transformation, and dashboarding."

---

## SECTION 3 — TECHNICAL: SQL

**Q: How comfortable are you with SQL? What have you used it for?**
> "I use SQL regularly — at PPNJ I wrote queries in GCP to fulfill ad-hoc, cross-departmental data requests. I'm comfortable with joins, CTEs, window functions, stored procedures, and query optimization."

**Q (likely follow-up): Explain the difference between WHERE and HAVING.**
- WHERE filters rows *before* grouping; HAVING filters *after* aggregation (on grouped results).

**Q: What's a window function? Give an example.**
- A function that performs a calculation across a set of rows related to the current row, without collapsing them (unlike GROUP BY). Example: `ROW_NUMBER()`, `RANK()`, running totals with `SUM() OVER (PARTITION BY ...)`.

**Q: What's a CTE and why use it?**
- A Common Table Expression — a named temporary result set (`WITH ... AS`) that makes complex queries readable and lets you reference the same subquery multiple times, including recursively.

**Q: How do you optimize a slow query?**
- Check indexes, avoid SELECT *, filter early, look at the execution plan, reduce unnecessary joins/subqueries, avoid functions on indexed columns in WHERE.

> **Prep tip:** Have ONE concrete SQL story ready — a specific request someone made at PPNJ and how you queried it. Interviewers love a real example over textbook definitions.

---

## SECTION 4 — TECHNICAL: PYTHON / ETL

**Q: Walk me through an ETL pipeline you built.**
This is your strongest technical story. Tell it as the medallion flow:
> "At PPNJ I designed a medallion architecture on Google Cloud Storage — bronze, silver, gold layers. I extracted raw data from shared Google Drive, transformed it in Python using Pandas, and loaded it through the layers. The gold layer fed Power BI dashboards, while the intermediate silver layer supported faster ad-hoc updates. For lighter needs I'd use Python or Excel depending on the request."

**Q (follow-up): Why a medallion architecture? What do the layers do?**
- **Bronze** = raw, untouched ingested data (source of truth).
- **Silver** = cleaned, validated, deduplicated, joined.
- **Gold** = business-ready, aggregated, structured for reporting/dashboards.
- Benefit: separation of concerns, reprocessing without re-ingesting, traceability.

**Q: What Python libraries do you use for data work?**
- Pandas (wrangling), NumPy (numerical), Matplotlib/Seaborn (viz), SQLAlchemy (DB connection). Be honest about depth — you use Pandas most.

**Q: How do you handle messy / inconsistent data?**
Use your real PPNJ experience:
> "That was most of my job at PPNJ — years of unstructured historical data in manual Excel. I standardized formats, handled duplicates using composite keys, validated at the source with VBA-based input forms so bad data didn't enter in the first place, then consolidated into star/snowflake schemas."

---

## SECTION 5 — TECHNICAL: POWER BI / DASHBOARDS / DATA MODELLING

**Q: Describe a dashboard you built and its impact.**
> "I built Power BI dashboards for sales, customer segmentation, campaigns, and operational KPIs, giving management real-time revenue and cost visibility. It replaced manual reporting and saved roughly 25–30 hours a week. I built some dashboards in Excel too, when a department preferred it — I chose the tool based on who was using it."

**Q: What is DAX? Give an example of a measure you've written.**
- DAX = Data Analysis Expressions, the formula language in Power BI. Example measures: `Total Revenue = SUM(Sales[Amount])`, or a YoY calc using `CALCULATE` with `SAMEPERIODLASTYEAR`. Have one real measure ready.

**Q: Star schema vs snowflake schema — explain.**
- **Star:** central fact table connected directly to denormalized dimension tables. Simpler, faster queries.
- **Snowflake:** dimensions are normalized into sub-dimensions. Less redundancy, more joins, slightly slower.
- You've built both — say which you used and why.

**Q: Fact vs dimension table?**
- Fact = measurable events/metrics (sales, transactions), usually numeric + foreign keys.
- Dimension = descriptive context (customer, product, date).

---

## SECTION 6 — BEHAVIORAL / SITUATIONAL

**Q: Tell me about a difficult data problem you solved.**
Use the Lark Base deduplication story (Bridge Content):
> "At Bridge Content, there was a data-integrity issue — duplicate records that couldn't be filtered out. I engineered a trigger-based deduplication workflow using composite keys (Order ID + date), which replaced a manual cleanup process and kept records clean and filterable in real time."

**Q: Tell me about a time you worked with non-technical stakeholders.**
This is your signature strength — lean in:
> "At PPNJ almost the entire team relied on Excel and wasn't technical. A big part of my job was meeting them where they were — I built Excel-based input forms with VBA so they could contribute data cleanly, and I delivered some dashboards in Excel instead of Power BI when that's what they were comfortable with. I focused on adoption, not just building the fanciest solution."

**Q: Tell me about a time you had autonomy / owned something.**
> "At PPNJ I was given full flexibility to design the company's entire data approach — there was no existing infrastructure. I decided the tools, the architecture, the storage strategy, and how to get people to use it. It taught me to own outcomes end-to-end."

**Q: A time you made a mistake / something failed.**
Have one honest, small example ready with what you learned. Don't say "I have no weaknesses." Pick something real and minor, and emphasize the fix.

**Q: How do you prioritize when multiple people request data at once?**
> "I clarify urgency and business impact, batch similar requests, and for recurring ones I'd automate or build a self-serve dashboard so people don't have to keep asking."

---

## SECTION 7 — THE GAP QUESTIONS (BE HONEST, SHOW JUDGMENT)

**Q: Have you worked with big data / enterprise tools like Airflow, dbt, BigQuery, Spark?**
Be honest — don't fake it:
> "I haven't used those in production. I worked in a smaller, low-infrastructure environment, so I solved the same problems — orchestration, transformation, layering — with the tools I had: Python, GCS, a medallion structure. I understand the concepts and I'm confident I'd pick those tools up quickly."

**Q: Your experience is at smaller companies — how would you handle enterprise scale?**
> "The scale was smaller, but the problems were the same: messy data, multiple sources, stakeholder needs, building for adoption. What I bring is ownership and judgment — I designed systems from scratch rather than just plugging into existing ones. I'm eager to apply that in a larger, more structured environment."

---

## SECTION 8 — QUESTIONS TO ASK THEM (ALWAYS HAVE 3–4)
Asking good questions signals seriousness. Pick a few:
- "What does the current data stack and reporting setup look like?"
- "What would success in this role look like in the first 6 months?"
- "How does the data team work with other departments here?"
- "What are the biggest data challenges the team is facing right now?"
- "Is there room to grow technically — new tools, bigger projects?"

---

## SECTION 9 — YOUR CORE TALKING POINTS (MEMORIZE THESE)
No matter what they ask, keep steering back to these strengths:
1. **End-to-end ownership** — designed a whole data function from nothing.
2. **Medallion architecture on GCP** — real, modern data engineering, self-taught.
3. **SQL + Python + Power BI** — full analyst toolkit, used in production.
4. **Adoption-focused** — VBA forms, dual-tool dashboards, built for non-technical users.
5. **Measurable impact** — 25–30 hrs/week saved, ~90% manual entry reduction (Bridge).
6. **Certified** — Data Analyst, Data Scientist, Data Engineer certs.

---

## FINAL REMINDERS
- Confidence comes from preparation. You've done real work — rehearse it until it flows.
- Every wobble you had in prep has a real, defensible answer. Trust that.
- Neutral on PPNJ exit. Positive on what you learned. Forward-looking on what you want.
- You built something most mid-level analysts have only read about. Walk in owning that.

Good luck.
