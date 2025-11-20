# Business Configuration Templates
## TapeGeeks & Brontë Harbour Classic

**Pre-configured business settings ready to copy & paste**

---

## Configuration 1: TapeGeeks (Kinesiology Tape Products)

### Complete businessConfig Object

```javascript
const businessConfig_TapeGeeks = {
    // BRAND IDENTITY
    brandName: "TapeGeeks",
    industry: "Sports Medicine & Athletic Performance",
    contentType: "athletic product photography",
    productType: "kinesiology tape, nasal strips, and performance products",
    brandValues: "athletic performance, injury prevention, professional quality, scientific backing",
    brandPromise: "Photography must emphasize product quality, athletic performance benefits, and professional-grade reliability.",

    // MARKETING CHANNELS
    marketingChannels: "Instagram, Facebook, Amazon product pages, B2B medical suppliers, sports medicine catalogs",
    platforms: "e-commerce product pages and social media marketing",

    // PRODUCT CATEGORIES
    categories: {
        'kinesiology-tape': {
            name: 'Kinesiology Tape',
            description: 'Professional athletic tape for muscle support and injury prevention',
            keywords: 'muscle support, flexibility, athletic performance, injury prevention, sports medicine',
            visualFocus: 'Show tape application on muscles, flexibility in motion, professional athletic use'
        },
        'nasal-strips': {
            name: 'Nasal Strips',
            description: 'Breathing enhancement strips for athletic performance',
            keywords: 'breathing, airflow, performance enhancement, endurance, oxygen intake',
            visualFocus: 'Show athletes wearing strips during activity, improved breathing, performance boost'
        },
        'compression-gear': {
            name: 'Compression Products',
            description: 'Compression sleeves and gear for recovery and performance',
            keywords: 'recovery, circulation, endurance, muscle support, post-workout',
            visualFocus: 'Show compression on limbs, active recovery, athletic training'
        },
        'athletic-accessories': {
            name: 'Athletic Accessories',
            description: 'Professional sports medicine and performance accessories',
            keywords: 'versatility, quality, professional-grade, training tools, sports medicine',
            visualFocus: 'Show products in use, professional athletic setting, quality materials'
        }
    },

    // TARGET AUDIENCES
    audiences: {
        'professional-athletes': {
            name: 'Professional Athletes',
            description: 'Elite athletes and competitive sports professionals',
            messaging: 'Emphasize performance gains, competitive edge, professional-grade quality, tour-level standards',
            painPoints: 'Need reliable performance, injury prevention, quick recovery, professional results',
            visuals: 'High-intensity action, elite performance, professional sports settings'
        },
        'sports-medicine-professionals': {
            name: 'Sports Medicine Professionals',
            description: 'Physical therapists, athletic trainers, sports doctors',
            messaging: 'Focus on scientific backing, clinical results, professional recommendations, patient outcomes',
            painPoints: 'Need evidence-based products, consistent quality, trusted by professionals',
            visuals: 'Clinical settings, professional application, medical credibility'
        },
        'fitness-enthusiasts': {
            name: 'Fitness Enthusiasts',
            description: 'Regular gym-goers, CrossFit, recreational athletes',
            messaging: 'Highlight versatility, ease of use, workout enhancement, injury prevention',
            painPoints: 'Want to train harder safely, prevent injuries, improve performance',
            visuals: 'Gym settings, CrossFit boxes, active training, diverse exercises'
        },
        'runners': {
            name: 'Runners',
            description: 'Marathon runners, trail runners, recreational joggers',
            messaging: 'Emphasize endurance support, joint protection, breathing improvement, long-distance benefits',
            painPoints: 'Knee/joint pain, breathing efficiency, muscle fatigue, distance performance',
            visuals: 'Running action, outdoor trails, marathon settings, endurance focus'
        },
        'coaches-trainers': {
            name: 'Coaches & Trainers',
            description: 'Athletic coaches, personal trainers, strength coaches',
            messaging: 'Focus on client results, professional recommendations, bulk/team pricing, proven effectiveness',
            painPoints: 'Need reliable products to recommend, client safety, performance results',
            visuals: 'Coaching scenarios, team settings, professional instruction'
        }
    },

    // SEASONAL / PROMOTIONAL PERIODS
    seasons: {
        'spring-training': {
            name: 'Spring Training Season',
            dates: 'March - May',
            description: 'Athletes preparing for summer competitions',
            messaging: 'Get ready for competition season, build strength safely, prevent early-season injuries',
            visuals: 'Outdoor training, fresh starts, building intensity, preparation mode'
        },
        'marathon-season': {
            name: 'Marathon Season',
            dates: 'September - November',
            description: 'Peak marathon and endurance race season',
            messaging: 'Go the distance, support your training, prevent overuse injuries, optimize breathing',
            visuals: 'Long-distance running, endurance focus, race-day preparation'
        },
        'new-year-fitness': {
            name: 'New Year Fitness Goals',
            dates: 'January - February',
            description: 'Resolution season, new fitness commitments',
            messaging: 'Start strong, train safely, build healthy habits, prevent beginner injuries',
            visuals: 'Fresh starts, goal-setting, beginner-friendly, motivation'
        },
        'back-to-school-sports': {
            name: 'Back to School Sports',
            dates: 'August - September',
            description: 'Youth sports season, school athletics',
            messaging: 'Keep young athletes safe, support growing bodies, prevent sports injuries',
            visuals: 'Youth sports, school athletics, team settings, parent appeal'
        },
        'year-round': {
            name: 'Year-Round Performance',
            dates: 'Ongoing',
            description: 'Continuous training and performance',
            messaging: 'Consistent performance, always ready, professional-grade quality',
            visuals: 'Timeless athletic imagery, professional quality, versatile use'
        }
    },

    // BRAND VOICE & TONE
    tone: {
        primary: 'Professional and science-backed',
        secondary: 'Athletic and performance-driven',
        avoid: 'Casual slang, unproven claims, amateur presentation'
    },

    // COLOR PALETTE
    brandColors: {
        primary: '#1976D2',      // Professional Blue
        secondary: '#F57C00',    // Energy Orange
        accent: '#00C853',       // Performance Green
        neutral: '#455A64'       // Professional Gray
    },

    // CALL TO ACTION
    cta: {
        primary: 'Enhance Your Performance',
        secondary: 'Shop Professional-Grade Tape',
        tertiary: 'Join Elite Athletes'
    }
};
```

---

## Configuration 2: Brontë Harbour Classic (Father's Day Race)

### Complete businessConfig Object

```javascript
const businessConfig_BronteHarbour = {
    // BRAND IDENTITY
    brandName: "Brontë Harbour Classic",
    industry: "Community Running Events & Health Promotion",
    contentType: "running race event photography",
    productType: "scenic waterfront Father's Day race experience",
    brandValues: "family celebration, community health, scenic beauty, Father's Day tradition, active lifestyle",
    brandPromise: "Photography must capture the scenic waterfront beauty, family-friendly atmosphere, and Father's Day celebration spirit.",

    // MARKETING CHANNELS
    marketingChannels: "Facebook Ads, Instagram, local community boards, running club newsletters, Hamilton media, event listing sites",
    platforms: "event registration, community engagement, and social media promotion",

    // EVENT CATEGORIES / CONTENT TYPES
    categories: {
        'race-day-experience': {
            name: 'Race Day Experience',
            description: 'The scenic waterfront race atmosphere and community celebration',
            keywords: 'scenic course, waterfront running, community atmosphere, race day energy, Hamilton lakefront',
            visualFocus: 'Show beautiful Brontë Harbour waterfront, runners on scenic course, community celebration'
        },
        'fathers-day-celebration': {
            name: 'Father\'s Day Celebration',
            description: 'Special Father\'s Day family activity and celebration',
            keywords: 'Father\'s Day, family activity, dad and kids, healthy celebration, family tradition',
            visualFocus: 'Show fathers running with families, post-race celebration, Father\'s Day festivities'
        },
        'training-preparation': {
            name: 'Training & Preparation',
            description: 'Getting ready for the race, course preview, training tips',
            keywords: 'race preparation, training runs, course familiarity, fitness goals, race readiness',
            visualFocus: 'Show training runs, course preview, preparation activities, goal-setting'
        },
        'registration-promotion': {
            name: 'Registration Promotion',
            description: 'Race registration, early bird pricing, group discounts',
            keywords: 'register now, early bird, group discount, save your spot, limited spots',
            visualFocus: 'Show registration details, pricing benefits, countdown to race day'
        },
        'community-impact': {
            name: 'Community Health Impact',
            description: 'Promoting community health, active lifestyle, Hamilton pride',
            keywords: 'community health, active Hamilton, local pride, neighborhood event, healthy lifestyle',
            visualFocus: 'Show local community, Hamilton pride, neighborhoods, health focus'
        }
    },

    // TARGET AUDIENCES
    audiences: {
        'fathers': {
            name: 'Fathers',
            description: 'Dads looking for meaningful Father\'s Day activity',
            messaging: 'Create a Father\'s Day memory, healthy celebration, accomplish something special, family time',
            painPoints: 'Want meaningful activity, not just another gift, quality time with family, personal achievement',
            visuals: 'Dads running, fathers with kids, post-race celebration with family, proud moments'
        },
        'families': {
            name: 'Families',
            description: 'Families planning Father\'s Day celebration',
            messaging: 'Celebrate Dad together, healthy family activity, create traditions, support Dad\'s goals',
            painPoints: 'Want special Father\'s Day plan, include whole family, healthy activity, memorable experience',
            visuals: 'Families cheering, kids at finish line, family photos, celebration together'
        },
        'local-runners': {
            name: 'Hamilton Area Runners',
            description: 'Local running community and running club members',
            messaging: 'Scenic local race, beautiful Brontë Harbour course, support local events, Hamilton pride',
            painPoints: 'Want quality local races, convenient location, scenic courses, community connection',
            visuals: 'Familiar Hamilton locations, local landmarks, running community, neighborhood pride'
        },
        'first-time-racers': {
            name: 'First-Time Race Participants',
            description: 'People who\'ve never run a race before',
            messaging: 'Perfect first race, supportive atmosphere, achievable distance, you can do this',
            painPoints: 'Nervous about first race, want welcoming environment, achievable goals, not intimidating',
            visuals: 'Supportive atmosphere, diverse participants, achievable distances, encouraging vibe'
        },
        'serious-runners': {
            name: 'Competitive Runners',
            description: 'Runners seeking race times, PRs, competition',
            messaging: 'Fast flat course, chip timing, age group awards, competitive field, scenic fast route',
            painPoints: 'Want quality timing, competitive field, fast course, accurate results, recognition',
            visuals: 'Competitive racing, finish line clocks, race times, athletic performance'
        },
        'health-conscious-community': {
            name: 'Health-Conscious Community',
            description: 'People prioritizing active lifestyle and wellness',
            messaging: 'Community health event, active lifestyle, wellness celebration, Hamilton\'s healthy community',
            painPoints: 'Want community connection, healthy activities, local wellness events, active lifestyle',
            visuals: 'Community health, active lifestyle, wellness focus, neighborhood vitality'
        }
    },

    // SEASONAL / PROMOTIONAL PERIODS
    seasons: {
        'fathers-day-weekend': {
            name: 'Father\'s Day Weekend',
            dates: 'June (specific date varies)',
            description: 'The race day itself - Father\'s Day celebration',
            messaging: 'Celebrate Dad this Father\'s Day, meaningful Father\'s Day activity, special day for fathers',
            visuals: 'Father\'s Day elements, families celebrating dads, special recognition of fathers'
        },
        'early-bird-registration': {
            name: 'Early Bird Registration',
            dates: 'February - March',
            description: 'Discounted early registration period',
            messaging: 'Save money, secure your spot, best pricing, plan ahead, early commitment',
            visuals: 'Registration prompts, savings graphics, calendar countdown, planning imagery'
        },
        'spring-training-season': {
            name: 'Spring Training Season',
            dates: 'April - May',
            description: 'Pre-race training period',
            messaging: 'Train for June race, get ready for Father\'s Day, build your fitness, countdown to race day',
            visuals: 'Spring running, outdoor training, preparation, building fitness, training groups'
        },
        'last-chance-registration': {
            name: 'Final Registration Push',
            dates: 'May (2-3 weeks before race)',
            description: 'Final opportunity to register',
            messaging: 'Last chance to register, spots filling up, don\'t miss out, register this week',
            visuals: 'Urgency, limited availability, final call, countdown graphics'
        },
        'race-week': {
            name: 'Race Week',
            dates: 'Week of June race',
            description: 'Final race preparation and excitement',
            messaging: 'See you Sunday, final preparations, weather forecast, what to bring, you\'re ready',
            visuals: 'Excitement building, preparation tips, course reminders, anticipation'
        }
    },

    // BRAND VOICE & TONE
    tone: {
        primary: 'Community-focused and celebratory',
        secondary: 'Family-friendly and encouraging',
        tertiary: 'Proud of Hamilton and local beauty',
        avoid: 'Elitist language, intimidating messaging, overly competitive tone'
    },

    // COLOR PALETTE
    brandColors: {
        primary: '#1976D2',      // Water Blue (Harbour)
        secondary: '#4CAF50',    // Nature Green (Waterfront)
        accent: '#FF6F00',       // Sunrise Orange (Morning race)
        neutral: '#607D8B'       // Coastal Gray
    },

    // LOCATION EMPHASIS
    locationDetails: {
        venue: 'Brontë Harbour, Hamilton',
        scenicElements: 'Waterfront path, lake views, harbour beauty, peaceful water, scenic route',
        localPride: 'Hamilton\'s beautiful waterfront, local treasure, community gathering place',
        landmarks: 'Brontë Harbour, lakefront trail, waterfront park'
    },

    // DISTANCE OPTIONS
    raceDistances: {
        '5k': 'Perfect first race or family-friendly distance',
        '10k': 'Classic distance for runners of all levels',
        '1k-kids': 'Kids race - get the whole family involved'
    },

    // CALL TO ACTION
    cta: {
        primary: 'Register for Father\'s Day Race',
        secondary: 'Celebrate Dad with a Run',
        tertiary: 'Join Hamilton\'s Waterfront Classic'
    }
};
```

---

## Usage Instructions

### For TapeGeeks Implementation:

```javascript
// 1. Copy businessConfig_TapeGeeks object into your file

// 2. Use in prompt variations
function generatePromptVariations(analysis) {
    const config = businessConfig_TapeGeeks;
    // ... use config.brandName, config.categories, etc.
}

// 3. Use in comprehensive generation
function buildImagePromptWithUploadedImage(options, analysis) {
    const config = businessConfig_TapeGeeks;
    // ... use config.brandValues, config.audiences, etc.
}
```

### For Brontë Harbour Implementation:

```javascript
// 1. Copy businessConfig_BronteHarbour object into your file

// 2. Use in prompt variations
function generatePromptVariations(analysis) {
    const config = businessConfig_BronteHarbour;
    // ... use config.brandName, config.categories, etc.
}

// 3. Use in comprehensive generation
function buildImagePromptWithUploadedImage(options, analysis) {
    const config = businessConfig_BronteHarbour;
    // ... use config.locationDetails, config.raceDistances, etc.
}
```

---

## Quick Comparison

| Element | TapeGeeks | Brontë Harbour |
|---------|-----------|----------------|
| **Industry** | Sports Medicine Products | Community Running Events |
| **Content Type** | Product photography | Event photography |
| **Primary Audience** | Athletes, Sports Medicine Pros | Fathers, Families, Local Runners |
| **Tone** | Professional, Science-backed | Community-focused, Celebratory |
| **Visual Style** | Clean product shots, action use | Scenic waterfront, community atmosphere |
| **Key Season** | Marathon season, Spring training | Father's Day weekend, Spring registration |
| **CTA Focus** | Enhance performance, Professional-grade | Celebrate Dad, Join the race |

---

## Testing Scenarios

### TapeGeeks Test Images

**Test 1:** Blue kinesiology tape roll on white background
- Expected: Professional, clean, e-commerce ready prompts

**Test 2:** Athlete applying tape to knee
- Expected: Action-oriented, performance-focused prompts

**Test 3:** Nasal strip product shot
- Expected: Breathing enhancement, athletic performance messaging

### Brontë Harbour Test Images

**Test 1:** Runners on waterfront path with lake view
- Expected: Scenic, community-focused, waterfront beauty prompts

**Test 2:** Father and child at race finish line
- Expected: Father's Day celebration, family-friendly prompts

**Test 3:** Large group of runners at starting line
- Expected: Community event, energetic, inclusive prompts

---

**Both configurations are complete and ready to implement!**
