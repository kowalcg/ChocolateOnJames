# 🎯 CHOCOLATE ON JAMES - PROMPT GENERATION ENHANCEMENT PLAN

**Based on Bronte Harbour Classic v1.2 Enhancements**
**Date:** November 10, 2025
**Current Version:** Chocolate on James Content Creator Pro v4.3
**Target Version:** v5.0 (Enhanced AI Platform Optimization)

---

## 📊 ANALYSIS: BRONTE VS CHOCOLATE TOOLS

### **What Bronte Has That Chocolate Needs:**

#### ✅ **1. PLATFORM-SPECIFIC PROMPT OPTIMIZATION**
**Bronte Implementation:**
- Each AI platform (Gemini, ChatGPT, Sora, Sora 2, Midjourney, Grok, Krea) gets **custom-formatted prompts**
- Prompts written in the "language" each AI understands best
- Platform-specific syntax (Midjourney parameters, Sora temporal context, etc.)

**Chocolate Current State:**
- Generic prompts for all AI platforms ❌
- No platform-specific optimization ❌
- Missing advanced features like Sora 2 video context ❌

#### ✅ **2. CUSTOM TEXT IN IMAGE FEATURE**
**Bronte Implementation:**
- Users can specify text to be **rendered directly into the AI-generated image**
- Platform-specific text rendering instructions
- Quick-fill buttons for common text (dates, pricing, urgency)
- Best practices guidance for each AI's text rendering capabilities

**Chocolate Current State:**
- No custom text in image feature ❌
- Users must add text manually in Canva/Photoshop ❌

#### ✅ **3. CATEGORY-SPECIFIC SCENE DESCRIPTIONS**
**Bronte Implementation:**
```javascript
const categoryScenes = {
    'training': {
        scene: 'Solo runner or small group on peaceful training run',
        participants: '1-3 runners in training gear (NO race bibs)',
        setting: 'Quiet morning training route',
        exclude: 'NO race day atmosphere, NO crowds, NO race bibs'
    },
    'registration': {
        scene: 'Race day atmosphere with excited participants',
        participants: '30-50 runners with race bibs',
        setting: 'Event start line area with registration tents',
        exclude: ''
    }
}
```

**Chocolate Current State:**
- Has category subjects and moods ✅
- **Missing:** Detailed scene, participants, setting, and exclusions structure ❌
- Less specific guidance to prevent AI confusion ❌

#### ✅ **4. AUDIENCE-SPECIFIC MODIFIERS**
**Bronte Implementation:**
```javascript
const audienceModifiers = {
    'first-timers': 'Welcoming and encouraging, beginner-friendly, non-intimidating',
    'experienced': 'Competitive performance focus, serious athletic dedication',
    'families': 'Multi-generational, kids and parents together, inclusive fun'
}
```

**Chocolate Current State:**
- Basic audience targeting ⚠️
- **Missing:** Deep audience-specific visual and tonal modifiers ❌

#### ✅ **5. PHASE/TIMELINE CONTEXT**
**Bronte Implementation:**
```javascript
const phaseModifiers = {
    'launch': 'Early announcement energy, registration opening excitement',
    'training': 'Training season preparation, building toward goal',
    'raceday': 'Race day happening NOW, active event, live competition'
}
```

**Chocolate Current State:**
- Has seasonal context ✅
- **Missing:** Launch/campaign phase context (announcement, promo, holiday rush, etc.) ❌

---

## 🎨 ENHANCEMENT STRATEGY FOR CHOCOLATE ON JAMES

### **PHASE 1: Platform-Specific Prompt Optimization** ⭐ HIGH PRIORITY

#### **Implementation Plan:**

1. **Add `optimizePromptForPlatform()` function** (from Bronte)
2. **Create platform-specific formatters:**

```javascript
function optimizePromptForPlatform(genericPrompt, options) {
    const platform = options.aiPlatform;

    // Add custom text instructions if provided
    let customTextInstructions = '';
    if (options.customTextInImage && options.customTextInImage.length > 0) {
        customTextInstructions = buildCustomTextInstructions(options.customTextInImage, platform);
    }

    switch(platform) {
        case 'gemini':
            // Conversational, natural language
            return `Generate an image for me using these specifications:

I need a professional chocolate product photography image for Chocolate on James,
an artisan Hamilton chocolate shop on James Street North.

${genericPrompt}
${customTextInstructions}

Please create this with photorealistic quality, capturing the luxurious artisan
chocolate aesthetic. The image should be in ${getAspectRatio(options.platform)}
aspect ratio, optimized for ${options.platform} posting.

Make it drool-worthy and irresistible - something that makes people crave chocolate!`;

        case 'chatgpt':
            // Structured markdown format
            return `Create a professional photograph with these specifications:

**Business:** Chocolate on James - Artisan Hamilton Chocolate Shop
**Location:** James Street North, Hamilton, Ontario
**Brand:** Premium handcrafted artisan chocolates

${genericPrompt}
${customTextInstructions}

**Format:** ${getAspectRatio(options.platform)} aspect ratio for ${options.platform}
**Quality:** Photorealistic, professional commercial food photography
**Brand Colors:** Chocolate brown (#8B4513), Gold (#D4AF37), Cream (#F5F5DC)

Generate a high-quality image that captures the artisan luxury and irresistible
appeal of handcrafted chocolate.`;

        case 'midjourney':
            // Keyword-based with parameters
            const mjKeywords = extractKeywordsForMidjourney(genericPrompt, options);
            const mjTextKeywords = options.customTextInImage ?
                `, bold text overlay reading "${options.customTextInImage}", elegant typography, readable design` : '';

            return `${mjKeywords.main}

${mjKeywords.details}${mjTextKeywords}

--ar ${getAspectRatio(options.platform, true)} --style raw --quality 2 --stylize 300 --v 6.1

Midjourney Parameters:
- --ar: Aspect ratio for ${options.platform}
- --style raw: Photorealistic food photography (not artistic)
- --quality 2: Maximum quality
- --stylize 300: Professional commercial aesthetic
- --v 6.1: Latest model for photorealism`;

        case 'sora2':
            // Enhanced video with text capability
            return `[SORA 2 VIDEO GENERATION]

Generate professional food photography video for Chocolate on James
(James Street North, Hamilton, Ontario - Artisan Handcrafted Chocolates).

Video Content:
${genericPrompt}
${customTextInstructions}

Motion & Temporal Details:
- Video duration: 5-10 second cinematic sequence
- Product presentation: Slow reveal, elegant rotation, appetizing close-up details
- Camera technique: Professional food videography, smooth gimbal movement, macro focus
- Temporal flow: Opening establish → close-up detail → final hero shot
- Environmental motion: Steam rising (hot chocolate), drizzle pour, natural light shifts

Sora 2 Enhanced Parameters:
- Photorealism: Maximum (Sora 2 food rendering)
- Temporal coherence: Smooth cinematic motion
- Lighting simulation: Natural window light, golden hour warmth
- Material accuracy: Chocolate texture, glossy ganache, cocoa dust detail
- Frame coherence: Consistent quality throughout

Output: 4K-8K photorealistic food video
Brand Colors: Brown/Gold/Cream maintained throughout
Audio: Consider soft ambient cafe sounds`;

        case 'grok':
            // Technical precision
            return `[GROK IMAGE GENERATION REQUEST]

Objective: Generate photorealistic commercial food photography

Business Specifications:
- Business: Chocolate on James
- Type: Artisan handcrafted chocolate shop
- Location: James Street North, Hamilton, Ontario, Canada
- Brand positioning: Premium local artisan chocolates

${genericPrompt}
${customTextInstructions}

Technical Generation Parameters:
- Output format: ${getAspectRatio(options.platform)} aspect ratio
- Rendering mode: Photorealistic commercial food photography
- Image quality: 4K-8K resolution, print-quality
- Color space: sRGB, brand colors: #8B4513 (chocolate), #D4AF37 (gold), #F5F5DC (cream)
- Lighting model: Natural/studio food photography lighting
- Material physics: Accurate chocolate texture, glossy ganache, cocoa dust realism
- Food styling: Professional commercial food photography standards

Grok-Specific Optimization:
- Real-world material physics (chocolate melting point, texture accuracy)
- Geographic authenticity (Hamilton Ontario artisan shop aesthetic)
- Food safety presentation standards
- Commercial food photography conventions
- TEXT RENDERING: Clear typography for any text overlays`;

        case 'krea':
            // Realtime generation
            return `[KREA REALTIME GENERATION]

Base Concept: Professional food photography - Chocolate on James artisan chocolates

${genericPrompt}
${customTextInstructions}

Krea Generation Settings:
- Mode: Photorealistic commercial food photography
- Aspect Ratio: ${getAspectRatio(options.platform)}
- Style Strength: 0.7-0.8 (high photorealism with luxury aesthetic)
- AI Strength: 0.7-0.8 (accurate to prompt, food photography quality)
- Quality: Maximum resolution
- Speed: Quality mode (final render, not realtime preview)

Visual Style References:
- Food photography: Bon Appétit magazine, artisan chocolate catalogs
- Color grading: Warm luxurious palette, rich chocolate tones
- Composition: Professional food styling, appetizing presentation
- Mood: Luxurious, indulgent, artisan, high-end

Krea-Specific Notes:
- Emphasize chocolate texture (glossy, smooth, appetizing)
- Professional food styling with garnishes and props
- Brand color accuracy: Brown/Gold/Cream scheme
- Hamilton artisan aesthetic: authentic, local, handcrafted

Generate photorealistic quality optimized for ${options.platform}.`;

        default:
            return genericPrompt;
    }
}

function getAspectRatio(platform, midjourney = false) {
    const ratios = {
        'instagram-square': midjourney ? '1:1' : '1:1 aspect ratio (square)',
        'instagram-story': midjourney ? '9:16' : '9:16 vertical aspect ratio (portrait)',
        'facebook-ad': midjourney ? '1.91:1' : '1.91:1 landscape aspect ratio',
        'pinterest': midjourney ? '2:3' : '2:3 vertical aspect ratio (tall pin)'
    };
    return ratios[platform] || '1:1';
}

function extractKeywordsForMidjourney(prompt, options) {
    // Extract key concepts for Midjourney
    const category = options.category;

    const categoryKeywords = {
        'product-showcase': 'premium artisan chocolate, professional product photography, luxury presentation',
        'promotional': 'sale promotion, special offer, attention-grabbing, bold commercial photography',
        'seasonal': 'festive holiday chocolate, gift presentation, seasonal celebration',
        'educational': 'chocolate making process, artisan craftsmanship, informative editorial',
        'behind-scenes': 'chocolate shop interior, artisan at work, handcrafting process',
        'lifestyle': 'indulgent moment, self-care, cozy chocolate experience',
        'local-hamilton': 'James Street North, Hamilton Ontario, local artisan shop',
        'customer-engagement': 'interactive social media, fun engaging content, shareable moment'
    };

    let mjMain = `${categoryKeywords[category] || 'artisan chocolate photography'}, Chocolate on James, James Street North Hamilton, artisan handcrafted chocolates, professional commercial food photography`;

    let mjDetails = `premium chocolate product, luxurious presentation, professional food styling, natural lighting, warm inviting atmosphere, brown gold cream colors, ${options.platform.replace('-', ' ')} composition`;

    // Add seasonal keywords
    if (options.season && options.season !== 'any') {
        const seasonalKeywords = {
            'february': 'Valentine\'s Day, romantic, red pink accents, hearts, love theme',
            'october': 'Halloween, autumn colors, festive orange brown, spooky fun',
            'november': 'Thanksgiving, fall harvest, gratitude, warm autumn tones',
            'december': 'Christmas holiday, festive, winter magic, gift-worthy, red green gold'
        };
        if (seasonalKeywords[options.season]) {
            mjDetails += `, ${seasonalKeywords[options.season]}`;
        }
    }

    // Add audience keywords
    if (options.audience) {
        const audienceKeywords = {
            'millennials': 'modern aesthetic, Instagram-worthy, trendy, stylish',
            'parents': 'family-friendly, wholesome, nurturing, gift-giving',
            'corporate': 'professional, sophisticated, premium, business gifting',
            'tourists': 'local landmark, Hamilton pride, artisan local',
            'chocolate-lovers': 'indulgent, decadent, connoisseur quality, premium cocoa'
        };
        if (audienceKeywords[options.audience]) {
            mjDetails += `, ${audienceKeywords[options.audience]}`;
        }
    }

    return { main: mjMain, details: mjDetails };
}

function buildCustomTextInstructions(customText, platform) {
    const textUpper = customText.toUpperCase();

    switch(platform) {
        case 'gemini':
            return `\n\n**IMPORTANT TEXT OVERLAY:**
Include this text in the image: "${textUpper}"

- Position: Prominently visible (top third or center)
- Style: Elegant, clean, professional typography
- Color: Gold (#D4AF37) with chocolate brown shadow OR Cream with brown outline
- Font: Serif or elegant sans-serif (luxury aesthetic)
- Size: Large, social-media-thumbnail-readable
- Integration: Natural part of composition, elegant placement
- Readability: High contrast against background

The text is part of the marketing message - make it elegant and prominent!`;

        case 'chatgpt':
            return `\n\n**TEXT OVERLAY SPECIFICATION:**
Include this exact text: "${textUpper}"

Typography Requirements:
- Font: Elegant serif (Playfair Display, Bodoni) or luxury sans-serif
- Position: Upper third or centered for maximum visibility
- Color: Gold (#D4AF37) with brown outline OR Cream with chocolate shadow
- Size: 72-96pt equivalent (large luxury scale)
- Style: Elegant, sophisticated, high-end aesthetic
- Contrast: Ensure readability (semi-transparent overlay if needed)
- Brand alignment: Luxury chocolate aesthetic

Make the text impossible to miss while maintaining elegance!`;

        case 'midjourney':
            // Already handled in main keywords
            return '';

        case 'sora2':
            return `\n\n**TEXT IN VIDEO FRAME:**
Render this text: "${textUpper}"

- Typography: Elegant serif or luxury sans-serif
- Placement: Strategic position (elegant banner or overlay)
- Animation: Text visible throughout sequence (not mid-fade)
- Color: Gold with chocolate outline (brand colors)
- Scale: Large, thumbnail-readable, luxury aesthetic
- Background: Subtle overlay for readability if needed
- Brand consistency: High-end chocolate aesthetic

Text should feel naturally integrated into luxury video!`;

        case 'grok':
            return `\n\n**GROK TEXT RENDERING:**
Generate text overlay: "${textUpper}"

Technical Specifications:
- Typography: Vector-quality elegant serif or luxury sans-serif
- Positioning: Optimal rule-of-thirds placement
- Color theory: High-contrast gold/chocolate or cream/brown
- Legibility: 72pt minimum, stroke/shadow for separation
- Brand alignment: Luxury chocolate aesthetic
- Text accuracy: Zero tolerance for misspellings
- Integration: Professional graphic design standard

Text must be readable at thumbnail size with luxury aesthetic!`;

        case 'krea':
            return `\n\n**KREA TEXT OVERLAY:**
Include text: "${textUpper}"

Parameters:
- Font weight: Medium-Bold (500-700) - elegant not heavy
- Font family: Elegant serif or luxury sans-serif
- Position: Upper or center region
- Color: Gold + chocolate shadow OR Cream + brown outline
- Scale: Large, prominent, luxury aesthetic
- Effect: Subtle shadow or stroke (elegant not harsh)
- Background: Overlay if needed for readability
- Style: High-end chocolate brand aesthetic

Prioritize elegance and readability!`;

        default:
            return `\n\nIMPORTANT: Include this text prominently: "${textUpper}"
Make it elegant, large, and visible with luxury chocolate aesthetic.`;
    }
}
```

---

### **PHASE 2: Enhanced Category Scene Structure** ⭐ HIGH PRIORITY

**Current Chocolate Categories:**
- product-showcase
- promotional
- seasonal
- educational
- behind-scenes
- lifestyle
- local-hamilton
- customer-engagement
- custom

**Enhancement: Add Detailed Scene Structure**

```javascript
function buildImagePrompt(options) {
    // ... existing code ...

    // NEW: Category-specific scene descriptions (like Bronte)
    const categoryScenes = {
        'product-showcase': {
            scene: 'Professional commercial product photography setup showcasing premium handcrafted chocolates as hero subject',
            subject: 'Individual chocolate pieces or elegant box arrangement displayed with museum-quality presentation',
            setting: 'Clean professional studio or elegant boutique display with premium presentation elements',
            exclude: 'Avoid cluttered backgrounds, amateur styling, or distracting elements that detract from chocolate quality'
        },
        'promotional': {
            scene: 'Bold eye-catching promotional photography with strong visual impact and clear value proposition',
            subject: 'Featured chocolate products with promotional elements (savings, limited time, special offer visual cues)',
            setting: 'Commercial advertising environment with attention-grabbing composition and urgency-creating atmosphere',
            exclude: 'Avoid subtle or understated presentation - this needs to POP and command attention'
        },
        'seasonal': {
            scene: 'Festive seasonal celebration photography with elegant gift-worthy presentation and holiday magic',
            subject: 'Beautifully wrapped chocolate gifts or seasonal chocolate arrangements with holiday styling',
            setting: 'Festive holiday environment with seasonal decorations, warm lighting, and celebratory atmosphere',
            exclude: 'Avoid generic presentation - should feel special occasion and gift-worthy'
        },
        'educational': {
            scene: 'Clear informative editorial photography demonstrating chocolate knowledge, process, or storage techniques',
            subject: 'Chocolate making process, storage examples, or educational demonstration with clear visual communication',
            setting: 'Professional teaching environment or artisan workshop with informative context',
            exclude: 'Avoid overly artistic shots - clarity and information delivery is priority'
        },
        'behind-scenes': {
            scene: 'Authentic documentary-style photography capturing real artisan chocolate creation moments',
            subject: 'Artisan chocolatier hands at work, chocolate making process, authentic craft moments',
            setting: 'Real chocolate shop workspace, James Street North location, authentic artisan environment',
            exclude: 'CRITICAL: This is REAL behind-scenes, not staged. NO overly perfect product shots, NO studio lighting. Authentic workshop atmosphere only.'
        },
        'lifestyle': {
            scene: 'Aspirational lifestyle photography featuring chocolate as part of indulgent self-care moments',
            subject: 'Person enjoying chocolate in cozy relaxation setting or special indulgent moment',
            setting: 'Warm inviting lifestyle environment - cozy reading nook, cafe table, relaxation space',
            exclude: 'Avoid clinical product shots - this is about the EXPERIENCE and FEELING of indulgence'
        },
        'local-hamilton': {
            scene: 'Vibrant Hamilton community photography celebrating James Street North character and local pride',
            subject: 'Chocolate on James storefront, James Street North location, Hamilton local atmosphere',
            setting: 'James Street North streetscape, Hamilton urban character, local artisan shop environment',
            exclude: 'Must feel authentically Hamilton/James Street North - not generic shop photography'
        },
        'customer-engagement': {
            scene: 'Dynamic interactive social media photography designed for maximum shareability and engagement',
            subject: 'Fun engaging chocolate moment perfect for social sharing - poll-worthy, comment-inducing, highly interactive',
            setting: 'Social media optimized environment with clean shareable composition',
            exclude: 'Avoid formal commercial shots - this needs personality, fun, and social media appeal'
        },
        'custom': {
            scene: options.customCategory || 'Professional branded content photography',
            subject: 'Premium artisan chocolates',
            setting: 'Professional commercial environment',
            exclude: ''
        }
    };

    // Get category-specific details
    const sceneDetails = categoryScenes[options.category] || categoryScenes['custom'];

    // Build prompt with category structure
    let prompt = `Create a stunning high-quality photograph for Chocolate on James with these specifications:

SCENE & SUBJECT:
${sceneDetails.scene}

MAIN SUBJECT:
${sceneDetails.subject}

SETTING:
${sceneDetails.setting}

BUSINESS CONTEXT (Reference):
- Business: Chocolate on James
- Location: James Street North, Hamilton, Ontario
- Product: Premium handcrafted artisan chocolates
- Brand: Luxury local artisan chocolate shop

COMPOSITION & STYLE:
- Image format: ${platformSpecs[options.platform]}
- Photography style: ${styleSpecs[options.style] || 'professional commercial food photography'}
- Camera settings: Macro lens for detail (if close-up), shallow depth of field (f/2.8-f/4), professional food photography standards
- Composition: Rule of thirds, appetizing presentation, balanced visual weight
- Mood: ${categoryMoods[options.category]}`;

    // Add exclusions
    if (sceneDetails.exclude) {
        prompt += `\n\n⚠️ CRITICAL EXCLUSIONS:
${sceneDetails.exclude}`;
    }

    // ... rest of existing prompt building ...

    return {
        platform: options.aiPlatform.toUpperCase(),
        prompt: optimizePromptForPlatform(prompt, options), // NEW: Platform optimization
        includeLogo: options.includeLogo
    };
}
```

---

### **PHASE 3: Audience-Specific Modifiers** ⭐ MEDIUM PRIORITY

**Add audience modifiers to affect visual presentation:**

```javascript
// NEW: Audience-specific visual and tonal modifiers
const audienceModifiers = {
    'millennials': 'Instagram-worthy aesthetic, modern trendy presentation, social media optimized styling, authentic not overly formal, visually striking shareable moment',
    'parents': 'Family-friendly wholesome atmosphere, gift-giving focus, nurturing presentation, thoughtful gesture emphasis, accessible and relatable',
    'corporate': 'Professional sophisticated presentation, premium business gifting aesthetic, corporate quality standards, polished executive appeal',
    'tourists': 'Hamilton local landmark integration, authentic James Street North character, destination appeal, Canadian artisan pride, memorable local experience',
    'chocolate-lovers': 'Connoisseur-level detail, premium cocoa quality emphasis, artisan craftsmanship showcase, indulgent decadent presentation, chocolate expertise visible',
    'wedding': 'Romantic elegant presentation, special occasion sophistication, luxury wedding favor aesthetic, timeless classic beauty',
    'holiday-shoppers': 'Gift-worthy presentation, festive seasonal styling, value and quality visible, perfect present atmosphere',
    'custom': options.customAudience || 'General appeal with broad accessibility'
};

// In buildImagePrompt, add:
TARGET AUDIENCE FOCUS:
${audienceModifiers[options.audience] || audienceModifiers['custom']}
${options.customAudience ? `\nCustom audience: ${options.customAudience}` : ''}
```

---

### **PHASE 4: Campaign Phase Context** ⭐ MEDIUM PRIORITY

**Add launch/campaign timing context:**

```javascript
// NEW: Campaign phase modifiers (similar to Bronte's race timeline)
const campaignPhaseModifiers = {
    'launch': 'New product launch energy, introducing new chocolate, first reveal excitement, debut announcement atmosphere',
    'promotion': 'Active sale promotion, limited-time offer urgency, special deal emphasis, value-focused presentation',
    'holiday-rush': 'Peak holiday shopping season, gift deadline urgency, festive seasonal magic, last-minute gift solution',
    'everyday': 'Regular inventory showcase, always-available classic products, everyday luxury moment',
    'pre-order': 'Coming soon anticipation, advance ordering opportunity, exclusive early access atmosphere',
    'custom': options.customTiming || 'Current inventory and offerings'
};

// In buildImagePrompt, add:
CAMPAIGN TIMING CONTEXT:
${campaignPhaseModifiers[options.phase] || campaignPhaseModifiers['everyday']}
${options.customTiming ? `\nSpecific timing: ${options.customTiming}` : ''}
```

**Add Phase Selector to HTML:**

```html
<div class="section">
    <div class="section-title">📅 Campaign Phase</div>
    <select id="phase">
        <option value="everyday">Regular Inventory</option>
        <option value="launch">New Product Launch</option>
        <option value="promotion">Sale/Promotion Active</option>
        <option value="holiday-rush">Holiday Shopping Season</option>
        <option value="pre-order">Pre-Order / Coming Soon</option>
        <option value="custom">⚙ Custom Phase Below ⚙</option>
    </select>
    <div class="input-group" style="margin-top: 10px;">
        <input type="text" id="custom-timing" placeholder="e.g., Valentine's Week Rush, Easter Pre-Orders, Summer Launch">
        <div class="input-help">Specific campaign timing or product launch schedule</div>
    </div>
</div>
```

---

### **PHASE 5: Custom Text in Image** ⭐ HIGH PRIORITY

**Add custom text feature (from Bronte):**

```html
<!-- Add this under "Image Elements" section -->
<div class="section" style="margin-top: 10px; background: rgba(212, 175, 55, 0.05); padding: 15px; border-radius: 8px; border: 1px solid rgba(212, 175, 55, 0.2);">
    <label for="custom-text-in-image" style="display: block; margin-bottom: 8px; color: #d4a574; font-weight: 600; font-size: 0.9em;">
        📝 Custom Text IN Image (Optional)
        <span class="tooltip" data-tooltip="AI will include this text in the generated image - perfect for promotions, dates, pricing!">ℹ️</span>
    </label>
    <input
        type="text"
        id="custom-text-in-image"
        placeholder="e.g. VALENTINE'S DAY or 15% OFF or HANDMADE IN HAMILTON"
        style="width: 100%; padding: 10px; border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 5px; background: rgba(0,0,0,0.3); color: #fff; font-size: 0.9em;"
    >
    <p style="margin-top: 8px; font-size: 0.75em; color: #8B7355; line-height: 1.4;">
        💡 <strong>Pro Tip:</strong> Keep text short (3-5 words max). Use ALL CAPS for impact. ChatGPT and Midjourney work best for text rendering.
    </p>
    <div style="margin-top: 10px; display: flex; gap: 5px; flex-wrap: wrap;">
        <button onclick="document.getElementById('custom-text-in-image').value='VALENTINE\'S DAY'" style="padding: 5px 10px; background: rgba(212,175,55,0.2); border: 1px solid rgba(212,175,55,0.4); border-radius: 15px; color: #d4a574; cursor: pointer; font-size: 0.75em;">Quick: Valentine's</button>
        <button onclick="document.getElementById('custom-text-in-image').value='15% OFF THIS WEEK'" style="padding: 5px 10px; background: rgba(212,175,55,0.2); border: 1px solid rgba(212,175,55,0.4); border-radius: 15px; color: #d4a574; cursor: pointer; font-size: 0.75em;">Quick: 15% Off</button>
        <button onclick="document.getElementById('custom-text-in-image').value='HANDMADE IN HAMILTON'" style="padding: 5px 10px; background: rgba(212,175,55,0.2); border: 1px solid rgba(212,175,55,0.4); border-radius: 15px; color: #d4a574; cursor: pointer; font-size: 0.75em;">Quick: Hamilton Made</button>
        <button onclick="document.getElementById('custom-text-in-image').value='LIMITED EDITION'" style="padding: 5px 10px; background: rgba(212,175,55,0.2); border: 1px solid rgba(212,175,55,0.4); border-radius: 15px; color: #d4a574; cursor: pointer; font-size: 0.75em;">Quick: Limited</button>
    </div>
</div>
```

```javascript
// In getOptions():
customTextInImage: document.getElementById('custom-text-in-image').value.trim(),
```

---

## 🎯 IMPLEMENTATION PRIORITY

### **MUST HAVE (Week 1):**
1. ✅ Platform-specific prompt optimization (`optimizePromptForPlatform()`)
2. ✅ Custom text in image feature
3. ✅ Enhanced category scene structure

### **SHOULD HAVE (Week 2):**
4. ✅ Audience-specific modifiers
5. ✅ Campaign phase context
6. ✅ Midjourney keyword extraction

### **NICE TO HAVE (Week 3):**
7. ✅ Platform comparison guide document
8. ✅ Text rendering best practices guide
9. ✅ Example outputs showcase

---

## 📊 EXPECTED RESULTS

### **Before Enhancement:**
- Generic prompts for all AI platforms
- Users manually add text overlays
- Less specific scene guidance
- Basic audience targeting
- No campaign timing context

### **After Enhancement:**
- ✅ **7 AI platforms** with custom-optimized prompts
- ✅ **Text rendered directly** into AI-generated images
- ✅ **Detailed scene descriptions** prevent AI confusion
- ✅ **Audience-specific visuals** match target customer
- ✅ **Campaign timing context** sets proper atmosphere
- ✅ **Midjourney keywords** for artistic control
- ✅ **Sora 2 video context** for motion-based images
- ✅ **Platform-specific syntax** (parameters, formatting)

---

## 🚀 NEXT STEPS

1. **Review this document** with stakeholders
2. **Approve enhancement scope** and priority
3. **Begin Phase 1 implementation** (platform optimization)
4. **Test with real content** (Valentine's Day campaign)
5. **Iterate based on results**
6. **Document in user guide**
7. **Release v5.0**

---

## 📋 SUCCESS METRICS

- ✅ All 7 AI platforms supported with custom prompts
- ✅ Custom text feature working across all platforms
- ✅ Category scenes prevent AI confusion (90%+ accuracy)
- ✅ Audience modifiers change visual presentation
- ✅ Campaign timing affects prompt atmosphere
- ✅ User can copy-paste prompts directly to any AI
- ✅ Generated images require minimal post-editing

---

**ENHANCEMENT PLAN COMPLETE - READY FOR IMPLEMENTATION** 🎯

**Estimated Development Time:** 6-8 hours
**Target Release:** Chocolate on James Content Creator PRO v5.0
**Key Benefit:** Platform-optimized prompts = MUCH better AI-generated images

