# TapeGeeks Implementation Guide
## Two-Stage Image Workflow for Tape Product Content Generator

**Created:** November 15, 2025
**Source System:** Chocolate on James Content Creator PRO v5.2
**Target System:** TapeGeeks Content Generator
**Estimated Implementation Time:** 4-6 hours

---

## Table of Contents
1. [System Adaptation Overview](#system-adaptation-overview)
2. [Pre-Implementation Checklist](#pre-implementation-checklist)
3. [Step-by-Step Implementation](#step-by-step-implementation)
4. [TapeGeeks-Specific Customizations](#tapegeeks-specific-customizations)
5. [Testing Plan](#testing-plan)
6. [Agent Instructions](#agent-instructions)

---

## System Adaptation Overview

### What We're Porting

The **Two-Stage Image Workflow** that allows users to:
1. Upload reference images of tape products (competitor products, inspiration, existing product photos)
2. Get AI analysis of visual characteristics (colors, style, lighting)
3. Generate quick prompt variations OR comprehensive custom prompts

### Key Differences: Chocolate → Tape Products

| Aspect | Chocolate on James | TapeGeeks Adaptation |
|--------|-------------------|---------------------|
| **Product Type** | Chocolates, truffles, boxes | Tape rolls, packaging tape, masking tape, duct tape |
| **Visual Focus** | Luxury, artisan quality, texture | Industrial quality, adhesion, professional application |
| **Color Palette** | Browns, golds, warm tones | Blues, yellows, grays, brand colors |
| **Use Cases** | Gifts, treats, celebrations | Construction, packaging, repairs, creative projects |
| **Brand Voice** | Premium, artisan, local pride | Professional, reliable, industrial strength |
| **Seasonal Content** | Valentine's, Christmas, Easter | Back-to-school, moving season, holiday shipping |

---

## Pre-Implementation Checklist

### 1. Locate Your Existing TapeGeeks Generator File

**Question to answer:**
- [ ] What is the file path to your TapeGeeks content generator?
- [ ] Is it HTML/JavaScript like Chocolate on James, or different technology?
- [ ] What's the current file size?

### 2. Identify Existing Structure

**Map these elements in your current TapeGeeks tool:**

#### Controls Panel (Left Side - Input Controls)
- [ ] Product category selector (e.g., Packaging Tape, Duct Tape, Masking Tape)
- [ ] Platform selector (Instagram, Facebook, LinkedIn, YouTube)
- [ ] Target audience (Contractors, DIY enthusiasts, Businesses, etc.)
- [ ] Tone selector (Professional, Educational, Creative, etc.)
- [ ] Special features checkboxes

#### Output Panel (Right Side - Generated Content)
- [ ] AI image prompt display area
- [ ] Social media captions
- [ ] Copy buttons
- [ ] Export functionality

### 3. Backup Current Version

```bash
# Before ANY changes
cp tapegeeks-generator.html tapegeeks-generator-BACKUP-Nov15-2025.html
```

---

## Step-by-Step Implementation

### PHASE 1: Add Image Upload Infrastructure (1 hour)

#### Step 1.1: Add HTML Upload Section

**Location:** Before your existing controls panel

```html
<!-- IMAGE UPLOAD SECTION -->
<div class="image-upload-section" id="imageUploadSection">
    <div class="section-title">
        📸 Upload Reference Image (Optional)
        <span class="tooltip" data-tooltip="Upload tape product photo for AI-powered prompt generation">ℹ️</span>
    </div>

    <!-- Dropzone -->
    <div class="image-dropzone" id="imageDropzone">
        <div class="dropzone-content">
            <span style="font-size: 3em;">📸</span>
            <p>Drop tape product image here</p>
            <p style="font-size: 0.85em; color: #888;">or paste (Ctrl+V) or click to browse</p>
            <input type="file" id="imageFileInput" accept="image/*" style="display: none;">
            <button onclick="document.getElementById('imageFileInput').click()" class="btn-upload">
                Choose File
            </button>
        </div>
    </div>

    <!-- Analysis Results (hidden by default) -->
    <div class="image-analysis-results hidden" id="imageAnalysisResults">
        <div class="analysis-header">
            <h3>🔍 Image Analysis</h3>
            <button class="btn-clear-analysis" onclick="clearImageAnalysis()">Clear</button>
        </div>
        <div id="analysisDisplay"></div>
        <div class="prompt-variations" id="promptVariations"></div>
    </div>
</div>
```

#### Step 1.2: Add CSS Styling

```css
/* Image Upload Section */
.image-upload-section {
    background: rgba(30, 40, 50, 0.95);
    border-radius: 15px;
    padding: 25px;
    margin-bottom: 20px;
    border: 1px solid rgba(100, 150, 200, 0.2);
}

.image-dropzone {
    border: 2px dashed rgba(100, 150, 200, 0.4);
    border-radius: 10px;
    padding: 40px;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s;
    background: rgba(0, 0, 0, 0.2);
}

.image-dropzone:hover {
    border-color: rgba(100, 150, 200, 0.7);
    background: rgba(100, 150, 200, 0.1);
}

.image-dropzone.dragover {
    border-color: #4CAF50;
    background: rgba(76, 175, 80, 0.1);
}

.btn-upload {
    margin-top: 15px;
    padding: 10px 20px;
    background: linear-gradient(135deg, #2196F3, #1976D2);
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 600;
}

.hidden {
    display: none !important;
}

.image-analysis-results {
    margin-top: 20px;
    padding: 20px;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 10px;
}

/* Upload Banner (shown when image loaded) */
.image-upload-banner {
    background: linear-gradient(135deg, rgba(76, 175, 80, 0.2), rgba(56, 142, 60, 0.2));
    border: 1px solid rgba(76, 175, 80, 0.5);
    border-radius: 10px;
    padding: 15px;
    margin-bottom: 15px;
    display: flex;
    align-items: center;
    gap: 15px;
}

.image-banner-thumbnail {
    width: 60px;
    height: 60px;
    border-radius: 8px;
    object-fit: cover;
    border: 2px solid rgba(255, 255, 255, 0.3);
}

.btn-clear-image {
    background: rgba(244, 67, 54, 0.3);
    border: 1px solid rgba(244, 67, 54, 0.5);
    color: #fff;
    padding: 6px 12px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 0.85em;
}
```

#### Step 1.3: Add JavaScript Event Handlers

```javascript
// State Variables (add to top of <script> section)
let currentImageData = null;
let currentAnalysis = null;
let generatedVariations = [];

// File Input Handler
document.getElementById('imageFileInput').addEventListener('change', function(e) {
    if (e.target.files && e.target.files[0]) {
        handleImageUpload(e.target.files[0]);
    }
});

// Drag and Drop Handlers
const dropzone = document.getElementById('imageDropzone');

dropzone.addEventListener('click', function() {
    document.getElementById('imageFileInput').click();
});

dropzone.addEventListener('dragover', function(e) {
    e.preventDefault();
    dropzone.classList.add('dragover');
});

dropzone.addEventListener('dragleave', function() {
    dropzone.classList.remove('dragover');
});

dropzone.addEventListener('drop', function(e) {
    e.preventDefault();
    dropzone.classList.remove('dragover');

    if (e.dataTransfer.files && e.dataTransfer.files[0]) {
        handleImageUpload(e.dataTransfer.files[0]);
    }
});

// Paste Handler (anywhere on page)
document.addEventListener('paste', function(e) {
    const items = e.clipboardData.items;
    for (let i = 0; i < items.length; i++) {
        if (items[i].type.indexOf('image') !== -1) {
            const blob = items[i].getAsFile();
            handleImageUpload(blob);
            break;
        }
    }
});

// Main Upload Handler
function handleImageUpload(file) {
    if (!file.type.match('image.*')) {
        alert('Please upload an image file (JPG, PNG, WebP)');
        return;
    }

    const reader = new FileReader();
    reader.onload = function(e) {
        currentImageData = e.target.result;
        displayImagePreview(currentImageData);
        analyzeImage(currentImageData);
    };
    reader.readAsDataURL(file);
}
```

---

### PHASE 2: Implement Image Analysis (1.5 hours)

#### Step 2.1: Copy Analysis Functions

**Copy these functions from Chocolate on James v5.2:**

1. `analyzeImageWithAI(imageData)`
2. `extractDominantColors(ctx, width, height)`
3. `analyzeBrightness(ctx, width, height)`
4. `analyzeColorTemperature(colors)`
5. `rgbToHex(r, g, b)`
6. `hexToRgb(hex)`

**Location:** Add before your existing `buildImagePrompt()` function

#### Step 2.2: Customize Analysis for Tape Products

**Modify the brightness/style descriptions:**

```javascript
// In analyzeImageWithAI(), change style descriptions:

// BEFORE (Chocolate):
style: brightness > 180 ? 'Bright, high-key product photography' : ...

// AFTER (TapeGeeks):
style: brightness > 180 ?
    'Bright, clean industrial product photography with professional presentation' :
    brightness > 120 ?
    'Balanced product photography with clear visibility and professional lighting' :
    'Dramatic product photography with strong contrast highlighting texture and detail',
```

**Modify mood descriptions:**

```javascript
// BEFORE (Chocolate):
mood: brightness > 150 ? 'Bright, cheerful, inviting' : 'Warm, intimate, artisan'

// AFTER (TapeGeeks):
mood: brightness > 150 ?
    'Professional, clean, trustworthy, industrial-grade quality' :
    'Strong, durable, reliable, heavy-duty performance'
```

---

### PHASE 3: Create Prompt Variations (1 hour)

#### Step 3.1: Add `generatePromptVariations()` Function

```javascript
function generatePromptVariations(analysis) {
    const colors = analysis.colorPalette.join(', ');
    const brightness = analysis.imageMetrics.avgBrightness;
    const temp = analysis.imageMetrics.temperature;

    generatedVariations = [
        // Variation 1: Exact Match - Recreate Reference
        `Professional tape product photography recreating this exact style: ${analysis.style}.
         Lighting: ${analysis.lighting}.
         Color palette: ${colors}.
         Showcase: ${brightness > 170 ? 'Bright, clean presentation ideal for e-commerce' :
                     'Balanced professional photography with clear product visibility'}.
         Maintain exact brightness level and ${temp} color temperature for brand consistency.
         High-resolution commercial photography suitable for product pages and advertising.`,

        // Variation 2: Inspired - Creative Variation
        `Tape product photography inspired by reference: Similar ${analysis.mood} aesthetic
         with creative interpretation. Quality level: ${analysis.style}.
         Color inspiration: ${colors}. Keep ${temp} tones but explore different angles
         showing product application and versatility. Professional commercial quality
         emphasizing durability and industrial strength.`,

        // Variation 3: Premium - Elevated Version
        `Ultra-professional industrial product photography: ${analysis.style} elevated
         to premium commercial standard. Enhanced lighting showcasing adhesive quality,
         perfect ${colors} color accuracy, extreme close-up detail of texture and material.
         ${brightness > 170 ? 'Pristine clean presentation for high-end marketing' :
                             'Dramatic lighting emphasizing strength and reliability'}.
         Magazine-quality photography for professional catalogs and advertising.`,

        // Variation 4: TapeGeeks Branded
        `TapeGeeks brand product photography: ${analysis.style} adapted for professional
         tape and adhesive brand identity. ${analysis.lighting} showcasing industrial-grade
         quality and reliability. ${temp} professional atmosphere that communicates
         durability, strength, and trusted performance. Include TapeGeeks brand colors
         and professional industrial aesthetic. Photography suitable for website,
         social media, and B2B marketing materials.`
    ];

    // Display variations in UI
    displayPromptVariations();
}
```

---

### PHASE 4: Integrate with Main Generator (1.5 hours)

#### Step 4.1: Add Upload Banner Above Generate Button

```html
<!-- Add this right before your existing "Generate Content" button -->
<div class="image-upload-banner hidden" id="imageUploadBanner">
    <img src="" id="imageBannerThumbnail" class="image-banner-thumbnail" alt="Uploaded">
    <div style="flex: 1;">
        <strong style="color: #4CAF50;">✓ Using Uploaded Image</strong>
        <p style="margin: 5px 0 0 0; font-size: 0.85em; color: #aaa;">
            The AI will style YOUR tape product based on options selected below
        </p>
    </div>
    <button class="btn-clear-image" onclick="clearUploadedImage()">Clear Image</button>
</div>
```

#### Step 4.2: Create TapeGeeks-Specific Prompt Builder

```javascript
function buildImagePromptWithUploadedImage(options, analysis) {
    let prompt = '';

    // 1. SUBJECT FROM UPLOADED IMAGE
    prompt += `SUBJECT FROM UPLOADED REFERENCE IMAGE:\n`;
    prompt += `Product Type: Professional tape product photography\n`;
    prompt += `Visual Style: ${analysis.style}\n`;
    prompt += `Color Palette: ${analysis.colorPalette.join(', ')}\n`;
    prompt += `Lighting: ${analysis.lighting}\n`;
    prompt += `Mood: ${analysis.mood}\n`;
    prompt += `Brightness: ${analysis.imageMetrics.avgBrightness > 170 ? 'High-key/Bright' :
                             analysis.imageMetrics.avgBrightness > 85 ? 'Balanced' : 'Low-key/Dramatic'}\n`;
    prompt += `Color Temperature: ${analysis.imageMetrics.temperature}\n\n`;

    // 2. PLATFORM OPTIMIZATION
    prompt += `PLATFORM OPTIMIZATION:\n`;
    const platforms = {
        'instagram': '1:1 square, Instagram product post',
        'facebook': '1.91:1 landscape, Facebook business post',
        'linkedin': '1.91:1 landscape, LinkedIn B2B post',
        'youtube': '16:9 landscape, YouTube thumbnail',
        'website': 'Flexible ratio, high-resolution product page'
    };
    prompt += `- Format: ${platforms[options.platform] || platforms['instagram']}\n\n`;

    // 3. PRODUCT CATEGORY SPECIFIC
    prompt += `PRODUCT CATEGORY:\n`;
    const categoryDetails = {
        'packaging-tape': 'Packaging tape - emphasize adhesion, clarity, industrial strength',
        'duct-tape': 'Duct tape - highlight durability, versatility, heavy-duty performance',
        'masking-tape': 'Masking tape - showcase precision, clean lines, professional application',
        'double-sided': 'Double-sided tape - demonstrate strong bond, invisible application',
        'specialty': 'Specialty tape - emphasize unique features and specialized applications'
    };
    prompt += `- ${categoryDetails[options.category] || 'Professional tape product'}\n\n`;

    // 4. TARGET AUDIENCE
    prompt += `TARGET AUDIENCE:\n`;
    const audienceMessages = {
        'contractors': 'Professional contractors - emphasize reliability, industrial strength, job-site performance',
        'diy': 'DIY enthusiasts - highlight ease of use, versatility, project success',
        'businesses': 'Business/commercial - focus on efficiency, cost-effectiveness, professional results',
        'artists': 'Artists & creators - showcase creative applications, precision, clean results',
        'warehouse': 'Warehouse/shipping - emphasize volume usage, secure packaging, efficiency'
    };
    prompt += `- ${audienceMessages[options.audience] || 'General professional users'}\n\n`;

    // 5. USE CASE / APPLICATION
    if (options.useCase) {
        prompt += `APPLICATION CONTEXT:\n`;
        prompt += `- Show product in use: ${options.useCase}\n`;
        prompt += `- Demonstrate effectiveness and professional application\n\n`;
    }

    // 6. SEASONAL / PROMOTIONAL
    if (options.season && options.season !== 'any') {
        prompt += `SEASONAL CONTEXT:\n`;
        const seasonal = {
            'back-to-school': 'Back-to-school season - organize, label, prepare',
            'moving-season': 'Moving season (summer) - secure packing, reliable moving',
            'holiday-shipping': 'Holiday shipping season - secure packages, gift wrapping',
            'spring-projects': 'Spring projects - renovations, improvements, DIY'
        };
        prompt += `- ${seasonal[options.season]}\n\n`;
    }

    // 7. TECHNICAL SPECIFICATIONS
    prompt += `TECHNICAL REQUIREMENTS:\n`;
    prompt += `- Resolution: 4K-8K, 300 DPI for print\n`;
    prompt += `- Focus: Tack-sharp on product, professional lens quality\n`;
    prompt += `- Color Accuracy: ${analysis.colorPalette.join(', ')}\n`;
    prompt += `- Lighting: ${analysis.lighting} enhanced for product clarity\n`;
    prompt += `- Background: ${brightness > 170 ? 'Clean white or light gray' : 'Professional neutral backdrop'}\n\n`;

    // 8. BRAND ELEMENTS
    prompt += `BRANDING:\n`;
    prompt += `- TapeGeeks brand identity: Professional, reliable, industrial-grade quality\n`;
    prompt += `- Color scheme: TapeGeeks brand colors incorporated naturally\n`;
    if (options.includeLogo) {
        prompt += `- Reserve space for TapeGeeks logo (bottom right)\n`;
    }
    prompt += `\n`;

    // 9. FINAL INSTRUCTION
    prompt += `FINAL RESULT: Professional ${options.platform} product photography that preserves
    the visual aesthetic from uploaded image (colors: ${analysis.colorPalette.slice(0, 3).join(', ')},
    ${brightness > 170 ? 'bright clean presentation' : 'balanced professional lighting'}),
    while showcasing TapeGeeks ${options.category || 'tape products'} for ${options.audience || 'professional users'}.
    Photography must emphasize product quality, reliability, and professional-grade performance.`;

    return {
        prompt: prompt,
        platform: options.platform || 'Instagram'
    };
}
```

#### Step 4.3: Update Main Dispatcher

```javascript
function buildImagePrompt(options) {
    // Check if image analysis exists (Stage 2 mode)
    if (currentAnalysis !== null) {
        return buildImagePromptWithUploadedImage(options, currentAnalysis);
    }

    // No image - use existing generic prompt builder
    return buildGenericImagePrompt(options);
}
```

---

### PHASE 5: UI State Management (30 minutes)

#### Step 5.1: Add Helper Functions

```javascript
function displayImagePreview(imageData) {
    document.getElementById('imageAnalysisResults').classList.remove('hidden');
    showImageModeBanner(imageData);
}

function showImageModeBanner(imageData) {
    const banner = document.getElementById('imageUploadBanner');
    const thumbnail = document.getElementById('imageBannerThumbnail');

    banner.classList.remove('hidden');
    thumbnail.src = imageData;

    // Update generate button text
    const btn = document.getElementById('btn-generate');
    if (btn) {
        btn.textContent = '✨ Generate Content Using Uploaded Image';
    }
}

function clearUploadedImage() {
    if (confirm('Clear uploaded image? You can upload again anytime.')) {
        currentImageData = null;
        currentAnalysis = null;
        generatedVariations = [];

        document.getElementById('imageUploadBanner').classList.add('hidden');
        document.getElementById('imageAnalysisResults').classList.add('hidden');
        document.getElementById('imageFileInput').value = '';

        // Reset button text
        const btn = document.getElementById('btn-generate');
        if (btn) {
            btn.textContent = '✨ Generate Complete Content';
        }
    }
}

function clearImageAnalysis() {
    clearUploadedImage();
}
```

---

## TapeGeeks-Specific Customizations

### 1. Product Categories (Replace Chocolate Categories)

```javascript
const tapeCategories = {
    'packaging-tape': {
        name: 'Packaging Tape',
        description: 'Clear, strong adhesive for secure package sealing',
        keywords: 'shipping, packaging, e-commerce, warehouse, secure seal'
    },
    'duct-tape': {
        name: 'Duct Tape',
        description: 'Heavy-duty multi-purpose tape for repairs and construction',
        keywords: 'construction, repairs, heavy-duty, versatile, industrial'
    },
    'masking-tape': {
        name: 'Masking Tape',
        description: 'Precision tape for painting, labeling, and delicate surfaces',
        keywords: 'painting, precision, clean lines, temporary, removable'
    },
    'double-sided': {
        name: 'Double-Sided Tape',
        description: 'Strong adhesive on both sides for permanent bonding',
        keywords: 'mounting, crafts, invisible bond, permanent, mounting'
    },
    'specialty': {
        name: 'Specialty Tape',
        description: 'Specialized tapes for unique applications',
        keywords: 'electrical, anti-slip, reflective, heat-resistant, custom'
    }
};
```

### 2. Target Audiences (Replace Chocolate Audiences)

```javascript
const audiences = {
    'contractors': 'Professional Contractors',
    'diy': 'DIY Enthusiasts',
    'businesses': 'Businesses & Commercial',
    'warehouse': 'Warehouse & Shipping',
    'artists': 'Artists & Creators',
    'facilities': 'Facilities Management',
    'retail': 'Retail & E-commerce'
};
```

### 3. Use Cases / Applications

```javascript
const useCases = {
    'packaging': 'Secure package sealing and shipping',
    'repairs': 'Quick repairs and fixes',
    'construction': 'Construction and building projects',
    'painting': 'Painting and surface protection',
    'crafts': 'Arts, crafts, and DIY projects',
    'labeling': 'Organization and labeling',
    'mounting': 'Mounting and permanent bonding',
    'industrial': 'Industrial and manufacturing applications'
};
```

### 4. Seasonal Promotions (Replace Chocolate Seasons)

```javascript
const seasons = {
    'back-to-school': 'Back to School (August-September)',
    'moving-season': 'Moving Season (May-August)',
    'holiday-shipping': 'Holiday Shipping (November-December)',
    'spring-projects': 'Spring Projects (March-May)',
    'year-end': 'Year-End Inventory & Organization',
    'any': 'Year-Round / No Seasonal Focus'
};
```

### 5. Brand Voice Adjustments

| Element | Chocolate on James | TapeGeeks |
|---------|-------------------|-----------|
| **Tone** | Warm, inviting, artisan | Professional, reliable, industrial |
| **Key Words** | Handcrafted, premium, luxury | Durable, strong, industrial-grade |
| **Call to Action** | Treat yourself, gift someone | Get the job done, trust the bond |
| **Visual Style** | Warm browns/golds, cozy | Blues/grays, professional, clean |

---

## Testing Plan

### Test Cases for TapeGeeks Implementation

#### Test 1: Bright Product Photo
**Upload:** Clear packaging tape on white background
**Expected Analysis:**
- Brightness: High (>170)
- Colors: Clear/transparent, whites, light grays
- Mood: Clean, professional, trustworthy
**Expected Prompt:** High-key photography, e-commerce ready, clean presentation

#### Test 2: Dark Industrial Photo
**Upload:** Heavy-duty duct tape in workshop setting
**Expected Analysis:**
- Brightness: Low (<85)
- Colors: Dark grays, blacks, industrial tones
- Mood: Strong, durable, heavy-duty
**Expected Prompt:** Dramatic lighting, industrial strength, job-site tough

#### Test 3: Warm-Toned Application Photo
**Upload:** Hand applying masking tape with warm lighting
**Expected Analysis:**
- Temperature: Warm
- Colors: Beiges, yellows, warm tones
- Mood: Approachable, DIY-friendly
**Expected Prompt:** Lifestyle photography, easy application, user-friendly

#### Test 4: Stage 2 Workflow
**Steps:**
1. Upload packaging tape image
2. Select: Instagram, Holiday Shipping season, Business audience
3. Generate
**Expected:** Prompt combines tape image + holiday shipping context + business messaging

---

## Agent Instructions

### Prompt for AI Agent to Implement TapeGeeks System

```
I need you to implement a two-stage image workflow system in my TapeGeeks content generator,
based on the system we built for Chocolate on James.

REFERENCE FILES:
1. Source system: /path/to/chocolate-content-creator-pro-v5.2.html
2. Logic documentation: /path/to/COMPLETE-LOGIC-DOCUMENTATION-V5.2.md
3. Implementation guide: /path/to/TAPEGEEKS-IMPLEMENTATION-GUIDE.md

TARGET FILE:
- My existing TapeGeeks generator file at: [YOUR FILE PATH]

REQUIREMENTS:
1. Add image upload capability (drag/drop, paste, file browser)
2. Implement pixel-based image analysis:
   - Extract dominant colors
   - Analyze brightness (bright/normal/dark)
   - Detect color temperature (warm/cool/neutral)
3. Create two-stage workflow:
   - Stage 1: Generate 4 quick prompt variations from uploaded image
   - Stage 2: Combine uploaded image analysis + user options for comprehensive prompt
4. Customize all prompts for tape products (not chocolate):
   - Product categories: Packaging, Duct, Masking, Double-Sided, Specialty
   - Audiences: Contractors, DIY, Businesses, Warehouse, Artists
   - Tone: Professional, reliable, industrial-grade (not artisan/luxury)
5. Add visual indicators:
   - Upload banner when image is loaded
   - Dynamic button text
   - Clear image functionality
6. Maintain all existing TapeGeeks functionality

CUSTOMIZATION NOTES:
- Replace chocolate-specific terminology with tape product terminology
- Adjust color preferences (blues/grays instead of browns/golds)
- Update mood descriptions (professional/durable instead of warm/artisan)
- Adapt seasonal content (back-to-school, moving season, holiday shipping)

DELIVERABLES:
1. Updated TapeGeeks generator file with two-stage workflow
2. Backup of original file
3. Quick testing guide
4. Summary of changes made

Please implement this step-by-step, testing after each phase.
```

---

## Summary Checklist

Before you start, ensure you have:

- [ ] Backed up original TapeGeeks file
- [ ] Read complete logic documentation
- [ ] Identified all customization points
- [ ] Prepared test images (3-4 different tape products)
- [ ] Allocated 4-6 hours for implementation
- [ ] Have access to both Chocolate and TapeGeeks files

After implementation:

- [ ] Test with bright images
- [ ] Test with dark images
- [ ] Test Stage 1 (quick variations)
- [ ] Test Stage 2 (full custom generation)
- [ ] Test clear functionality
- [ ] Verify original functionality still works

---

**Ready to implement? Follow the phases in order, test each one, and you'll have a powerful image-aware content generator for TapeGeeks!**
