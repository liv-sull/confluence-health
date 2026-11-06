# Confluence content health dashboard

A dashboard that makes the case for cleaning up Vocus Confluence in batches. It's shown on the wiki through an iframe.

It has three tabs: **Summary** (one screen for executives), **Detail** (charts, the top 20 spaces, the Rovo tests) and **Data** (how to check every number against the raw spreadsheets).

## How it works

- `index.html` is the whole dashboard. It contains **no Vocus data**, which is why this repo can be public.
- The numbers travel in the link, after the `#`. Browsers never send that part to GitHub, so the figures are only visible to people who can see the Confluence page holding the iframe.
- Opening the page **without** the `#` part shows a link builder instead of the dashboard.

## Updating the numbers

1. Get a fresh Confluence export and rebuild **Confluence_Content_Health_Dashboard.xlsx**. Or edit its thresholds on the **Notes** tab.
2. Open the workbook in Excel and save it, so every formula has a value.
3. Go to https://liv-sull.github.io/confluence-health/ (no `#`).
4. Optional: attach the workbook to the Confluence page and paste its link into the builder. The dashboard will then link to it so readers can sort and filter every space.
5. Choose the workbook. It's read in your browser and isn't uploaded anywhere.
6. Copy the new link and paste it into the iframe macro on the Confluence page.

## Sorting and links

- Both tables on the dashboard sort when you click a column heading.
- Space names link straight to the space in Confluence.
- The workbook includes the two original spreadsheets, unchanged, on the **Raw -** tabs.
- For the full list of all spaces and every page in the top 20, use the workbook: **Space Summary**, **Top 20 batch plan** and **Top 20 pages** all have filters.

## Changing the wording

The text lives in `index.html`, inside the `render` function. Edit the file on GitHub (pencil icon), then commit. The page updates within a minute or two. The link doesn't change.

## Iframe settings

- Confluence page set to **full width**
- Width **100%**, height about **1500px**. That fits the Summary tab. The Detail tab scrolls inside the frame.
- After changing `index.html`, bump the number in the link (`?v=5` to `?v=6`). GitHub caches pages for about 10 minutes, and the new number skips the cache.

## Things to know

- "Untouched" means not edited. The export has no page views.
- The export lists who **created** each page, not who owns it. A Rovo test on 20 October 2026 showed creator and owner matched, so creator is shown as the likely owner.
- Rovo was tested for counting and finding owners and wasn't reliable at this scale. The four tests are written up on the dashboard.
