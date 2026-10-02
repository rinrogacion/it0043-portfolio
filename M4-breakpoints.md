# M4: Content-based breakpoint observations

## Method

I tested the page in the browser at 320, 360, 400, 480, 540, 600, 700, 768, 800, 900, 1024, 1200, and 1440 CSS pixels wide. I inspected element bounds, grid track counts, text fit, and document width. No CSS was changed during this final verification pass.

The browser reported no horizontal document overflow at any tested width. The document's reported scroll width was 15 CSS pixels less than `innerWidth` in this environment, consistent across the measurements; it was not evidence of horizontal overflow.

## Navigation

- The title and links use one row at widths of 600px and above. Below 600px, the title and links occupy separate rows.
- The combined title and navigation links need approximately 452px of content width. The nav's 8% horizontal padding means this fits in one row at approximately 553px viewport width.
- A forced one-row measurement showed the available nav content width was about 441px at 540px, too small for the combined content, and about 458px at 560px, enough to fit.
- With the actual CSS, all four links fit on one line starting at 360px, but the title remains on a separate row until the existing 600px breakpoint. At 320px the links themselves wrap to a second line.

**Breakpoint observation:** the content can fit the title and links on one row at roughly 560px. The current 600px breakpoint is close to that observed threshold and intentionally keeps the mobile nav stacked below it.

## Skills

- The current layout uses one column below 600px and two columns at 600px and above.
- At 320px, each one-column skill card is about 256px wide and all labels fit.
- At 600px, the two-column cards are about 236px wide; at 768px they are about 306px wide.
- A supplementary measurement forcing four columns showed that the four-card layout could not fit its intrinsic card widths around 700px, while all four cards fit at 768px (about 143px per card). The longest label, “JavaScript,” needs about 75px of text width before padding.

**Breakpoint observation:** 600px is where the current two-column layout begins. A four-column alternative would need roughly 768px in these measurements to fit all four cards without intrinsic-width pressure. The chosen narrow-screen one-column layout prioritizes label readability over showing more cards in each row.

## Projects

- Below 600px, cards use one column and the grid fits its content area.
- At 600px, the three-column cards are about 150px wide, leaving about 90px for text after the cards' 30px padding on both sides.
- At 768px, the cards are about 197px wide, leaving about 137px for text.
- At 800px, the cards are about 206px wide, leaving about 146px for text.
- At 900px, the cards are about 234px wide, leaving about 174px for text.

**Breakpoint observation:** three columns work structurally at 600px without horizontal overflow, but the available text area is constrained. The measurements suggest that card content becomes more comfortable around 850–900px. This was recorded as a design consideration, not changed during final verification.

## Verified widths

| Width | Navigation | Skills | Projects | About and Contact text | Horizontal overflow |
|---:|---|---|---|---|---|
| 320px | Links wrap and remain visible | One column | One column | Contained | None |
| 360px | Links fit on one line; title above | One column | One column | Contained | None |
| 400px | Links fit on one line; title above | One column | One column | Contained | None |
| 480px | Links fit on one line; title above | One column | One column | Contained | None |
| 540px | Links fit on one line; title above | One column | One column | Contained | None |
| 600px | Title and links share a row | Two columns | Three columns | Contained | None |
| 700px | Title and links share a row | Two columns | Three columns | Contained | None |
| 768px | Title and links share a row | Two columns | Three columns | Contained | None |
| 800px | Title and links share a row | Two columns | Three columns | Contained | None |
| 900px | Title and links share a row | Two columns | Three columns | Contained | None |
| 1024px | Title and links share a row | Two columns | Three columns | Contained | None |
| 1200px | Title and links share a row | Two columns | Three columns | Contained | None |
| 1440px | Title and links share a row | Two columns | Three columns | Contained | None |

## Report 06 decision

The Skills grid remains two columns at 1440px, but its two tracks span the available content width. The report's two-column observation was reproduced; the claim that substantial horizontal space was left unused beside the grid was not supported. I rejected it as a defect and made no change.