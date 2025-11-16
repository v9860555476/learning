# Ekaxa Calculator Page Development Prompt

**Generated:** November 15, 2025  
**Source:** Ekaxa Master Prompt V3.0  
**Platform:** Lovable (Frontend) + Supabase (Backend)  
**Prompt Type:** Web Page Development

---

## Critical Requirements

**Platform:** Lovable  
**Design:** Clean, functional Apple-style interface  
**Primary Color:** Teal (#14B8A6)  
**Access Control:** Tier-based (Guest: 3 uses, Free: unlimited, Premium/Platinum: unlimited + features)  
**Authentication:** Required for saving results, optional for basic use

---

## Page Specifications

**URL:** `/calculator`

**Layout:** Single column on mobile, two-column on desktop with calculator on the left occupying sixty percent width and results on the right occupying forty percent width.

**Typography:** Use Inter font throughout for consistency and readability. Page heading should be 48 pixels in Clash Display. Input labels should be 14 pixels semi-bold. Error messages should be 12 pixels in coral color (#FF6B6B). Results should use a mix of 16 pixels body text and 24 pixels for key numbers.

---

## Tab System

### Tab Navigation

Display a horizontal tab bar at the top of the calculator with six tabs: Life Path Number, Destiny Number, Soul Urge Number, Personality Number, Compatibility (with a gold "Premium" badge), and Yearly Forecast (with a gold "Premium" badge).

Active tabs should have a teal bottom border measuring 4 pixels thick and teal text. Inactive tabs should have gray text. For Premium-only tabs, if a Free or Guest user clicks them, display a modal explaining the feature requires Premium or Platinum tier with upgrade call-to-action buttons.

### Tab Content Structure

Each tab should contain: a description section explaining what this number reveals with two to three sentences in gray text, an input form with clearly labeled fields, a calculate button in teal, and a results section that appears below after calculation.

---

## Life Path Number Tab

### Input Fields

Display three date input fields arranged horizontally: Month (dropdown with January through December), Day (number input accepting values 1 through 31), and Year (number input accepting values 1900 through 2025). Add clear labels above each field and use placeholder text like "Select month," "Enter day," and "Enter year."

Below the date inputs, include an optional full name field (text input) with helper text that states "Optional: For enhanced interpretation." Add an optional birth time field (time picker) with helper text "Optional: For precise calculations."

### Calculate Button

Style as a prominent teal button using #14B8A6 with white text reading "Calculate My Life Path." The button should be disabled and grayed out until valid date inputs are provided. Add a subtle loading spinner inside the button when processing.

### Results Display

After calculation, display a card with cream background using #F9F7F4 showing: the Life Path Number as a large number measuring 72 pixels in teal color centered at the top, a heading "Your Life Path Number: X" in 28 pixels, a detailed interpretation paragraph with eight to ten sentences explaining the meaning, key traits section with four to five bullet points, strengths and challenges sections with three to four points each, and compatible numbers section.

For Free users, include a call-to-action box at the bottom: "Want to save this reading? Sign up for free!" with a teal button.

For authenticated Free users, add a "Save This Reading" button that stores the result in Supabase. Display remaining saves count showing X out of 50 remaining.

For Premium and Platinum users, add both "Save Reading" and "Download PDF" buttons. The download button should generate a professionally formatted PDF report.

---

## Destiny Number Tab

### Input Fields

Display a single full name input field with label "Enter Your Full Birth Name." Include helper text below: "Use the name exactly as it appears on your birth certificate." Add a checkbox option: "Include middle name(s)" that expands additional input fields if checked.

### Calculation Method

Use the Pythagorean numerology system where A equals 1, B equals 2, and continues through Z equals 26. Calculate by summing all letter values and reducing to a single digit, except for master numbers 11, 22, and 33 which should not be reduced.

### Results Display

Show the Destiny Number prominently at 72 pixels in teal, followed by the name breakdown showing each letter's numeric value in a table format. Display interpretation sections covering: life purpose and calling presented as a paragraph, career guidance with four to five points, relationship patterns with three to four points, and spiritual path presented as a paragraph.

---

## Soul Urge Number Tab

### Input Fields

Full name input with separate fields for first name, middle name (optional), and last name. Include helper text: "We'll calculate using only the vowels in your name."

### Calculation Method

Extract vowels (A, E, I, O, U) from the full name and calculate their numeric sum using the Pythagorean system. Reduce the sum to a single digit except for master numbers.

### Results Display

Display Soul Urge Number, interpretation focusing on inner desires and motivations with eight to ten sentences, what drives you section with four to five points, emotional needs with three to four points, and hidden talents with three to four points.

---

## Personality Number Tab

### Input Fields

Same as Soul Urge tab with full name inputs including first name, middle name (optional), and last name fields.

### Calculation Method

Extract consonants from the full name and calculate their numeric sum using the Pythagorean system. Reduce to single digit except for master numbers.

### Results Display

Display Personality Number, interpretation of outward persona with eight to ten sentences, how others see you with four to five points, first impression traits with three to four points, and public versus private self comparison section.

---

## Compatibility Tab (Premium/Platinum Only)

### Access Control

Check user tier on tab click. If Guest or Free tier, display a modal with: heading "Unlock Compatibility Readings," description of what compatibility analysis reveals, comparison table showing Free versus Premium features, and call-to-action buttons showing "Upgrade to Premium $29/month" in teal and "See All Features" as secondary button.

### Input Fields (for authorized users)

Display two sets of inputs side by side: Person A with fields for your date of birth and name, and Person B with fields for partner's date of birth and name. Include optional field for relationship type dropdown offering Romantic, Business, Friendship, and Family options.

### Results Display

Show compatibility percentage as a large circular progress indicator showing 0 to 100 percent with color coding: 80 to 100 percent displayed in green, 60 to 79 percent displayed in teal, 40 to 59 percent displayed in gold, and below 40 percent displayed in coral. Display detailed compatibility analysis covering: overall harmony score, strengths of the partnership with four to five points, potential challenges with three to four points, communication style compatibility, life path alignment, and recommendations for growth.

---

## Yearly Forecast Tab (Premium/Platinum Only)

### Access Control

Same tier checking as Compatibility tab. Display upgrade modal for unauthorized users using the same format.

### Input Fields (for authorized users)

Display date of birth field and year to forecast dropdown showing current year, next year, and following year options.

### Results Display

Show the Personal Year Number prominently. Display month-by-month forecast in an accordion format where each month can be expanded to show: themes and focus areas, opportunities to watch for, challenges to navigate, and lucky dates.

---

## Guest User Limitations

### Usage Tracking

For unauthenticated users, track calculator uses in session storage. After each calculation, increment the counter. When count reaches 3, display a full-screen modal that cannot be dismissed with: compelling headline "Unlock Unlimited Calculations," explanation of Free tier benefits, two OAuth buttons for Sign in with Google and Sign in with Facebook, and small text "It's free forever, no credit card needed."

### Visual Indicators

Display a usage counter at the top of the page for Guest users showing "2 calculations remaining" in a small teal badge. The badge should update after each calculation.

---

## Authenticated User Features

### Save Functionality

After each calculation for Free tier users, display a "Save This Reading" button. On click, save to Supabase calculations table with fields: user ID, calculation type, input data stored as JSON, result data stored as JSON, and created timestamp.

Show success message: "Reading saved to your dashboard!" Track save count and display remaining slots for Free users with maximum 50 saved calculations.

### My Saved Readings Sidebar

For authenticated users, display a collapsible sidebar on the right showing recent saved calculations with the last 5 entries. Each entry should show: calculation type icon, brief title such as "Life Path: 7," date saved, and quick view button. Clicking quick view loads the full result without recalculation.

---

## Calculation Logic Implementation

### Pythagorean System

Create a mapping object where A through I equals 1 through 9, J through R equals 1 through 9, and S through Z equals 1 through 8. Implement reduce function that sums digits until a single digit remains, with exception handling for master numbers 11, 22, and 33 which should not be reduced further.

### Date Calculations

For Life Path Number, reduce month, day, and year separately, then sum and reduce the total. For example: Birth date March 15, 1985 becomes 3 plus 6 (from 1+5) plus 5 (from 1+9+8+5=23, then 2+3=5) equals 14, then 1+4 equals 5.

### Name Calculations

Convert all letters to uppercase, remove spaces and special characters. For Destiny Number, sum all letters. For Soul Urge, extract only vowels A, E, I, O, U. For Personality Number, extract only consonants. Apply reduction rules to all calculations.

---

## Supabase Integration

### Calculations Table Structure

Query and insert to calculations table with columns: id as UUID, user ID as foreign key to auth users, calculation type as enum accepting life path, destiny, soul urge, personality, compatibility, yearly forecast, input data as JSONB storing form values, result number as integer, result interpretation as text, created at as timestamp, updated at as timestamp.

### Row Level Security

Users can only read their own calculations where user ID equals authenticated user ID. Users can insert calculations only when authenticated. Admins can read all calculations.

### Save Operation

On save button click, validate user is authenticated and check tier limitations where Free tier has maximum 50 saves. Execute Supabase insert with input data, result data, and calculation type. Update local state to reflect saved status. Show success toast notification.

### Load Saved Readings

On page load for authenticated users, query calculations table where user ID equals current user, ordered by created at descending, limit 50 for Free tier or unlimited for Premium and Platinum. Display in sidebar with most recent first.

---

## PDF Generation (Premium/Platinum Only)

### Report Format

Generate PDF using library like jsPDF or react-pdf with Ekaxa branding including logo and colors. Include sections: cover page with user name and calculation type, input summary, prominent number display, detailed interpretation, charts or graphics for visual appeal, and footer with "Generated by Ekaxa - Embrace Grace" and generation date.

### Styling

Use teal and gold color scheme matching the website. Include page numbers, professional typography using Inter font, generous white space, and high-quality graphics.

---

## Responsive Design

### Mobile (375px)

Stack all form fields vertically with full width. Move results below inputs with no side-by-side layout. Collapse the saved readings sidebar into a "View Saved" button at the bottom. Use full-screen modals for premium upgrade prompts. Ensure all touch targets are minimum 44 by 44 pixels.

### Tablet (768px)

Allow two-column layout for comparison inputs showing Person A and Person B side by side. Keep results below inputs. Display saved readings as a bottom drawer that slides up.

### Desktop (1280px)

Use side-by-side layout with calculator form on left occupying 60 percent width and results on right occupying 40 percent width. Display saved readings sidebar on the far right as a toggleable panel. Keep all controls and results visible simultaneously to minimize scrolling.

---

## Testing Checklist

Verify all six tabs are visible and clickable. Confirm Premium tabs show upgrade modal for Guest and Free users. Test all calculation logic with known numerology examples. Verify Guest user counter increments correctly and blocks at 3 uses. Test save functionality for Free users respects 50 calculation limit. Confirm Premium users can download PDF reports. Test all form validations for required fields, date ranges, and name format. Verify responsive layouts at all breakpoints. Test saved readings sidebar displays correctly. Confirm accessibility with keyboard navigation. Verify all Supabase queries work with proper RLS policies.

---

## Code Examples

### Pythagorean System Implementation

```javascript
const letterValues = {
  A: 1, B: 2, C: 3, D: 4, E: 5, F: 6, G: 7, H: 8, I: 9,
  J: 1, K: 2, L: 3, M: 4, N: 5, O: 6, P: 7, Q: 8, R: 9,
  S: 1, T: 2, U: 3, V: 4, W: 5, X: 6, Y: 7, Z: 8
}

function reduceToSingleDigit(num) {
  // Exception: master numbers 11, 22, 33
  if (num === 11 || num === 22 || num === 33) return num
  
  while (num > 9) {
    num = num.toString().split('').reduce((sum, digit) => sum + parseInt(digit), 0)
  }
  return num
}
```

### Guest Usage Tracking

```javascript
// sessionStorage tracking
let uses = parseInt(sessionStorage.getItem('guest_calculator_uses') || '0')
uses++
sessionStorage.setItem('guest_calculator_uses', uses.toString())

if (uses >= 3) {
  // Show full-screen modal (cannot dismiss)
  setShowUpgradeModal(true)
}
```

### Save Calculation to Supabase

```javascript
const { error } = await supabase
  .from('calculations')
  .insert({
    user_id: session.user.id,
    calculation_type: 'life_path',
    input_data: { date_of_birth, name },
    result_number: lifePathNumber,
    result_data: { interpretation, traits },
    is_saved: true
  })

// Check tier limits
const { count } = await supabase
  .from('calculations')
  .select('*', { count: 'exact', head: true })
  .eq('user_id', session.user.id)
  .eq('is_saved', true)

// Free tier: max 50 saves
if (tier === 'Free' && count >= 50) {
  alert('You've reached your save limit. Upgrade to Premium for unlimited saves.')
}
```

---

## End of Prompt

This prompt provides complete specifications for building the Ekaxa calculator page using the Lovable platform with Supabase backend integration. All calculations follow authentic Pythagorean numerology principles with proper tier-based access control and OAuth authentication requirements.
