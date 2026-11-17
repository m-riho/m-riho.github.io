# ADADA 2026 poster materials

A small English-language companion to the poster by Hisashi Sato and Kunio Kondo. Visitors can read the preliminary study, find the three publisher records, and read or download the classroom questionnaire. There is no data collection, JavaScript, external font, or build step.

## Files and publishing

- `index.html`: study, participants, findings, papers and contacts.
- `questionnaire.html`: the source of truth for the English item guide.
- `questionnaire.pdf`: the same guide in print layout.
- `assets/style.css`: screen and A4 print styles. `assets/contours.svg` is a decorative mathematical illustration, not student work.
- `assets/adada2026-qr.svg` and `.png`: the same QR matrix for the poster landing page.

In the existing **m-riho/m-riho.github.io** user-site repository, put this directory at `adada2026/` on the Pages publishing branch (`master`, root). Commit only this directory. Leave the root index, Pages settings and all other pages unchanged. Do not copy reference manuscripts, notebooks, raw responses or the research project. After Pages builds, visit https://m-riho.github.io/adada2026/ and follow both questionnaire links.

## Updating content

Edit the three articles in the Related Publications section of the index. Check titles, bibliographic information and destinations against publisher records. The ADADA journal record gives 2024, 28(4), 80–86, and the JGG record includes a subtitle. These take precedence over the shorter or older citations on the project brief.

Edit the numbered items in the questionnaire HTML. Keep the English question, response format, source locator, and any CT label distinct. JGG §§5.1–5.4 supply Q1–Q6 and Q15–Q17. For Q7–Q14 and Q18 the exact wording is from the supplied JIP manuscript, Appendix A.1; JGG documents the CT mapping (Table 2) and autumn-only administration of Q18 (§4). Do not describe the wording of these nine items as a verbatim JGG transcript. JIP lists an extra Q4 option; the page distinguishes it from the four JGG options. The five-point endpoints and neutral midpoint are documented; the intermediate labels are explanatory. Do not substitute themes, responses or results for questions.

## Regenerating the PDF

Open the local questionnaire HTML in Chrome or Chromium, print, and choose **Save as PDF**, A4, portrait, scale 100%, with browser headers/footers off. Print CSS hides navigation/download links and groups the sections into three pages. For a headless equivalent, from this directory:

```sh
chromium --headless --no-pdf-header-footer --print-to-pdf="$PWD/questionnaire.pdf" "file://$PWD/questionnaire.html"
```

Use your installed Chrome executable in place of `chromium`. Check that the PDF contains Q1–Q18 in order, the response formats, Q4 choices and variant, Q18 semester note, scale and both citations.

## Regenerating and placing the QR code

The research checkout includes `poster/github-pages/generate_qr.py`. With Python, ReportLab and Pillow installed, run `python3 poster/github-pages/generate_qr.py` from the project root. Both assets encode **https://m-riho.github.io/adada2026/** with error correction Q and a four-module white border. To regenerate outside the research checkout, use a QR encoder with the same URL, error correction Q, white background and four-module margin. Do not encode the questionnaire URL.

Copy the PNG to `poster/adada2026-poster/figures/adada2026-qr.png`. The existing footer in `main.tex` places it at 38 mm alongside the label “Related Publications & Full Questionnaire” and a readable URL. Run `make -C poster/adada2026-poster`. Check the one-page A0 output, scan the code, and verify the landing page before printing. If distributing the poster source ZIP, refresh the edited files and include the QR image.
