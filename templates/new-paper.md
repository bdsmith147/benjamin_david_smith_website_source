---
# ============================================================================
# NEW PAPER TEMPLATE
# 1. Create a new folder in content/publication/ named like:  smith-2027-short-title
#    (lowercase, hyphens, no spaces). This becomes the permanent web address:
#    /works/smith-2027-short-title/  — never rename the folder after publishing.
# 2. Inside that folder, create a file named  index.md  and paste this whole file in.
# 3. Fill in the values below. Lines starting with # are notes and can be deleted.
# 4. Keep the quotation marks and the two-space indentation exactly as shown.
# ============================================================================

title: "Full title of the paper"
date: 2027-03-15                      # publication date: YYYY-MM-DD (no quotes). A date in the FUTURE
                                      # hides the page until that day: use today or earlier.

# Authors in order, spelled exactly as in the paper. Your name must be written
# "Benjamin D. Smith" so it shows in bold. New co-authors appear on the People page
# automatically; add their link and position in data/coauthors.yaml.
authors: ["Benjamin D. Smith", "First Co-Author", "Second Co-Author"]

# Which tab on the Works page it appears under. Use ONE of:
#   ["journal_article"]  published, peer-reviewed article  -> Articles tab
#   ["preprint"]         submitted / arXiv only            -> Submitted tab
#   ["thesis"]           thesis or dissertation            -> Theses tab
publication_types: ["journal_article"]

publication: "Journal Name 12, 345678"   # venue line shown in the citation (no year)
journal: "Journal Name"                  # journal name only (used by Google Scholar)
doi: "10.xxxx/xxxxxx"                    # DOI without https://doi.org/ ; delete line if none
# status: "Submitted"                    # optional label for preprints; remove the # to use

abstract: "Paste the abstract here, all on one line. If it contains a double quote character, write it as \" instead."

# Buttons shown on the paper's page. Add or delete entries; keep the indentation.
# For a PDF you host yourself: upload it to static/files/ and use  url: "files/your-file.pdf"
# (no slash at the start).
links:
  - name: Publisher's Version
    url: "https://doi.org/10.xxxx/xxxxxx"
  - name: arXiv
    url: "https://arxiv.org/abs/xxxx.xxxxx"

# Optional keywords (lowercase). Used for site search and tag pages.
tags: ["quantum sensing", "atom interferometry"]
---
Optional: any extra text below the line above appears on the paper's page under the abstract,
for example "Supervised by Professor ...". Delete this paragraph if you don't need it.
