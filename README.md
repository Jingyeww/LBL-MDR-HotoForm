# Handover & Takeover (HOTO) Form

A single-page form for recording the condition and contents of a customer's 3D
printer when Layer by Layer takes it in, and again when it goes back.

Fill it in on screen, have the customer sign on the device, then print or save as
PDF. Everything is in one HTML file — no install, no server, no dependencies.

## Running it

Open `index.html` in any browser. That's the whole setup.

To use it on a phone or tablet, publish the file with GitHub Pages (Settings →
Pages → Deploy from a branch → main → / (root)), open the resulting URL, then use
"Add to Home Screen" so it opens fullscreen like an app. A tablet is the better
device here — the signature box is easier to sign on.

## What it records

- **Parties** — customer name and contact, plus the Layer by Layer representative
  receiving the printer.
- **Printer details** — brand, then a model list that appears for that brand.
  Bambu Lab and Creality have their own lists; anything else takes a free-text
  model. "No Printer" is an option for accessory-only handovers.
- **MFMS** — asks whether a multi-filament system is included, then reveals brand
  and model (AMS lite / AMS 1 / AMS, CFS / CFS-C, or free text).
- **Accessories** — checklist of what came with the printer. Three items open
  extra fields when ticked: MFMS cable (4-pin, 6-pin), filament (type and
  amount), and Others (free text).
- **Condition at handover** — free-text description of existing damage. Worth
  filling in properly; this is the field that settles arguments later.
- **Liability notice** — sits directly above the signature so the customer reads
  it before signing.
- **Two signatures** — one for handover, one for takeover, each with its own date
  field. The handover date defaults to today; the takeover date is left blank
  until the printer goes back.

Sub-fields stay hidden until the answer above them calls for them, so the form
stays short on screen.

## Output

**Print / Save as PDF** at the bottom opens the browser print dialog. The button
itself and the page background are stripped from the printout.

If the green accent bars don't appear on the PDF, turn on "Background graphics"
in the print dialog — browsers leave them off by default.

## Signatures

Sign with a finger, stylus or mouse in the box. Clear signature wipes that one
pad only; the two pads are independent. Resizing the window or rotating a tablet
redraws the pad and keeps what was already signed.

Nothing on this form is saved anywhere. Closing or reloading the page loses
everything, signatures included. Print or save the PDF before you leave the
customer.

## Customising

Everything editable is plain HTML, no build step:

| What | Where |
| --- | --- |
| Printer brands | the `#brand` select |
| Bambu Lab and Creality model lists | the `#bambuModel` and `#crealityModel` selects |
| MFMS model lists | the `#mfmsBambuModel` and `#mfmsCrealityModel` selects |
| Accessory checklist | the `.checklist` block in the Accessories section |
| Liability wording | the `.notice` block |
| Colours | the `:root` variables at the top of the stylesheet |

Adding a model is one `<option>` line. Adding an accessory that needs a follow-up
field means copying the pattern used by Filament: a checkbox with an `onchange`
handler that toggles the `show` class on a `.subfield` div.

## Files

- `index.html` — the whole form, logo included as an embedded image
- `README.md` — this file
