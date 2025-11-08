# File Interconnections Map - Chocolat on James Project

**Purpose**: This document maps dependencies between files to ensure consistency when updates are made. When you change a key metric or assumption in one file, this guide shows which other files must be updated.

**Last Updated**: October 2025

---

## Core Financial Assumptions (MASTER REFERENCE)

These numbers appear in multiple files and must stay consistent:

### Current State
- **Current Revenue**: $537,000 annually
- **Historical Peak**: $751,000 (2021)
- **Revenue Decline**: -28.5% (2021-2025)
- **Peak Month**: December $89K (16.6% of annual)
- **Low Month**: January $17K (3.2% of annual)
- **Seasonality**: 5.2x variance
- **Current Marketing Spend**: $0
- **Owner Hours**: 84+/week

### Year 1 Targets (Bootstrap Package)
- **Target Revenue**: $650-675K (+21-26%)
- **Walk-in Revenue**: $505K
- **E-commerce Revenue**: $90-100K
- **Corporate Revenue**: $40-50K
- **Other Revenue**: $15-20K
- **Total Investment**: $28,000
- **Net Profit Margin**: 17-18%
- **Payback Period**: 4-5 months
- **ROI**: 2.9-3.6x

---

## Critical Numbers by Investment Package

### Bootstrap Package (RECOMMENDED)
- **Investment**: $28,000
- **Year 1 Revenue**: $650-675K
- **Approach**: Dan DIY + AI tools + consulting
- **Consultant Fee**: $11,500
- **AI Tools Cost**: $776/year
- **Marketing Spend**: $6,500
- **Dan's Time**: 30 hours/week

### Hybrid Package
- **Investment**: $52,000
- **Year 1 Revenue**: $675-700K
- **Adds**: Professional photography ($2,500) + Part-time marketing coordinator ($12,000)

### Full-Service Package
- **Investment**: $125,000
- **Year 1 Revenue**: $700-750K
- **Approach**: Agency-managed

---

## File Dependency Matrix

### When You Update Investment Numbers

**If Bootstrap Package investment changes from $28K:**

Update these files:
1. `/proposal/pricing-options-revised.md` - Line 23 (main budget)
2. `/proposal/executive-summary.md` - Lines 143-155 (investment breakdown)
3. `/README.md` - Lines 63 (bootstrap investment amount)
4. `/proposal/phase-1-scope.md` - Budget summary section
5. `/proposal/phase-2-scope.md` - Budget summary section
6. `/proposal/recommendations.md` - Investment discussion
7. `/AI-IMPLEMENTATION-GUIDE.md` - Line 3 (savings calculation)

### When You Update Revenue Targets

**If Year 1 revenue target changes from $650-675K:**

Update these files:
1. `/financial-analysis/growth-projections.md` - All projection tables
2. `/financial-analysis/revenue-analysis.md` - Year 1 projection section
3. `/proposal/executive-summary.md` - Line 20 (Year 1 objective)
4. `/README.md` - Line 59 (Year 1 objective)
5. `/proposal/opportunities.md` - Combined opportunity analysis
6. `/proposal/recommendations.md` - Expected outcomes sections
7. `/proposal/phase-1-scope.md` - Success metrics
8. `/proposal/phase-2-scope.md` - Success metrics
9. `/proposal/pricing-options-revised.md` - Expected outcomes for each package

### When You Update E-commerce Targets

**If e-commerce revenue target changes from $90-100K Year 1:**

Update these files:
1. `/strategy/ecommerce-strategy.md` - Year 1 target (appears 5+ times)
2. `/financial-analysis/growth-projections.md` - Channel breakdown tables
3. `/proposal/executive-summary.md` - Implementation approach section
4. `/proposal/opportunities.md` - E-commerce opportunity (#1)
5. `/proposal/recommendations.md` - Recommendation 1.1
6. `/proposal/phase-1-scope.md` - Phase 1 deliverables
7. `/proposal/phase-2-scope.md` - E-commerce scaling section

### When You Update Corporate Gifting Targets

**If corporate revenue target changes from $40-50K Year 1:**

Update these files:
1. `/strategy/corporate-gifting-strategy.md` - Year 1 target (appears 8+ times)
2. `/financial-analysis/growth-projections.md` - Channel breakdown tables
3. `/proposal/opportunities.md` - Corporate gifting opportunity (#3)
4. `/proposal/recommendations.md` - Recommendation 2.1
5. `/proposal/phase-2-scope.md` - Corporate program section
6. `/proposal/pricing-options-revised.md` - Expected outcomes

### When You Update Marketing Budget

**If marketing budget changes from $6,500 (Bootstrap):**

Update these files:
1. `/strategy/marketing-strategy.md` - Budget allocation table (Line 31+)
2. `/proposal/pricing-options-revised.md` - Bootstrap budget breakdown
3. `/proposal/phase-1-scope.md` - Month marketing spend
4. `/proposal/phase-2-scope.md` - Marketing scale-up budget
5. `/financial-analysis/profitability-assessment.md` - Marketing ROI section
6. `/proposal/recommendations.md` - Marketing investment discussion

### When You Update Consultant Fees

**If your consulting fee changes from $11,500:**

Update these files:
1. `/proposal/pricing-options-revised.md` - Lines 154, 206, 533
2. `/proposal/executive-summary.md` - Line 153 (consultant fee)
3. `/proposal/phase-1-scope.md` - Strategic consulting budget
4. `/proposal/phase-2-scope.md` - Consulting budget
5. `/AI-IMPLEMENTATION-GUIDE.md` - Your Role section

---

## Content Consistency Rules

### Brand Information

**Business Name**: "Chocolat on James" (with "Chocolat" - French spelling)
**Location**: James Street North, Hamilton, Ontario
**Owner**: Dan Edwards
**Acquisition Date**: September 30, 2025
**Products**: Handmade chocolates, truffles, ice cream, coffee

### Key Messaging (Keep Consistent)

**Value Proposition**: 
"Hamilton's Premier Artisan Chocolatier - Handcrafted with Care"

**Positioning**: 
"Toronto quality at Hamilton accessibility"

**Differentiation**:
1. Local Hamilton business (support local)
2. Handmade, artisan quality
3. Multi-product destination (chocolate + ice cream + coffee)
4. James Street North location (arts district)
5. Same-day delivery capability

### Strategic Priorities (Consistent Order)

1. Launch e-commerce platform
2. Implement marketing strategy
3. Create customer database and email marketing
4. Develop corporate gifting program
5. Reduce revenue seasonality
6. Establish operational systems
7. Reduce owner's working hours

---

## Metric Consistency Guide

### Financial Metrics Format

**Revenue**: Always show in thousands with K (e.g., $537K not $537,000 in summaries)

**Percentages**: 
- Growth rates: Show with + sign (e.g., +26%)
- Margins: No sign (e.g., 17% net margin)

**Ranges**: Use dash (e.g., $650-675K)

### Time Periods

**Months**: Use Month 1-12 (not January-December for projections)
**Phases**: Phase 1 (Months 1-4), Phase 2 (Months 5-12)
**Years**: Year 1, Year 2, Year 3

### Investment Packages

Always refer to as:
- **Bootstrap Package** (not "DIY" or "Self-Service")
- **Hybrid Package** (not "Mixed" or "Combined")
- **Full-Service Package** (not "Agency" or "Premium")

---

## Cross-References Map

### Research Files Reference:

**competitive-analysis.md** referenced by:
- executive-summary.md (competitive position)
- market-research.md (competitive landscape)
- ecommerce-strategy.md (competitor benchmarks)

**market-research.md** referenced by:
- executive-summary.md (market opportunity)
- opportunities.md (opportunity sizing)
- recommendations.md (market validation)

**website-audit.md** referenced by:
- ecommerce-strategy.md (platform recommendations)
- phase-1-scope.md (e-commerce implementation)

**industry-benchmarks.md** referenced by:
- financial-analysis/*.md (all financial files use benchmarks)
- profitability-assessment.md (margin comparisons)

### Financial Files Reference:

**revenue-analysis.md** referenced by:
- growth-projections.md (baseline and scenarios)
- executive-summary.md (current state)
- opportunities.md (revenue potential)

**profitability-assessment.md** referenced by:
- growth-projections.md (profitability projections)
- recommendations.md (investment decisions)
- pricing-options-revised.md (ROI calculations)

**growth-projections.md** referenced by:
- executive-summary.md (3-year vision)
- recommendations.md (growth path)
- phase-2-scope.md (Year 2-3 preview)

### Strategy Files Reference:

**ecommerce-strategy.md** referenced by:
- opportunities.md (opportunity #1)
- recommendations.md (priority #1)
- phase-1-scope.md (e-commerce implementation)

**marketing-strategy.md** referenced by:
- all proposal files (marketing budget and tactics)
- phase-1-scope.md and phase-2-scope.md (marketing execution)

**corporate-gifting-strategy.md** referenced by:
- opportunities.md (opportunity #3)
- recommendations.md (recommendation 2.1)
- phase-2-scope.md (Months 5-6)

**partnership-opportunities.md** referenced by:
- opportunities.md (tier 2 opportunities)
- phase-2-scope.md (partnership development)

### Proposal Files Reference:

**executive-summary.md** - Master summary, references ALL files + CONSULTANT-PROFILE.md

**current-state.md** - References all research files

**opportunities.md** - References research + strategy files

**recommendations.md** - References all other proposal files

**phase-1-scope.md** - References: ecommerce-strategy, marketing-strategy

**phase-2-scope.md** - References: corporate-gifting-strategy, partnership-opportunities

**pricing-options-revised.md** - References: all financial files, AI-implementation-guide, CONSULTANT-PROFILE.md

### Supporting Documents Reference:

**CONSULTANT-PROFILE.md** - Referenced by:
- README.md (consultant introduction)
- executive-summary.md (strategic consultant section)
- pricing-options-revised.md (consultant value proposition)
- QUICK-START-GUIDE.md (why Greg section)

**AI-IMPLEMENTATION-GUIDE.md** - Referenced by:
- pricing-options-revised.md (cost savings justification)
- All proposal files (AI approach explanation)

**QUICK-START-GUIDE.md** - Executive briefing, references most files

**FILE-INTERCONNECTIONS-MAP.md** - This document, references all files

**GREG-CREDENTIALS-ONE-PAGER.md** - One-page consultant bio, referenced by:
- QUICK-START-GUIDE.md (consultant section)
- PROJECT-NAVIGATION-GUIDE.md (presentation materials)
- FINAL-PROJECT-SUMMARY.md (credentials showcase)

**PROJECT-NAVIGATION-GUIDE.md** - How to use the project, references:
- All proposal files
- All key documents
- Presentation strategy

**PROJECT-COMPLETION-SUMMARY.md** - Project overview for consultant use

**FINAL-PROJECT-SUMMARY.md** - Complete project summary with credentials integrated

---

## Update Workflow

### When Making a Change

**Step 1: Identify Impact**
- Check this map to see which files are affected
- Note all files that reference the changing data

**Step 2: Update Master First**
- Update the source/master file with new information
- Document the change and reasoning

**Step 3: Update Dependent Files**
- Go through each dependent file systematically
- Use search/replace for exact numbers
- Verify context still makes sense with new numbers

**Step 4: Cross-Check Consistency**
- Read through updated sections
- Ensure narrative consistency (not just numbers)
- Check calculations (percentages, totals, etc.)

**Step 5: Update This Map**
- If you add new key metrics, add them to this map
- Note new dependencies created

---

## Quick Reference: Where Key Info Lives

| Information | Master Source | Also Appears In |
|-------------|---------------|-----------------|
| Current revenue ($537K) | revenue-analysis.md | 8 other files |
| Year 1 target ($650-675K) | growth-projections.md | 9 other files |
| Bootstrap investment ($28K) | pricing-options-revised.md | 7 other files |
| E-commerce target ($90-100K) | ecommerce-strategy.md | 7 other files |
| Corporate target ($40-50K) | corporate-gifting-strategy.md | 6 other files |
| Marketing budget ($6,500) | pricing-options-revised.md | 5 other files |
| Consultant fee ($11,500) | pricing-options-revised.md | 5 other files |
| AI tool costs ($776/year) | AI-IMPLEMENTATION-GUIDE.md | 3 other files |
| Dan's time (30 hrs/week) | pricing-options-revised.md | 5 other files |
| Payback period (4-5 months) | pricing-options-revised.md | 3 other files |

---

## Version Control

When making significant updates:

**Document Version Changes**:
```
## Version History

v1.0 - October 2025 - Initial analysis (agency-focused, $125K investment)
v2.0 - October 2025 - Revised to bootstrap approach ($28K investment, AI-powered)
```

**Tag Updated Files**:
At bottom of each updated file:
```
**Last Updated**: October 2025  
**Version**: 2.0 (Bootstrap revision)
**Status**: Current  
**Next Review**: After Phase 1 completion (Month 4)
```

---

## Validation Checklist

Before finalizing any major update, verify:

**Financial Consistency**:
- [ ] All revenue projections add up correctly
- [ ] Investment totals match across files
- [ ] ROI calculations consistent
- [ ] Percentages calculate correctly from absolute numbers

**Strategic Consistency**:
- [ ] Priorities ordered the same way across files
- [ ] Timelines align (Phase 1 vs. Phase 2)
- [ ] Success metrics achievable given investment
- [ ] Recommendations support stated goals

**Narrative Consistency**:
- [ ] Tone consistent (bootstrap-friendly, not agency-sales)
- [ ] Dan's situation described consistently
- [ ] Value propositions align
- [ ] No contradictions in approach

**Technical Consistency**:
- [ ] File cross-references work
- [ ] Internal links valid
- [ ] File names match references
- [ ] Structure logical and navigable

---

## Common Update Scenarios

### Scenario 1: Dan Chooses Hybrid Instead of Bootstrap

**Files to Update**:
1. README.md - Change recommended package
2. executive-summary.md - Update investment and outcomes
3. All phase scopes - Adjust budgets and staffing
4. pricing-options-revised.md - Mark Hybrid as recommended

**Key Changes**:
- Investment: $28K → $52K
- Revenue: $650-675K → $675-700K
- ROI: 2.9-3.6x → 2.5-3.2x
- Dan's time: 30 hrs/week → 20-25 hrs/week

### Scenario 2: Phase 1 Results Better Than Expected

**Files to Update**:
1. phase-2-scope.md - Increase Phase 2 targets
2. growth-projections.md - Adjust Year 1 projection upward
3. recommendations.md - Note success, adjust Phase 2 priorities

**What to Track**:
- Actual vs. projected at Month 4
- Which channels over/underperformed
- Lessons learned for Phase 2
- Budget reallocation opportunities

### Scenario 3: New AI Tool Reduces Costs Further

**Files to Update**:
1. AI-IMPLEMENTATION-GUIDE.md - Add new tool
2. pricing-options-revised.md - Reduce costs
3. phase-1-scope.md - Update tool budget

**Recalculate**:
- Total tool costs
- Savings vs. traditional
- ROI impact
- Implementation timeline

---

## File Health Check (Monthly)

**Review Quarterly**:
- [ ] Are cross-references still valid?
- [ ] Have any assumptions changed?
- [ ] Do projections need updating based on actuals?
- [ ] Are new opportunities identified?
- [ ] Should new files be added?

**Update Annually**:
- Complete refresh based on Year 1 results
- Reset projections for Year 2
- Revise strategies based on learnings
- Archive outdated versions

---

## Key Contacts & Roles

**Project Owner**: Dan Edwards (Chocolat on James)  

**Strategic Consultant**: **Greg** | 905-334-9282
- 28 years engineering (SMS-Siemag Chief Engineer + Consulting Engineering)
- 10+ years multi-channel e-commerce (Amazon, Shopify, Direct to multi-million $)
- $2M+ digital advertising expertise
- AI & automation pioneer ($75K-125K savings proven)

**Document Maintainer**: Greg / Assigned team member

**For Questions About**:
- Financial projections → Contact Greg (engineering precision)
- AI implementation → Contact Greg (AI expert)
- E-commerce strategy → Contact Greg (10+ years experience)
- Day-to-day execution → Dan (with Greg's guidance)
- Strategic pivots → Joint decision (Dan + Greg monthly sessions)

---

## Conclusion

This interconnections map ensures:
1. ✅ Consistency across all 20 project files
2. ✅ Easy updates when assumptions change
3. ✅ Clear dependencies documented
4. ✅ Version control maintained
5. ✅ Quality assurance systematic

**Use this map every time you update project files!**

---

**Document Owner**: Project Consultant  
**Last Updated**: October 2025  
**Next Review**: After Phase 1 completion or when assumptions change  
**Status**: Master reference document - keep current!

