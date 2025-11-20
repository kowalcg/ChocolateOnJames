# Image Analysis Feature - Quick User Guide
## Chocolate Content Creator PRO v5.1

---

## What's New?

The image analysis feature now **actually analyzes your uploaded images** instead of giving generic responses. When you upload a dark photo, you get dark, moody prompts. When you upload a bright photo, you get bright, airy prompts.

---

## How It Works

### Step 1: Upload Your Inspiration Image
- **Click** the upload area or **drag & drop** an image
- **Paste** directly with Ctrl+V (Cmd+V on Mac)
- Supports: JPG, PNG, WebP

### Step 2: Automatic Analysis
The tool analyzes:
- ✅ **Real Colors** - Extracts actual dominant colors from your image
- ✅ **Brightness** - Detects if image is dark/normal/bright
- ✅ **Temperature** - Identifies warm/cool/neutral tones
- ✅ **Mood** - Generates descriptions matching the aesthetic

### Step 3: Get 4 Custom Prompt Variations

#### 🎯 Exact Match
Recreates the exact style of your uploaded image
- References specific brightness level
- Uses extracted color palette
- Matches detected lighting

#### ✨ Inspired
Similar feel with creative freedom
- Maintains brightness level
- Keeps color temperature
- Allows compositional variation

#### 💎 Premium
Elevated, luxury version
- Enhances detected characteristics
- Deepens dark images or brightens light ones
- Premium execution of analyzed style

#### 🍫 CHoJ Branded
Adapted for Chocolate on James
- Maintains successful aesthetic
- Incorporates brand colors
- Hamilton local character

---

## Real Examples

### Example 1: Dark, Moody Chocolate
**You Upload:** Low-lit chocolate truffle photo with dramatic shadows

**Analysis Shows:**
- Brightness: Dark (moody, dramatic lighting)
- Temperature: Warm (golden amber tones)
- Colors: #3E2723, #8B4513, #1A0F0A

**Exact Match Prompt Says:**
> "Match the dark, moody, dramatic low-key lighting with deep shadows...
> Use these exact dominant colors: #3E2723, #8B4513, #1A0F0A...
> Warm color temperature with golden amber glow..."

---

### Example 2: Bright, Clean Product Shot
**You Upload:** Bright white background with even lighting

**Analysis Shows:**
- Brightness: Bright (high-key, airy lighting)
- Temperature: Neutral (balanced)
- Colors: #F5F5DC, #D4AF37, #C8B896

**Exact Match Prompt Says:**
> "Match the bright, high-key, airy lighting with minimal shadows...
> Use these exact dominant colors: #F5F5DC, #D4AF37, #C8B896...
> Neutral color temperature with natural balance..."

---

### Example 3: Warm Golden Hour
**You Upload:** Chocolate with warm sunset lighting

**Analysis Shows:**
- Brightness: Normal (balanced)
- Temperature: Warm (golden tones)
- Colors: #D4A574, #8B6F47, #F5DEB3

**Inspired Prompt Says:**
> "Keep the normal exposure level and warm color temperature...
> Inspired by the dominant colors: #D4A574, #8B6F47, #F5DEB3...
> Maintain comfortable, welcoming, natural atmosphere..."

---

## Understanding the Analysis Display

When you upload an image, you'll see:

```
📷 Uploaded Image          |  🎨 Extracted Analysis
[Your Image Preview]       |
                           |  Brightness Level
Clear Image                |  Dark, moody, dramatic low-key lighting
                           |
                           |  Color Temperature
                           |  Warm, golden, amber tones
                           |
                           |  Style
                           |  Dramatic low-key photography...
                           |
                           |  [Color Swatches of Extracted Colors]
```

---

## How to Use the Prompts

### Option 1: Copy to Clipboard
Click **"📋 Copy"** button → Paste into your AI image generator

### Option 2: Send Directly to Generator
Click **"➡️ Use"** button → Automatically generates content with that prompt

---

## Tips for Best Results

### 1. Upload High-Quality References
- Use clear, well-composed images
- Higher resolution = better color extraction
- Avoid heavily filtered or compressed images

### 2. Match Your Desired Aesthetic
- Want dark moody photos? Upload dark reference images
- Want bright clean shots? Upload bright reference images
- The analysis will match what you upload

### 3. Try Multiple References
- Upload different images to explore styles
- Compare the generated prompts
- Mix and match elements you like

### 4. Customize After Analysis
- Use the extracted colors as a starting point
- Adjust platform/season settings below
- Regenerate with tweaked parameters

---

## Technical Notes

### Current Implementation
- **Canvas-based pixel sampling** - Analyzes actual image pixels
- **Real color extraction** - Gets dominant colors from uploaded image
- **Brightness detection** - Calculates perceived luminosity
- **Temperature analysis** - Measures warm vs cool tones

### Future Enhancement (TODO)
For production deployment, consider integrating **Claude Vision API** for:
- Detailed scene understanding ("chocolate truffle on marble")
- Composition analysis ("rule of thirds placement")
- Object recognition (props, styling elements)
- Photography technique identification
- More nuanced contextual prompts

---

## Workflow Integration

### Recommended Workflow:
1. **Find Inspiration** - Browse Instagram, Pinterest, or your own photos
2. **Upload Reference** - Drag & drop or paste into the tool
3. **Review Analysis** - Check if colors/brightness match what you see
4. **Choose Variation** - Select Exact/Inspired/Premium/CHoJ version
5. **Generate Content** - Click "Use" to create prompts + captions
6. **Create in AI Tool** - Use the generated prompt in Gemini/ChatGPT/etc.

---

## Troubleshooting

### "Colors look wrong"
- Check if image is color-corrected
- Try uploading higher resolution version
- Very dark/bright images may have limited color range

### "Analysis doesn't match"
- Image may be heavily filtered
- Try different reference image
- Manual adjustments available in controls below

### "Need different style"
- Upload different reference image
- Try the "Inspired" variation for more flexibility
- Adjust season/platform settings and regenerate

---

## Questions?

**How is this different from the old version?**
- Old: Every image got same generic "soft diffused lighting" prompt
- New: Each image analyzed to generate unique, matching prompts

**Does it work offline?**
- Yes! Analysis runs in your browser using canvas
- No external API calls for basic analysis
- Future Claude API integration would require internet

**Can I use my own photos?**
- Absolutely! Upload your existing chocolate photos
- Great for maintaining consistent style
- Reference your successful shots

**Will it work with any image?**
- Works best with chocolate/food photography
- Can analyze any image for colors/brightness
- Quality reference = quality analysis

---

**Last Updated:** November 15, 2025
**Tool Version:** v5.1 with Real Image Analysis
**Created By:** Greg Kowalczyk
