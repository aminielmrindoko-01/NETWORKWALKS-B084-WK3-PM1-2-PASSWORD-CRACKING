# NETWORKWALKS-B084-WK3-PM1-2-PASSWORD-CRACKING

### Password Cracking with John the Ripper & Networkwalks Tools

**W3-PM1 & W3-PM2 | CYBERSECURITY | NETWORKWALKS**

| Field | Detail |
| --- | --- |
| Student Name (Cybersecurity Professional) | AMINIELI MRINDOKO|
| Program / Batch | B084 |
| Instructor | ______________________________ |
| Submission Date | 20 NOVEMBER 2026 |
| Modules Documented | W3-PM1 — Password Cracking with JTR; W3-PM2 — Password Cracking with NW Tools |
| Training Target | `My Locked PDF1.pdf` |
| Authorization / Lab Scope Confirmation | ______________________________ |
| Activities Covered | PDF hash extraction, password recovery, verification, and flag documentation |

# 1. Liability Disclaimer

This report documents an educational password-recovery exercise using Networkwalks training material. Any repetition must remain within an authorized lab scope and use files the participant owns or has permission to test. The authorization field above is left for the student to complete; this report does not establish written permission for other targets.

The screenshots retain the exercise solution and local desktop information as submission evidence. Networkwalks content and branding belong to their respective owners.

# 2. Introduction

This report covers two separate Week 3 projects: **Password Cracking with JTR (W3-PM1)** and **Password Cracking with NW Tools (W3-PM2)**. Both concern the training document `My Locked PDF1.pdf`, using different interfaces to recover its password.

Project Module 1 uses Johnny, the graphical interface for John the Ripper. Project Module 2 uses the Networkwalks Hash Calculator and Password Cracker. Each project has its own walkthrough and screenshot evidence.

The assignment titles supplied for this report are:

1. `W3-PM1 - Week3 - Project Module1 - Password Cracking with JTR v1.pdf`
2. `W3-PM2 - Week3 - Project Module2 - Password Cracking with NW Tools v1.pdf`

This report is based on the supplied screenshots and hash file. The full assignment briefs and marking rubrics have not been reviewed. No new password-recovery run was performed while preparing this repository.

# 3. Tools Used

| Tool / Material | Purpose in the Recorded Exercise |
| --- | --- |
| Windows | Desktop environment shown in the screenshots. |
| Johnny | Load the PDF hash, configure the John executable, and display the recovered password. |
| John the Ripper 1.9.0-jumbo-1 | Password-recovery engine detected in Johnny's settings. |
| OnlineHashCrack PDF extraction page | Displays the PDF extraction output in Project Module 1. |
| Networkwalks Hash Calculator | Shows file digests and PDF-specific extraction output. |
| Networkwalks Password Cracker | Runs the browser dictionary exercise and displays its results. |
| Browser PDF viewer | Shows the password prompt and opened training PDF. |
| `hash1.txt` | Supplied PDF hash preserved in the repository. |

# 4. Activities Performed

## 4.1 Project Module 1 — Password Cracking with JTR

### Step 1: Open Johnny and prepare the hash

The initial capture shows Johnny open with an empty password list. A later capture shows extraction completed for `My Locked PDF1.pdf`, with output beginning `$pdf$4*4*128*`. The supplied value is preserved in [hash1.txt](labs/01-john-the-ripper/inputs/hash1.txt).

### Step 2: Load the hash and configure the engine

The hash appears in Johnny's password list. Settings screenshots show an executable ending in `run/john.exe`, a detected John the Ripper `1.9.0-jumbo-1 OMP` engine, and a 15-second interface update interval.

The selected attack mode, wordlist, and runtime are not visible. Earlier status counters differ from the final single-PDF result; they are not used to establish this project's recovered-password count.

### Step 3: Record the recovered password

The final Johnny result shows format PDF and `100% (1/1: 1 cracked, 0 left)`. The recovered password is `good-luck`.

![Project Module 1 — Johnny password result](labs/01-john-the-ripper/screenshots/2026-11-20-213833.png)

### Step 4: Verify the PDF and capture the flag

The following captures show a password prompt and then the opened one-page document. The displayed flag is `nw{cybersecurity_flag_captured_2608}`.

![Project Module 1 — Opened PDF and flag](labs/01-john-the-ripper/screenshots/2026-11-20-214010.png)

**Complete procedure and eight screenshots:** [Project Module 1 walkthrough](labs/01-john-the-ripper/README.md).

## 4.2 Project Module 2 — Password Cracking with NW Tools

### Step 1: Inspect the initial input

The first calculator capture shows the File view and digest outputs. The next screenshot contains a plain hexadecimal value in the cracker's PDF hash field. No outcome is visible for that exact input.

### Step 2: Extract the PDF-specific value

The later calculator capture uses the PDF view and displays structured output beginning with `$pdf$`. It reports revision R4, version V4, and a 128-bit key length. This is the input representation shown in the subsequent cracking attempts.

### Step 3: Record the unsuccessful built-in-list attempt

The built-in list contains 100 entries. The result shows `100 / 100` candidates tried and reports that the password was not cracked with that wordlist. This establishes the outcome of that attempt, not that recovery is impossible.

![Project Module 2 — Built-in wordlist failure](labs/02-networkwalks/screenshots/2026-11-20-215238.png)

### Step 4: Record the successful attempt

The later screenshot shows `99 / 99`, a log match for `good-luck`, and a success message. The active wordlist is not visible in that capture.

![Project Module 2 — Successful password match](labs/02-networkwalks/screenshots/2026-11-20-215713.png)

The source file `passwords_list.txt` returned an access-denied response during repository preparation. Its contents and relationship to this run remain unverified. See the [input availability note](labs/02-networkwalks/inputs/README.md).

**Complete procedure and five screenshots:** [Project Module 2 walkthrough](labs/02-networkwalks/README.md).

## 4.3 Results Summary

| Activity | Recorded Outcome | Evidence Limit |
| --- | --- | --- |
| W3-PM1 — Johnny / JTR | `good-luck`; one PDF password recovered. | Attack settings and runtime are not shown. |
| W3-PM1 — Verification | Opened PDF displays `nw{cybersecurity_flag_captured_2608}`. | Original target PDF was not supplied. |
| W3-PM2 — Built-in list | 100 candidates tried; no match. | Applies to this recorded attempt. |
| W3-PM2 — Later attempt | `good-luck`; successful match with `99 / 99` displayed. | Active wordlist is not identified. |

The PDF-opening evidence belongs to Project Module 1 and predates the browser run. There is no separate post-run PDF-opening capture for Project Module 2.

# 5. Risk Analysis / Impact

These findings describe the training evidence, not a security assessment of Networkwalks infrastructure. No production-system severity rating is assigned.

| Finding | Evidence / Observation | Potential Impact or Interpretation |
| --- | --- | --- |
| Training password was recoverable | Both interfaces display `good-luck`. | Someone who obtains this PDF and recovers its password can read its contents. |
| One failed list did not end the exercise | The 100-entry attempt failed; a later attempt succeeded. | A failed list does not establish that recovery is impossible. |
| Input representation changed during the workflow | A plain hexadecimal value appears before the structured `$pdf$` extraction. | Confusing these inputs can prevent a valid attempt. |
| Successful-run settings are incompletely recorded | Johnny options and the browser's successful wordlist are not shown. | A reviewer cannot reproduce the exact runs from screenshots alone. |
| Evidence contains the solution | Screenshots show the password, flag, and local paths. | Publishing the evidence exposes those details to readers. |

# 6. Recommendations

1. **Replace the demonstrated password in any reused copy.** Treat `good-luck` as disclosed because it appears in this report and its screenshots.
2. **Check the input format before starting.** Preserve the complete PDF-specific extraction value for this exercise.
3. **Record each attempt's configuration.** Include tool versions, attack options, wordlist identity, candidate count, and runtime when available.
4. **Retain unsuccessful results.** Keep the failed attempt alongside the success to document the actual sequence.
5. **Verify each project's outcome.** Add a post-run PDF-opening capture for Project Module 2 if required by its brief.
6. **Complete missing submission material.** Fill in personal details, supply the readable original wordlist if required, and check both assignment briefs.
7. **Review the sharing audience.** Confirm whether the course permits public distribution of its materials and flag before publishing.

# 7. Conclusion

The supplied Week 3 screenshots document successful PDF password recovery using Johnny / John the Ripper for Project Module 1 and Networkwalks tools for Project Module 2. Both display `good-luck`. The Project Module 1 verification capture shows the opened document and its flag, `nw{cybersecurity_flag_captured_2608}`.

The exercise illustrates the importance of selecting the correct extraction format, documenting unsuccessful and successful attempts, and verifying tool output against the target document. Missing attack settings and wordlist information limit exact reproducibility.


## Repository structure

```text
networkwalks/
│   ├── project-report.md
│  
├── labs/
│   ├── 01-john-the-ripper/              # W3-PM1: JTR project
│   │   ├── README.md
│   │   ├── inputs/hash1.txt
│   │   └── screenshots/                 # 8 original captures
│   └── 02-networkwalks/                # W3-PM2: NW Tools project
│       ├── README.md
│       ├── inputs/README.md              # Wordlist availability note
│       └── screenshots/                 # 5 original captures

```


This verifies screenshot checksums and local Markdown link targets. No application installation or package dependencies are needed to read the reports.

— End —
