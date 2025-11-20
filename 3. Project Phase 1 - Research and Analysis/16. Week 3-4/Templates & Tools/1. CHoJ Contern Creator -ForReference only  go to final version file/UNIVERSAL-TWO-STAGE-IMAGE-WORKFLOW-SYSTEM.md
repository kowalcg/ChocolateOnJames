# Universal Two-Stage Image Workflow System
## Complete Implementation Guide for Any Business Type

**Version:** 1.0 - Universal
**Created:** November 15, 2025
**Applies To:** Physical Products, Events, Services, Local Businesses, E-commerce, B2B, B2C

---

## Table of Contents
1. [System Overview](#system-overview)
2. [How It Works (Universal)](#how-it-works-universal)
3. [Business Examples](#business-examples)
4. [Universal Data Flow](#universal-data-flow)
5. [Core Functions (Product-Agnostic)](#core-functions-product-agnostic)
6. [Implementation Steps](#implementation-steps)
7. [Customization Worksheet](#customization-worksheet)
8. [Testing Framework](#testing-framework)

---

## System Overview

### What This System Does (Universally)

This two-stage workflow allows ANY business to:

1. **Upload reference images** (competitor photos, inspiration, existing content, event photos, product shots)
2. **Get AI-powered analysis** (colors, lighting, brightness, mood, style)
3. **Generate 4 quick prompt variations** (Exact Match, Inspired, Premium, Your Brand)
4. **OR combine image with your business details** to create comprehensive marketing content

### Universal Benefits

✅ Works for **physical products** (kinesiology tape, nasal strips)
✅ Works for **events** (running races, Father's Day celebrations)
✅ Works for **services** (consulting, training, digital products)
✅ Works for **local businesses** (retail, restaurants, studios)
✅ Works for **B2B and B2C**

---

## How It Works (Universal)

### The Two-Stage Workflow

```
┌─────────────────────────────────────────┐
│  USER UPLOADS REFERENCE IMAGE           │
│  (Competitor, Inspiration, Own Content) │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│  AI ANALYZES ACTUAL IMAGE               │
│  - Extracts real colors from pixels     │
│  - Detects brightness (dark/bright)     │
│  - Identifies color temperature          │
│  - Generates unique description          │
└────────────────┬────────────────────────┘
                 │
        ┌────────┴────────┐
        ▼                 ▼
┌──────────────┐  ┌──────────────────────┐
│  STAGE 1     │  │  STAGE 2             │
│  Quick       │  │  Comprehensive       │
│  4 Prompts   │  │  Custom Generation   │
│  (30 sec)    │  │  (2 minutes)         │
└──────────────┘  └──────────────────────┘
```

### Stage 1: Quick Variations (30 seconds)
- Upload image → Get 4 instant AI prompt variations
- Copy and use immediately in your AI tool (Gemini, ChatGPT, etc.)

### Stage 2: Full Custom Generation (2 minutes)
- Use uploaded image + customize ALL options
- Platform, audience, season, style, tone, etc.
- Generate comprehensive prompt + social media captions

---

## Business Examples

### Example 1: Physical Products (TapeGeeks - Kinesiology Tape)

**Scenario:** Want to create Instagram post for new kinesiology tape color

**Stage 1 Workflow:**
1. Upload: Photo of blue kinesiology tape roll
2. Analysis detects: Blue (#1976D2), professional lighting, clean background
3. Get 4 variations:
   - Exact: Recreate this blue tape with same clean presentation
   - Inspired: Similar professional style, different angle
   - Premium: Ultra-professional medical-grade presentation
   - TapeGeeks Brand: Blue tape with TapeGeeks athletic branding

**Stage 2 Workflow:**
1. Keep uploaded blue tape image
2. Select options:
   - Platform: Instagram Post
   - Audience: Athletes & Sports Medicine Professionals
   - Season: Spring Training Season
   - Style: Action/Lifestyle
   - Include: Product in use, athletic performance
3. Generate: Comprehensive prompt showing blue kinesiology tape being applied by athlete during spring training, targeting sports medicine pros

**Result:** Marketing content perfectly matched to your actual product + strategic targeting

---

### Example 2: Events (Brontë Harbour Classic - Father's Day Race)

**Scenario:** Attract runners to register for June Father's Day race

**Stage 1 Workflow:**
1. Upload: Photo from last year's race (runners on waterfront course)
2. Analysis detects: Blues/greens (water/nature), bright outdoor lighting, energetic mood
3. Get 4 variations:
   - Exact: Recreate this waterfront race atmosphere precisely
   - Inspired: Similar scenic lakeside run, fresh perspective
   - Premium: Prestigious waterfront racing event presentation
   - Brontë Harbour Brand: Father's Day race with family celebration atmosphere

**Stage 2 Workflow:**
1. Keep uploaded race photo
2. Select options:
   - Platform: Facebook Ad
   - Audience: Fathers, Families, Local Runners
   - Season: Father's Day (June)
   - Style: Lifestyle/Community
   - Include: Waterfront setting, family celebration, local Hamilton pride
3. Generate: Comprehensive prompt showing scenic Brontë Harbour waterfront race with Father's Day celebration atmosphere, targeting families for registration

**Result:** Marketing content that captures your actual event + attracts target audience

---

### Example 3: Services (Hypothetical - Yoga Studio)

**Stage 1:** Upload peaceful yoga class photo → Get 4 prompt variations
**Stage 2:** Combine image + options (Platform: Instagram Story, Audience: Beginners, Season: New Year wellness) → Comprehensive content

### Example 4: Local Business (Hypothetical - Coffee Shop)

**Stage 1:** Upload latte art photo → Get 4 prompt variations
**Stage 2:** Combine image + options (Platform: Pinterest, Audience: Coffee lovers, Season: Fall PSL launch) → Comprehensive content

---

## Universal Data Flow

### State Variables (Same for ALL Businesses)

```javascript
// These variables work for ANY business type
let currentImageData = null;      // The uploaded image (base64)
let currentAnalysis = null;       // Analysis results (colors, brightness, mood)
let generatedVariations = [];     // 4 quick prompt variations
let lastGeneratedOptions = null;  // User's selected options
```

### Analysis Object (Universal Structure)

```javascript
{
    // VISUAL ANALYSIS (works for any image type)
    style: "Professional outdoor photography with bright natural lighting",
    composition: "Analyzed from uploaded reference image",
    lighting: "Bright natural sunlight creating energetic atmosphere",

    // COLOR DATA (extracted from actual pixels)
    colorPalette: ["#1976D2", "#4CAF50", "#E3F2FD", "#2E7D32", "#81C784"],

    // MOOD & ATMOSPHERE (adaptive to image)
    mood: "Energetic, active, outdoors, healthy lifestyle",

    // TECHNICAL DETAILS
    technicalDetails: "Well-lit outdoor setting, action-oriented composition",

    // METRICS (measured data)
    imageMetrics: {
        avgBrightness: 185,        // 0-255 scale
        colorCount: 5,             // Number of dominant colors
        temperature: "cool"        // warm/cool/neutral
    }
}
```

---

## Core Functions (Product-Agnostic)

### 1. Image Analysis (Works for ANY Image)

```javascript
function analyzeImageWithAI(imageData) {
    // Load image into canvas
    const img = new Image();
    img.onload = function() {
        const canvas = document.createElement('canvas');
        canvas.width = img.width;
        canvas.height = img.height;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0);

        // UNIVERSAL ANALYSIS (works for products, events, anything)
        const colors = extractDominantColors(ctx, canvas.width, canvas.height);
        const brightness = analyzeBrightness(ctx, canvas.width, canvas.height);
        const temperature = analyzeColorTemperature(colors);

        // ADAPTIVE DESCRIPTIONS (changes based on what's detected)
        return {
            style: brightness > 180 ?
                'Bright, high-key photography with clean, professional presentation' :
                brightness > 120 ?
                'Balanced photography with natural, authentic lighting' :
                'Dramatic, moody photography with strong contrast and atmosphere',

            lighting: brightness > 180 ?
                'Bright, even lighting from multiple sources' :
                brightness > 120 ?
                'Soft, natural lighting creating balanced exposure' :
                'Directional dramatic lighting with deep shadows',

            mood: brightness > 150 && temperature === 'cool' ?
                'Clean, professional, energetic, modern' :
                brightness > 150 && temperature === 'warm' ?
                'Bright, inviting, friendly, approachable' :
                brightness < 120 && temperature === 'warm' ?
                'Intimate, cozy, premium, sophisticated' :
                'Dramatic, bold, impactful, attention-grabbing',

            colorPalette: colors,
            technicalDetails: `${brightness > 170 ? 'High-key' : brightness > 85 ? 'Balanced' : 'Low-key'} exposure, ${temperature} color temperature`,
            imageMetrics: {
                avgBrightness: brightness,
                colorCount: colors.length,
                temperature: temperature
            }
        };
    };
    img.src = imageData;
}
```

### 2. Quick Variations (Universal Template)

```javascript
function generatePromptVariations(analysis, businessContext) {
    const colors = analysis.colorPalette.join(', ');
    const brightness = analysis.imageMetrics.avgBrightness;

    generatedVariations = [
        // VARIATION 1: EXACT MATCH (Universal)
        `Professional ${businessContext.contentType} photography recreating this exact style:
         ${analysis.style}.
         Lighting: ${analysis.lighting}.
         Color palette: ${colors}.
         Mood: ${analysis.mood}.
         Maintain exact brightness level (${brightness}/255) for visual consistency.
         High-resolution commercial photography suitable for ${businessContext.platforms}.`,

        // VARIATION 2: INSPIRED (Universal)
        `${businessContext.contentType} photography inspired by reference:
         Similar ${analysis.mood} aesthetic with creative variation.
         Quality level: ${analysis.style}.
         Color inspiration: ${colors}.
         Maintain ${analysis.imageMetrics.temperature} tones but explore different perspectives.
         Professional quality for ${businessContext.industry} marketing.`,

        // VARIATION 3: PREMIUM (Universal)
        `Ultra-premium ${businessContext.contentType} photography:
         ${analysis.style} elevated to luxury commercial standard.
         Enhanced lighting, perfect color harmony (${colors}), museum-quality detail.
         ${brightness > 170 ? 'Pristine bright presentation for premium positioning' :
                              'Dramatic atmospheric lighting for high-end appeal'}.
         Award-winning quality for ${businessContext.industry} campaigns.`,

        // VARIATION 4: YOUR BRAND (Customizable)
        `${businessContext.brandName} brand photography:
         ${analysis.style} adapted for ${businessContext.brandName} identity.
         ${analysis.lighting} showcasing ${businessContext.productType}.
         ${analysis.imageMetrics.temperature} ${analysis.mood} atmosphere
         communicating ${businessContext.brandValues}.
         Professional photography for ${businessContext.marketingChannels}.`
    ];
}
```

### 3. Comprehensive Generation (Universal Framework)

```javascript
function buildImagePromptWithUploadedImage(options, analysis, businessConfig) {
    let prompt = '';

    // 1. START WITH ACTUAL IMAGE ANALYSIS (Universal)
    prompt += `SUBJECT FROM UPLOADED REFERENCE IMAGE:\n`;
    prompt += `Content Type: ${businessConfig.contentType}\n`;
    prompt += `Visual Style: ${analysis.style}\n`;
    prompt += `Color Palette: ${analysis.colorPalette.join(', ')}\n`;
    prompt += `Lighting: ${analysis.lighting}\n`;
    prompt += `Mood: ${analysis.mood}\n`;
    prompt += `Brightness: ${analysis.imageMetrics.avgBrightness > 170 ? 'Bright/High-key' :
                             analysis.imageMetrics.avgBrightness > 85 ? 'Balanced' : 'Dark/Moody'}\n\n`;

    // 2. ADD PLATFORM (Universal)
    prompt += `PLATFORM OPTIMIZATION:\n`;
    prompt += `- ${getPlatformSpecs(options.platform)}\n\n`;

    // 3. ADD TARGET AUDIENCE (Business-Specific)
    prompt += `TARGET AUDIENCE:\n`;
    prompt += `- ${options.audience}\n`;
    prompt += `- ${getAudienceMessaging(options.audience, businessConfig)}\n\n`;

    // 4. ADD SEASONAL/OCCASION (Business-Specific)
    if (options.season) {
        prompt += `SEASONAL/OCCASION CONTEXT:\n`;
        prompt += `- ${getSeasonalContext(options.season, businessConfig)}\n\n`;
    }

    // 5. ADD CATEGORY/USE CASE (Business-Specific)
    prompt += `CONTENT CATEGORY:\n`;
    prompt += `- ${getCategoryDetails(options.category, businessConfig)}\n\n`;

    // 6. ADD STYLE PREFERENCES (Universal)
    prompt += `PHOTOGRAPHY STYLE:\n`;
    prompt += `- ${getStyleDescription(options.style)}\n`;
    prompt += `- Blend with visual characteristics from uploaded image\n\n`;

    // 7. FINAL INSTRUCTION (Universal)
    prompt += `FINAL RESULT: Professional ${options.platform} photography preserving
    the visual aesthetic from uploaded image (colors: ${analysis.colorPalette.slice(0,3).join(', ')},
    ${brightness > 170 ? 'bright presentation' : 'balanced atmosphere'}),
    while incorporating ${options.season || 'timeless'} context for ${options.audience}.
    ${businessConfig.brandPromise}`;

    return { prompt: prompt, platform: options.platform };
}
```

---

## Implementation Steps

### Phase 1: Set Up Your Business Configuration

**Create a businessConfig object for your specific business:**

```javascript
// EXAMPLE 1: TapeGeeks (Kinesiology Tape Products)
const businessConfig = {
    brandName: "TapeGeeks",
    industry: "Sports Medicine & Athletic Performance",
    contentType: "Athletic product",
    productType: "kinesiology tape and performance products",
    brandValues: "athletic performance, injury prevention, professional quality",
    marketingChannels: "Instagram, Facebook, Amazon, B2B medical suppliers",
    platforms: "e-commerce and social media marketing",

    categories: {
        'kinesiology-tape': 'Kinesiology tape - emphasize flexibility, support, performance',
        'nasal-strips': 'Nasal strips - highlight breathing improvement, athletic performance',
        'compression': 'Compression gear - focus on recovery, circulation, endurance',
        'accessories': 'Athletic accessories - versatility, quality, professional-grade'
    },

    audiences: {
        'athletes': 'Professional and amateur athletes',
        'sports-medicine': 'Sports medicine professionals and physical therapists',
        'fitness': 'Fitness enthusiasts and gym-goers',
        'coaches': 'Coaches and athletic trainers'
    },

    seasons: {
        'spring-training': 'Spring training season (March-May)',
        'marathon-season': 'Marathon season (October-November)',
        'year-round': 'Year-round athletic performance'
    }
};

// EXAMPLE 2: Brontë Harbour Classic (Running Race Event)
const businessConfig = {
    brandName: "Brontë Harbour Classic",
    industry: "Community Running Events",
    contentType: "Running race event",
    productType: "Father's Day waterfront race experience",
    brandValues: "family celebration, scenic running, community health, Father's Day tradition",
    marketingChannels: "Facebook Ads, Instagram, local community boards, running clubs",
    platforms: "event registration and community engagement",

    categories: {
        'race-day': 'Race day experience - scenic waterfront course, community atmosphere',
        'training': 'Training for the race - preparation tips, course preview',
        'family-celebration': 'Father's Day celebration - family activity, post-race festivities',
        'registration': 'Registration promotion - early bird, group discounts, race details'
    },

    audiences: {
        'fathers': 'Fathers looking for Father's Day activity',
        'families': 'Families wanting healthy Father's Day celebration',
        'local-runners': 'Hamilton area runners and running clubs',
        'first-timers': 'First-time race participants',
        'serious-runners': 'Competitive runners seeking times/PRs'
    },

    seasons: {
        'fathers-day': 'Father's Day weekend (June)',
        'spring-registration': 'Spring registration period (March-May)',
        'training-season': 'Pre-race training season (April-June)'
    }
};
```

### Phase 2: Customize UI Labels

**Update your HTML to match your business:**

```html
<!-- UNIVERSAL TEMPLATE -->
<div class="section-title">
    📸 Upload Reference Image (Optional)
    <span class="tooltip" data-tooltip="Upload [YOUR PRODUCT/EVENT] photo for AI-powered content generation">ℹ️</span>
</div>

<!-- TapeGeeks Example -->
<div class="section-title">
    📸 Upload Product Image (Optional)
    <span class="tooltip" data-tooltip="Upload kinesiology tape photo for AI-powered marketing content">ℹ️</span>
</div>

<!-- Brontë Harbour Example -->
<div class="section-title">
    📸 Upload Race Photo (Optional)
    <span class="tooltip" data-tooltip="Upload race or runner photo for AI-powered event marketing">ℹ️</span>
</div>
```

### Phase 3: Implement Core Functions

**Copy these functions exactly (they work for ANY business):**

1. ✅ `analyzeImageWithAI(imageData)` - Universal, no changes needed
2. ✅ `extractDominantColors()` - Universal, no changes needed
3. ✅ `analyzeBrightness()` - Universal, no changes needed
4. ✅ `analyzeColorTemperature()` - Universal, no changes needed

**Customize these functions with your businessConfig:**

5. ⚙️ `generatePromptVariations(analysis)` - Pass your businessConfig
6. ⚙️ `buildImagePromptWithUploadedImage(options, analysis)` - Pass your businessConfig

### Phase 4: Test With Your Images

Upload different image types relevant to YOUR business and verify unique results.

---

## Customization Worksheet

### Fill This Out BEFORE Implementation:

```
BUSINESS IDENTITY
─────────────────
Brand Name: ________________
Industry: ________________
Content Type: ________________ (e.g., "product photography", "event photography", "service imagery")

PRODUCTS/OFFERINGS
──────────────────
Main offerings (list 4-6):
1. ________________
2. ________________
3. ________________
4. ________________

BRAND VOICE
───────────
Tone (check all that apply):
□ Professional    □ Friendly      □ Energetic
□ Premium/Luxury  □ Approachable  □ Athletic
□ Trustworthy     □ Creative      □ Community-focused
□ Scientific      □ Fun           □ ________________

Brand Values (3-5 core values):
1. ________________
2. ________________
3. ________________

TARGET AUDIENCES
────────────────
Primary audiences (list 4-6):
1. ________________
2. ________________
3. ________________
4. ________________

PLATFORMS
─────────
Where do you market? (check all):
□ Instagram       □ Facebook      □ LinkedIn
□ Pinterest       □ TikTok        □ YouTube
□ Website         □ Email         □ Print ads
□ B2B catalogs    □ Amazon        □ ________________

SEASONAL CONTENT
────────────────
Key seasons/promotions (list 3-5):
1. ________________ (dates: ________)
2. ________________ (dates: ________)
3. ________________ (dates: ________)

COLOR PALETTE
─────────────
Brand colors (hex codes if known):
Primary: ________________
Secondary: ________________
Accent: ________________
```

---

## Testing Framework

### Universal Test Cases

**Test 1: Bright Image**
- Upload: Bright, well-lit image of your product/event/service
- Expected: Analysis shows "bright, high-key", generates clean professional prompts

**Test 2: Dark Image**
- Upload: Dark, moody image
- Expected: Analysis shows "dark, low-key", generates dramatic atmospheric prompts

**Test 3: Warm Tones**
- Upload: Warm-toned image (oranges, yellows, browns)
- Expected: Temperature = "warm", prompts reference warm inviting atmosphere

**Test 4: Cool Tones**
- Upload: Cool-toned image (blues, greens, grays)
- Expected: Temperature = "cool", prompts reference professional clean aesthetic

**Test 5: Stage 1 Workflow**
- Upload image → Verify 4 unique variations → Copy one → Works in AI tool

**Test 6: Stage 2 Workflow**
- Upload image → Select all options → Generate → Verify image analysis + options combined

---

## Agent Implementation Prompt (Universal)

```
I need you to implement a two-stage image analysis and content generation system in my [BUSINESS TYPE] content generator.

MY BUSINESS:
- Brand: [YOUR BRAND NAME]
- Industry: [YOUR INDUSTRY]
- Content Type: [PRODUCTS/EVENTS/SERVICES]

REFERENCE SYSTEM:
Location: [PATH TO CHOCOLATE ON JAMES FOLDER]
Files: chocolate-content-creator-pro-v5.2.html, UNIVERSAL-TWO-STAGE-IMAGE-WORKFLOW-SYSTEM.md

TARGET FILE: [YOUR FILE PATH]

BUSINESS-SPECIFIC CUSTOMIZATION:

Categories: [YOUR PRODUCT/EVENT TYPES]
Audiences: [YOUR TARGET AUDIENCES]
Seasons: [YOUR KEY SEASONS/PROMOTIONS]
Brand Voice: [YOUR TONE - professional/athletic/premium/etc.]
Brand Colors: [YOUR COLOR PALETTE]

REQUIREMENTS:
1. Image upload (drag/drop, paste, file browser)
2. Pixel-based analysis (colors, brightness, temperature)
3. Stage 1: 4 quick variations (Exact, Inspired, Premium, [MY BRAND])
4. Stage 2: Image + my business options = comprehensive prompt
5. All prompts reference ACTUAL analyzed image data
6. System works without images (backward compatible)

Please implement step-by-step, testing after each phase.
```

---

**This universal system works for chocolate, kinesiology tape, running races, yoga studios, coffee shops, or ANY business type!**

*Simply fill out the customization worksheet and implement with your business details.*
