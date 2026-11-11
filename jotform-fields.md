# Online referral form — field list for JotForm

Mirrors the fax referral form (`referral-form.pdf`). Build it in this order; group headings become JotForm "Section Collapse" or "Heading" elements.

**Form title:** Cardiac Preoperative Evaluation — Referral
**Intro text:** For surgeons' offices. We call the patient to schedule. Questions? Call or text 818-724-8200.

## 1 · Referring office
| Field | Type | Required |
|---|---|---|
| Practice | Short text | yes |
| Surgeon | Short text | yes |
| Scheduler / contact person | Short text | yes |
| Office phone | Phone | yes |
| Office fax (for the evaluation letter) | Phone | yes |
| Direct line or extension | Short text | no |

## 2 · Patient
| Field | Type | Required |
|---|---|---|
| Patient name | Full name | yes |
| Date of birth | Date | yes |
| Patient cell phone | Phone | yes |
| Preferred language | Dropdown: English, Spanish, Armenian, Farsi, Russian, Other | no |
| Insurance / plan | Short text | no — note: "skip if the face sheet is attached" |
| Member ID | Short text | no |
| Authorization # (HMO) | Short text | no |
| Primary care physician | Short text | no |
| PCP fax (for copy of letter) | Phone | no |

## 3 · Planned surgery and timing
| Field | Type | Required |
|---|---|---|
| Procedure | Short text | yes |
| Surgery date | Date | no |
| Date status | Radio: Scheduled / Tentative / Not yet set | yes |
| Timing | Radio: Routine / Within 72 hours (we'll also call your office) | yes |
| Planned facility | Short text, with checkbox "Not yet known" | no |
| Anesthesia | Checkboxes: General / Regional or spinal / MAC or sedation / Local / Unknown | no |

## 4 · Reason for evaluation (check all that apply)
Checkboxes, in this order:
- Routine preoperative evaluation
- Coronary disease / stent / bypass
- Heart failure or cardiomyopathy
- Atrial fibrillation / arrhythmia
- Valve disease or murmur
- Pacemaker or ICD
- Abnormal ECG
- Chest pain, dyspnea, or syncope
- Multiple risk factors (diabetes, kidney disease, age)
- Blood thinner / antiplatelet plan
- Facility or anesthesia requirement
- Other (short text)

## 5 · Attachments
| Field | Type |
|---|---|
| Face sheet (demographics and insurance) | File upload (PDF, JPG, PNG) |
| Medication list | File upload |
| Recent ECG, labs, or cardiac records | File upload, multiple |
| Notes for the clinic | Long text |

Helper text under the upload fields: "No files? Fax them to 818-724-8300 and we'll match them to this referral."

## After submit
Thank-you message: "Received. We'll call the patient to schedule, and your office will get the evaluation letter, consult note, and any test reports by fax. Call or text 818-724-8200 with any questions."

Notification: email to referrals@preops.com on each submission (HIPAA mode sends a secure link, not the contents).
