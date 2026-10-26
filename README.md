# 🛡️ APAAR Guardian
### Student Data Integrity & Verification Platform

APAAR Guardian is a web-based prototype designed to demonstrate student-record validation, institutional admission monitoring, and role-specific verification workflows.

<p align="center">
  <a href="https://apaar-guardian-frontend.onrender.com/login">
    <strong>🚀 Launch Live Demo</strong>
  </a>
</p>

---

## 📸 Application Walkthrough

Explore the APAAR Guardian interface through the following screenshots. Each section demonstrates a key feature and explains its role in the student-record verification workflow.

## 01. 🔐 Login & Role-Based Access

**Purpose:** Provide a role-specific entry point to APAAR Guardian.

Users can select one of three roles:

- **College Admin** — manages institutional student records and admission workflows.
- **AICTE Officer** — represents the regulatory oversight role.
- **Verifier** — represents the academic-record verification role.

The login interface accepts a registered mobile number and provides an OTP verification workflow. After successful verification, users are directed to the application experience associated with their selected role.

> **Demo credentials:** The prototype uses mock data and a fixed demonstration OTP (`123456`). This is a demonstration mechanism, not production-grade authentication.

<p align="center">
  <img src="https://github.com/user-attachments/assets/c58b5bd6-1a4b-4596-9435-4914e1583a24" alt="APAAR Guardian login page showing role selection and OTP verification" width="90%">
</p>

<p align="center"><em>Role selection, mobile-number entry, OTP verification, and access to the platform.</em></p>

---

## 02. 📂 Template Download & Student Upload

After logging in, the college admin downloads the official Excel template, which has the exact columns AICTE needs: APAAR ID, name, mobile, programme, admission type and quota. The admin pastes in the student records and uploads the file.

The system accepts only `.xlsx` or `.csv` files, rejects macro files, and gives every upload a version number and a fingerprint (SHA-256), so a file can’t be quietly swapped later.

A progress bar at the top shows the four steps: download template, upload file, review errors, submit. Checking happens after the upload, and the next screen shows the results.

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2a30e98-abb7-443a-9bb9-163150445728" alt="Student template download and upload interface" width="90%">
</p>

<p align="center"><em>Download the template, upload student records, and begin validation.</em></p>

---

## 03. 🧾 Error Report with Row Numbers

After the upload, the two gates check every row, and the college sees the results straight away instead of waiting weeks for a rejection.

A summary shows how many rows were checked, how many are valid, and how many have errors or warnings. Below it, each problem is listed by row number with a plain-language reason and a suggested fix: an ID with 11 digits, a possible duplicate student, an ID that isn’t in the registry (with a “did you mean” suggestion), or a missing ID that is marked as pending.

Errors must be fixed before the final submission. Warnings, such as being close to the approved intake, can go through with a flag. The college can fix rows on screen, download the error file, and re-check.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d32585c8-2758-4950-97e5-e32f284db764" alt="Validation error report with row numbers, error explanations, and suggested fixes" width="90%">
</p>

<p align="center"><em>Row-level validation findings help administrators identify and correct data-quality issues.</em></p>

---

## 04. ✅ Institutional Trust Score

Once the file passes the gates and the college submits it, the system gives the college a trust score out of 100 and a colour: green, yellow or red.

The score starts at 100 and loses points for each problem found, with a limit per check so one issue can’t erase everything. The screen shows where the points were lost (pending or invalid IDs, duplicate students, admissions above the approved intake) and what each check found.

The score is sent to the AICTE compliance officer, and the college can see it too. Yearly checks will change this same score later.

<p align="center">
  <img src="https://github.com/user-attachments/assets/08d44624-284f-45fb-bbcb-ad450f781015" alt="Institutional trust score with colour-coded status and validation findings" width="90%">
</p>

<p align="center"><em>A colour-coded score summarizes validation findings and institutional compliance indicators.</em></p>

---

## 05. 🏛️ AICTE Compliance Dashboard

The compliance officer’s home screen. It shows how many colleges are green, yellow and red, and lists the colleges with the lowest scores first so the riskiest ones are seen first.

Each row shows the college, its trust score and colour, and the main reason in plain words, such as intake exceeded or exam registration mismatch.

The officer can filter by state, programme or colour, open a case for a red college, review a yellow one, or export a report for policy and accreditation.

> **Human oversight:** A red flag means “send an inspector,” not “guilty,” and the final decision stays with a human.

<p align="center">
  <img src="https://github.com/user-attachments/assets/54c33015-a995-41da-898d-a73659f4ea3a" alt="AICTE compliance dashboard with institutional trust scores and colour-coded risk indicators" width="90%">
</p>

<p align="center"><em>The compliance dashboard helps officers prioritize institutional reviews and investigate potential issues.</em></p>

---

## 06. 📊 Yearly Update & Trust Score Changes

The first score is not final. Every year the system runs new checks against records the college can’t edit: exam registrations, exam fees and academic marks.

Each finding is applied to the same running score, so a college that started at 80 (green) can fall to 73 and then 65 (yellow), or further into red.

Every change is kept in a history with its reason, so the college and the AICTE officer can see exactly what moved the score and when. Colleges aren’t punished forever: when they fix the problems and a re-check confirms it, the points come back.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e797d63c-9801-4109-8a81-504aa309f02f" alt="Yearly validation findings and institutional trust score history" width="90%">
</p>

<p align="center"><em>Score history records changes over time and explains the findings behind each adjustment.</em></p>

---

## 07. 🤝 Consent-Based Verification Request

When an employer wants to verify a student, the student gets a request. The screen shows who is asking (a registered verifier), why, and exactly which details they want.

The student ticks only what they agree to share: enrolment status, programme name and years of study are ticked here, while mobile number and date of birth are left off.

The student can approve or decline. Approved access expires after a set time, and every lookup is written to the audit log, so misuse can be traced. This is limited disclosure: the employer sees what they need and nothing more.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a7c7835b-9972-4de9-b591-193205563a8f" alt="Student consent request with selectable information-sharing permissions" width="90%">
</p>

<p align="center"><em>Students can review verification requests and choose which information to share.</em></p>

---

## 08. 📱 QR-Based Degree Verification

At graduation, the college prints a QR code on the degree certificate, together with the APAAR ID. The QR carries a digitally signed copy of the student’s record.

A recruiter scans it with the verifier app, and the app checks the signature and shows a clear result: genuine or not, with only the limited details needed (programme, years, masked ID). A forged or edited certificate fails the signature check.

The check works without internet, and the app refreshes a list of cancelled certificates whenever it is online. If a certificate was cancelled after the scanner last synced, an offline scan can’t know about it, so the screen shows when the list was last updated.

<p align="center">
  <img src="https://github.com/user-attachments/assets/5714bcce-30f2-46a4-99dc-099dd1f493a6" alt="QR-based academic credential verification interface" width="90%">
</p>

<p align="center"><em>QR-based verification is designed to support credential authenticity checks with limited information disclosure.</em></p>

---

## 09. 🔄 System Workflow Diagrams

The following diagrams illustrate the platform's process flows and how its components connect.

### Flow 1

<p align="center">
  <img src="https://github.com/user-attachments/assets/772b2abc-517d-4149-9e0d-00e11ed962d5" alt="APAAR Guardian system flow diagram 1" width="85%">
</p>

### Flow 2

<p align="center">
  <img src="https://github.com/user-attachments/assets/65e585db-3605-45f0-94f3-17c883ba9fbf" alt="APAAR Guardian system flow diagram 2" width="85%">
</p>

### Flow 3

<p align="center">
  <img src="https://github.com/user-attachments/assets/a23bbbe9-184b-4f21-9967-10538324dc3c" alt="APAAR Guardian system flow diagram 3" width="85%">
</p>

---

## 🔄 End-to-End Demo Flow

The intended demonstration follows this sequence:

1. Open APAAR Guardian and select a demo role.
2. Complete the demonstration OTP flow.
3. Access the corresponding application workspace.
4. Review institutional or role-specific information.
5. Upload student data where the selected role permits it.
6. Examine validation results and flagged records.
7. Inspect individual records and their available status information.
8. Review batch history and verification-related workflows.

The exact steps available depend on the selected role and the features implemented in the deployed version.

---

## 🧪 Demo Environment

| Item | Details |
|:--|:--|
| Application | APAAR Guardian |
| Interface | Web application |
| Deployment | Render |
| Authentication demonstration | Fixed demo OTP |
| Demonstration data | Synthetic / mock student records |
| Primary workflow | Student-record validation and verification |

---

## 🔐 Security & Privacy Notes

- The current prototype uses mock student data for demonstration.
- The login interface illustrates role selection and an OTP-style verification flow.
- Role-specific access must be enforced by the backend, not just by hiding frontend screens.
- A fixed demo OTP must not be treated as secure production authentication.
- Production deployment would require proper identity verification, authorization, secure data storage, audit logging, and consent handling.

---

## ⚠️ Disclaimer

APAAR Guardian is a prototype developed for demonstration and evaluation. It is not an official APAAR service and is not officially affiliated with APAAR, AICTE, or any government department.

The demonstration uses synthetic data and should not be used to process real student records without appropriate authorization and security controls.

---

## 🔗 Project Links

- **Live Application:** [APAAR Guardian](https://apaar-guardian-frontend.onrender.com/login)
- **GitHub Repository:** Add your repository URL here

---

<p align="center">
  <strong>APAAR Guardian — Making student-record verification more transparent, traceable, and trustworthy.</strong>
</p>
