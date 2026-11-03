## 1. Interest of content

| Page | Comments |
|---|---|
| **Time Space Compression** | The most engaging page. It defines the concept, lists three benefits and expands on each one. The 2025 Nepal example makes it concrete and current. |
| **Quantum Computing** | Good range of applications (drug discovery, logistics, finance), it cites a source (PMC article) and links to the Medical page. The "Basic Facts" section could explain superposition a little more clearly. |
| **Data** | Good idea to present both positives and negatives, and it links to the Data Protection Act and data.gov.uk. Some points are vague ("you can craete fun models", "creating them is bad for local enviroment"). It's not clear what "them" refers to. |
| **Medical Applications** | Relevant, but thin: only two applications are given (hospital information systems, laboratory computing). Adding examples such as imaging/diagnostics, wearables or robotic surgery would help. |
| **Cyber Security** | Interesting angle (lesser-known roles plus salaries), but most of it isn't finished. Of the 13 roles listed, only two (Penetration Tester and Security Consultant) have real descriptions. The rest of the page repeats the same "Security Specialist / Incident Responder" block five times. The page also never explains how these roles are *beneficial*, which is the site's theme. |

The home page is just a heading ("The Pages") and a list of links. A sentence or two introducing the theme of "beneficial computing" would tie the site together.

## 2. Consistency and quality of visual presentation

- **Shared stylesheet:** Using one `stylesheet.css` is good. However, **`doc2.html` (Cyber Security) never links to it**, so it shows in the browser's default style and looks like a separate site.
- **Colour contrast:** Hot pink text on a dark green background (all headings) is hard to read and would probably fail WCAG contrast checks. Body text is also hot pink on white. Using a darker text colour, or keeping pink for accents only, would make the pages easier to read.
- **Styling coverage:** The CSS styles `p, ul, ol, h1, h2, h3, h5` but not `dl/dt/dd`, `h4` or `a`. So parts of the Medical page don't match, and links use the default blue next to pink text.
- **Navigation is inconsistent:**
  - Medical Applications and Cyber Security have **no link back to the home page**.
  - On the other pages, the "Home Page" link is in different places: before the author section on Quantum and Time Space, and after it on Data.
  - A shared nav bar at the top of every page would fix this.
- **Heading structure:** Every page jumps from `h1`–`h3` straight to `h5` for "Page Author". On Cyber Security, a paragraph comes *before* the `h1`.
- **Page titles** use different styles: "Main", "DATA ", " Roles in CYBERSECURITY ", "Quantum Computing". "Main" doesn't describe the site.
- **Unused element:** Quantum Computing has a `<button type="submit">Click</button>` that does nothing and isn't inside a form.

## 3. Quality of written presentation

Time Space Compression and Medical Applications are mostly well written. The other pages need proofreading. Spelling errors found:

- **Data:** campagning, differnt, represenitive, infulencing, variery, reaserch, personlised tutours, identifing, libary, wether, craete, negetives, enviroment, cenetrs, safe gaurdings, organistaions
- **Cyber Security:** cybersecuroiity, unkown, secuity (×2), memebrs, vunerabiliites, plolicies, porvide, comapny; "stimulate attacks" should be "simulate"
- **Quantum Computing:** simultated, combitorial, Finiancial; "streaming of manufacturing" probably means "streamlining"; "Quantum algorithms is" should be "are"
- **Time Space Compression:** expieriences, understnading; "the concept that describe" should be "describes"

Other writing issues:

- The **Data** page is written almost entirely in lowercase, including sentence starts and headings ("welcome to my webpage about data"). It also has an all-caps heading ("THERE IS LOADS OF DATA STORED"). The tone is more casual than on the other pages.
- On **Quantum Computing**, sentences have no full stops, and the source link text is just "here", sitting outside the paragraph.
- On **Cyber Security**, every role's heading is followed by the same sentence. Two roles also have the same salary (£52,493) with no source given.
- Joke author notes such as "after crashing her boat this morning", "Age: Old" and "No. of hours of sleep: 7" are fun but don't match the informative tone of the rest of the site.

## 4. Validity of HTML

Here are the problems in each file. Running every page through the [W3C validator](https://validator.w3.org/) would catch all of them.

**`index.html`, `QuantumComputing.html`**
- `lang="en-US"` is on `<head>`; it belongs on `<html>`.

**`MedicalApplications.html`**
- `<ol>` is nested directly inside `<dl>`, and `<dt>`/`<dd>` are inside `<li>`. Both are invalid. Use either a `<dl>` or an `<ol>`, not both.
- No closing `</html>` tag. `lang="en-UK"` isn't a valid language tag; use `en-GB`. No viewport meta tag.

**`TimeSpaceCompression.html`**
- Uses `<header>` instead of `<head>`, which puts `<title>` and `<link>` in the wrong place.
- No `<meta charset>` and no `lang`. `<Body>` is capitalised, unlike every other page.

**`prac3.html` (Data)**
- `<ul></ul>big data has many uses including</ul>`: the list is closed immediately, a stray `</ul>` follows, and the three `<li>` items below aren't inside any list.
- No `<meta charset>` and no `lang`. The `href` on the data.gov.uk link has no quotes. That's technically allowed, but the other links use quotes.

**`doc2.html` (Cyber Security)**
- `<a>` elements sit directly inside `<ul>` and wrap the `<li>`s. The `<li>` must be the direct child, with the `<a>` inside it.
- **Duplicate IDs:** `security-specialist` and `incident-responder` are each used 5 times.
- **Broken in-page links:** 11 of the 13 contents links point to IDs that don't exist. Security Consultant fails because of the capital S (`id="Security-consultant"`). Only Incident Responder and Penetration Tester work.
- The `penetration-tester` section is headed "Security Specialist".
- The salary label uses `<b>` outside a paragraph, followed by a separate `<p>`.
- The closing tag is `</html` (missing `>`). No `<meta charset>`, `lang` or stylesheet link.

## 5. Evidence of collaboration

**Author info not written by the author:** this is done well. Git blame shows each "Page Author" section was added by someone other than that page's author:

| Page | Page author | Author section written by |
|---|---|---|
| Quantum Computing | Eloise Slater | Isabelle Barker (`ed423ec`) |
| Time Space Compression | Belle (Isabelle) Barker | Eloise Slater (`1e15488`) |
| Data | Georgia Wilde | Eloise Slater (`e90a3dc`) |
| Medical Applications | Tess Deakin | Eloise Slater |
| Cyber Security | Blossom Nwokolo | *missing; no author section yet* |

Three of the four author sections were written by Eloise, so this cross-authoring could have been shared out more evenly.

**Balanced contributions from members:** every member owns at least one file, which is good. But the commit history is uneven (merge commits excluded):

| Member | Commits | Lines added | Main work |
|---|---|---|---|
| Eloise Slater | 28 | 128 | Quantum Computing, home page links, stylesheet, fixes across the site |
| Blossom Nwokolo | 3 | 88 | Cyber Security |
| roseflower456 (Georgia Wilde?) | 6 | 62 | Data |
| Isabelle Barker | 4 | 33 | Time Space Compression |
| Tess Deakin | 7 | 30 | Medical Applications, stylesheet |
| Kate | 2 | 12 | Initial `index.html` |

Eloise made more than half of all commits and did most of the work linking the pages together. Kate's only contribution is the first version of the home page. One member commits as `roseflower456`, so the history doesn't show their real name. Many commit messages give no information: "m", "x", "3", "changes", "Test", "to check it". Messages that describe the change would make each person's contribution easier to see.
