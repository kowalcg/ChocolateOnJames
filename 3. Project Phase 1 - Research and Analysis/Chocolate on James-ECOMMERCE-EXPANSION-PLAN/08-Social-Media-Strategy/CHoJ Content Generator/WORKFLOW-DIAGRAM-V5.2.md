# Two-Stage Image Workflow - Visual Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CONTENT CREATOR PRO v5.2                             │
│                   TWO-STAGE IMAGE WORKFLOW                              │
└─────────────────────────────────────────────────────────────────────────┘


                              USER UPLOADS IMAGE
                         (Drag/Drop/Paste/Click)
                                    │
                                    ├─────────────────────────────┐
                                    │                             │
                                    ▼                             ▼
                        ┌───────────────────────┐   ┌─────────────────────────┐
                        │   IMAGE ANALYSIS      │   │  VISUAL INDICATORS      │
                        │                       │   │                         │
                        │ • Extract colors      │   │ • Green banner shows    │
                        │ • Analyze brightness  │   │ • Thumbnail preview     │
                        │ • Detect temperature  │   │ • "Clear Image" button  │
                        │ • Assess mood         │   │ • Button text changes   │
                        └───────────┬───────────┘   └─────────────────────────┘
                                    │
                                    │
                    ┌───────────────┴──────────────┐
                    │                              │
                    ▼                              ▼
        ┌──────────────────────┐      ┌──────────────────────────┐
        │   STAGE 1 (QUICK)    │      │  STAGE 2 (CUSTOM)        │
        │                      │      │                          │
        │ 4 Prompt Variations: │      │ User Customizes:         │
        │                      │      │                          │
        │ 1️⃣ Exact Match       │      │ • Platform (IG/FB/Pin)  │
        │ 2️⃣ Inspired          │      │ • Season (Dec/Feb/etc)  │
        │ 3️⃣ Premium Elevated  │      │ • Audience (Gifts/Corp) │
        │ 4️⃣ CHoJ Branded      │      │ • Style (Photo/Life)    │
        │                      │      │ • Category              │
        │ Each has:            │      │ • Product name          │
        │ • Copy button        │      │ • Special notes         │
        │ • Use button ➡️      │      │                          │
        └──────────┬───────────┘      └───────────┬──────────────┘
                   │                              │
                   │ Click "Use"                  │ Click "Generate"
                   │                              │
                   ▼                              ▼
        ┌──────────────────────┐      ┌──────────────────────────┐
        │ Uses EXACT variation │      │ buildImagePromptWith     │
        │ prompt as-is         │      │ UploadedImage()          │
        │                      │      │                          │
        │ • No customization   │      │ Combines:                │
        │ • Instant result     │      │ • Image analysis ✓       │
        │ • Best for quick use │      │ • User controls ✓        │
        └──────────┬───────────┘      │ • Platform specs ✓       │
                   │                  │ • Seasonal elements ✓    │
                   │                  │ • Audience targeting ✓   │
                   │                  └───────────┬──────────────┘
                   │                              │
                   └──────────────┬───────────────┘
                                  │
                                  ▼
                    ┌────────────────────────────┐
                    │     GENERATE CONTENT       │
                    │                            │
                    │ • AI Image Prompt          │
                    │ • 10 Social Captions       │
                    │ • Hashtags                 │
                    │ • CTAs                     │
                    │ • Platform optimized       │
                    └────────────────────────────┘


═══════════════════════════════════════════════════════════════════════════


                          DETAILED WORKFLOW PATHS


PATH A: QUICK VARIATIONS (Stage 1 Only)
──────────────────────────────────────────────────────────────────────────

User Journey:
1. Upload image (chocolate truffles on table)
2. See 4 variations instantly
3. Click "Use" on "CHoJ Branded" variation
4. Get complete content immediately

Time: 30 seconds
Best for: Quick inspiration, testing styles


PATH B: FULL CUSTOMIZATION (Stage 2)
──────────────────────────────────────────────────────────────────────────

User Journey:
1. Upload image (chocolate truffles on table)
2. See green banner: "Using Uploaded Image"
3. Ignore quick variations
4. Set controls:
   Platform: Instagram Post
   Season: December (Christmas)
   Audience: Gift Buyers
   Style: Lifestyle
   Product: "Holiday Truffle Collection"
5. Click "Generate Content Using Uploaded Image"
6. Get comprehensive prompt + 10 captions

Time: 2 minutes
Best for: Targeted campaigns, seasonal content, audience-specific


PATH C: HYBRID APPROACH
──────────────────────────────────────────────────────────────────────────

User Journey:
1. Upload image
2. Review quick variations (get ideas)
3. Don't click "Use"
4. Use insights to customize left panel
5. Generate custom content
6. Compare custom vs quick variations

Time: 3 minutes
Best for: Learning, experimentation, comparison


═══════════════════════════════════════════════════════════════════════════


                       TECHNICAL FLOW DIAGRAM


┌──────────────────────────────────────────────────────────────────────────┐
│                         FUNCTION CALL FLOW                               │
└──────────────────────────────────────────────────────────────────────────┘

User uploads image
    │
    ├─> handleImageFile(file)
    │       │
    │       ├─> displayImagePreview(imageData)
    │       │       │
    │       │       ├─> showImageModeBanner(imageData)  🆕 v5.2
    │       │       │       │
    │       │       │       ├─> Show green banner
    │       │       │       ├─> Update thumbnail
    │       │       │       └─> Change button text
    │       │       │
    │       │       └─> Show "Analyzing..." state
    │       │
    │       └─> analyzeImage(imageData)
    │               │
    │               ├─> analyzeImageWithAI(imageData)
    │               │       │
    │               │       ├─> extractDominantColors()
    │               │       ├─> analyzeBrightness()
    │               │       ├─> analyzeColorTemperature()
    │               │       └─> Build analysis object
    │               │
    │               ├─> Store in currentAnalysis
    │               ├─> displayAnalysis(analysis)
    │               └─> generatePromptVariations(analysis)
    │                       │
    │                       └─> Create 4 variations
    │
    └─> Ready for user action


User clicks "Generate" (Stage 2)
    │
    ├─> generateContent()
    │       │
    │       ├─> getOptions() from left panel
    │       │
    │       ├─> buildImagePrompt(options)
    │       │       │
    │       │       ├─> Check: window.selectedImagePrompt?
    │       │       │   ├─> YES: Return variation (Stage 1)
    │       │       │   └─> NO: Continue ▼
    │       │       │
    │       │       ├─> Check: currentAnalysis exists? 🆕 v5.2
    │       │       │   ├─> YES: buildImagePromptWithUploadedImage() ⭐
    │       │       │   │       │
    │       │       │   │       ├─> Get image analysis data
    │       │       │   │       ├─> Get user options
    │       │       │   │       ├─> Combine intelligently
    │       │       │   │       └─> Return comprehensive prompt
    │       │       │   │
    │       │       │   └─> NO: Build generic prompt
    │       │       │
    │       │       └─> Return prompt object
    │       │
    │       ├─> buildSocialMediaCopy(options)
    │       │       │
    │       │       └─> Generate 10 captions with hashtags
    │       │
    │       └─> displayContent(imagePrompt, socialPosts, options)
    │               │
    │               ├─> Show "Using Your Image" badge 🆕 v5.2
    │               ├─> Display AI prompt
    │               └─> Display 10 social posts
    │
    └─> Content ready!


User clicks "Use" on variation (Stage 1)
    │
    ├─> sendToGenerator(index)
    │       │
    │       ├─> Store variation in window.selectedImagePrompt
    │       ├─> Call generateContent()
    │       │       │
    │       │       └─> buildImagePrompt() sees selectedImagePrompt
    │       │               │
    │       │               └─> Returns that exact variation
    │       │
    │       └─> Clear selectedImagePrompt after use
    │
    └─> Content ready!


User clicks "Clear Image"
    │
    ├─> clearUploadedImage() 🆕 v5.2
    │       │
    │       ├─> Confirm with user
    │       ├─> Clear currentImageData
    │       ├─> Clear currentAnalysis
    │       ├─> Hide banner
    │       ├─> Reset button text
    │       └─> Hide analysis results
    │
    └─> Ready for fresh upload or generic generation


═══════════════════════════════════════════════════════════════════════════


                         STATE MANAGEMENT


┌─────────────────────────────────────────────────────────────────────────┐
│ GLOBAL STATE VARIABLES                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│ currentImageData           Image base64 data                           │
│ currentAnalysis            Analysis object (colors, brightness, etc)   │
│ generatedVariations[]      Array of 4 quick variations                │
│ window.selectedImagePrompt Variation selected via "Use" button        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

State Transitions:

NO IMAGE STATE
├─ currentImageData: null
├─ currentAnalysis: null
├─ Banner: Hidden
├─ Button: "Generate Complete Content"
└─ Behavior: Generic prompts

    │ (Upload image)
    ▼

IMAGE UPLOADED STATE (Stage 2 Ready) 🆕 v5.2
├─ currentImageData: <base64>
├─ currentAnalysis: <object>
├─ Banner: Visible (green)
├─ Button: "Generate Content Using Uploaded Image"
└─ Behavior: Use image + controls

    │ (Click "Use" on variation)
    ▼

VARIATION SELECTED STATE (Stage 1)
├─ window.selectedImagePrompt: <string>
├─ Banner: Still visible
├─ Button: Normal
└─ Behavior: Use exact variation, ignore controls

    │ (Generate completes)
    ▼

GENERATED STATE
├─ Previous state maintained
├─ Output shown
└─ Can regenerate or clear

    │ (Click "Clear Image")
    ▼

NO IMAGE STATE (reset to start)


═══════════════════════════════════════════════════════════════════════════


                        KEY DECISION POINTS


buildImagePrompt() Decision Tree:
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│  Is window.selectedImagePrompt set?                                    │
│  ├─ YES → Return that exact prompt (Stage 1 path)                     │
│  └─ NO → Continue ▼                                                    │
│                                                                         │
│      Is currentAnalysis AND currentImageData present? 🆕 v5.2          │
│      ├─ YES → buildImagePromptWithUploadedImage()                     │
│      │           (Stage 2 path - NEW FEATURE)                         │
│      └─ NO → Build generic chocolate prompt                           │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘


═══════════════════════════════════════════════════════════════════════════

Legend:
🆕 - New in v5.2
⭐ - Key new function
✓ - Checkbox/confirmation
```
