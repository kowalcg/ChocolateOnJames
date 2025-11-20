# Quick Reference: Agent Prompt for Implementing Image Workflow

**Use this prompt with Claude Code or any AI coding assistant to replicate the two-stage image workflow in another project.**

---

## Copy & Paste This Entire Prompt:

```
I need you to implement a two-stage image analysis and prompt generation system in my content generator.

SOURCE SYSTEM REFERENCE:
Location: /Users/MacBook1/Library/CloudStorage/GoogleDrive-info@geartopdesign.com/Shared drives/Greg/1. Consulting/2. Chocolate on James/3. Project Phase 1 - Research and Analysis/Week 3-4/Templates & Tools/1. CHoJ Contern Creator/

Reference files:
1. chocolate-content-creator-pro-v5.2.html (working implementation)
2. COMPLETE-LOGIC-DOCUMENTATION-V5.2.md (technical documentation)
3. TAPEGEEKS-IMPLEMENTATION-GUIDE.md (step-by-step guide)

TARGET SYSTEM:
[SPECIFY YOUR FILE PATH HERE]

REQUIREMENTS:

1. IMAGE UPLOAD SYSTEM
   - Add drag-and-drop zone for images
   - Support paste (Ctrl+V/Cmd+V) from clipboard
   - File browser upload button
   - Accept: JPG, PNG, WebP

2. IMAGE ANALYSIS ENGINE
   - Extract 5 dominant colors from actual image pixels
   - Calculate average brightness (0-255 scale)
   - Determine color temperature (warm/cool/neutral)
   - Generate descriptive text based on analysis

3. TWO-STAGE WORKFLOW

   Stage 1: Quick Variations
   - Generate 4 instant prompt variations:
     a) Exact Match - recreate reference style precisely
     b) Inspired - similar aesthetic, creative variation
     c) Premium - elevated ultra-high-end version
     d) Branded - adapted for [MY BRAND] identity
   - Each variation references ACTUAL analyzed data
   - Display in cards with copy and "Use" buttons

   Stage 2: Comprehensive Generation
   - When image is uploaded, main generator uses it as BASE
   - Combine: Analyzed image data + User-selected options
   - Options include: platform, audience, season, style, etc.
   - Generate full comprehensive prompt

4. STATE MANAGEMENT
   - Global variables:
     * currentImageData (base64 string)
     * currentAnalysis (object with style, colors, lighting, etc.)
     * generatedVariations (array of 4 prompts)
   - Persist until user explicitly clears

5. UI INDICATORS
   - Green banner when image loaded showing thumbnail
   - Button text changes: "Generate Using Uploaded Image"
   - Clear Image button
   - Visual feedback throughout

6. KEY FUNCTIONS TO IMPLEMENT

   Required functions:
   - handleImageUpload(file)
   - analyzeImageWithAI(imageData)
   - extractDominantColors(ctx, width, height)
   - analyzeBrightness(ctx, width, height)
   - analyzeColorTemperature(colors)
   - generatePromptVariations(analysis)
   - buildImagePromptWithUploadedImage(options, analysis)
   - showImageModeBanner(imageData)
   - clearUploadedImage()

7. CUSTOMIZATION FOR [MY PRODUCT/BRAND]

   Replace these elements from chocolate context:

   Product Type: [YOUR PRODUCTS]
   Brand Voice: [YOUR TONE - professional/casual/luxury/etc.]
   Color Palette: [YOUR BRAND COLORS]
   Target Audiences: [YOUR CUSTOMER SEGMENTS]
   Seasonal Content: [YOUR RELEVANT SEASONS/PROMOTIONS]
   Product Categories: [YOUR PRODUCT TYPES]

8. CRITICAL SUCCESS FACTORS

   ✓ Each uploaded image produces UNIQUE prompts
   ✓ Analysis must be based on ACTUAL image data, not templates
   ✓ Both workflows work: quick (Stage 1) and comprehensive (Stage 2)
   ✓ System works perfectly WITHOUT images (backward compatible)
   ✓ Visual clarity - user always knows if image is active

IMPLEMENTATION APPROACH:

Please implement in phases:

Phase 1: Image upload infrastructure (HTML + CSS + basic JS)
Phase 2: Image analysis functions (pixel sampling, color extraction)
Phase 3: Quick variations (Stage 1)
Phase 4: Integration with main generator (Stage 2)
Phase 5: UI state management and visual indicators

After each phase, pause for testing before proceeding.

DELIVERABLES:

1. Updated [MY FILE] with complete two-stage system
2. Backup of original file (dated)
3. List of changes made
4. Quick testing checklist

Please start with Phase 1 and show me what you're adding before proceeding to the next phase.
```

---

## Customization Template

**Before running the prompt, fill in these placeholders:**

| Placeholder | Example (TapeGeeks) | Your Value |
|-------------|---------------------|------------|
| `[MY FILE PATH]` | `/path/to/tapegeeks-generator.html` | ____________ |
| `[MY BRAND]` | TapeGeeks | ____________ |
| `[YOUR PRODUCTS]` | Industrial tape products | ____________ |
| `[YOUR TONE]` | Professional, reliable, industrial-grade | ____________ |
| `[YOUR BRAND COLORS]` | Blues, grays, industrial colors | ____________ |
| `[YOUR CUSTOMER SEGMENTS]` | Contractors, DIY, Businesses, Warehouse | ____________ |
| `[YOUR RELEVANT SEASONS]` | Back-to-school, Moving season, Holiday shipping | ____________ |
| `[YOUR PRODUCT TYPES]` | Packaging, Duct, Masking, Specialty tape | ____________ |

---

## Expected Timeline

| Phase | Duration | Deliverable |
|-------|----------|-------------|
| Phase 1 | 1 hour | Upload UI working |
| Phase 2 | 1.5 hours | Analysis functions complete |
| Phase 3 | 1 hour | 4 quick variations generating |
| Phase 4 | 1.5 hours | Stage 2 integrated |
| Phase 5 | 30 min | All UI polish complete |
| **TOTAL** | **5.5 hours** | **Fully functional system** |

---

## Testing After Implementation

Run these tests to verify success:

```
✓ Upload bright image → Analysis shows "bright, high-key"
✓ Upload dark image → Analysis shows "dark, low-key"
✓ Upload warm-toned image → Analysis shows "warm temperature"
✓ Extract colors → Shows actual colors from image (not generic)
✓ Generate variations → All 4 reference actual image data
✓ Stage 1 workflow → Quick prompts work independently
✓ Stage 2 workflow → Image + options = comprehensive prompt
✓ Clear image → Resets to normal mode
✓ Without image → Works exactly as before (regression test)
```

---

## Troubleshooting

**If prompts are still generic:**
- Check that `currentAnalysis` is not null when generating
- Verify `buildImagePromptWithUploadedImage()` is being called
- Ensure analysis object has real data, not mock data

**If images aren't uploading:**
- Check FileReader browser compatibility
- Verify file input accept attribute
- Test drag/drop event handlers

**If colors look wrong:**
- Increase sample size (reduce sampleSize value)
- Verify canvas is loading image correctly
- Check rgbToHex conversion

---

**This prompt contains everything needed to replicate the system in any project!**
