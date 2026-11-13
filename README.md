# CIP-B106 Case Study 3: Amazon Echo Show 8 IoT Evidence Investigation

## 1. Project Overview

This project documents a digital forensic examination of an Amazon Echo Show 8 (2nd Generation) eMMC training image as part of the CIP-B106 Mobile and IoT Forensics course.

The investigation focused on identifying, extracting, examining, and correlating digital artefacts from the device's userdata partition to reconstruct device activity and establish a timeline of relevant events.

The examination was conducted using Kali Linux and established digital forensic tools. Only authorised course-provided training evidence was used. No live Amazon Echo device or cloud account was accessed.

## 2. Case Information

| Field | Description |
|---|---|
| Course | CIP-B106 Mobile and IoT Forensics |
| Case Study | Case Study 3 – Echo Show 8 |
| Case Identifier | CIPB106-EchoShow8 |
| Device | Amazon Echo Show 8 (2nd Generation) |
| Model Code | AEOAT |
| Device Codename | athena |
| Operating System | Fire OS 7.5.6.0 / Android 9 |
| Forensic Environment | Kali Linux |
| Evidence Type | eMMC training image and userdata partition |

## 3. Investigation Objectives

The examination aimed to:

- Identify the device model, operating system, and configuration.
- Examine local user and Amazon account artefacts.
- Investigate Wi-Fi and Bluetooth configuration records.
- Recover and analyse browser history and search activity.
- Examine Prime Video and Amazon Music-related artefacts.
- Identify Photo Booth images and video upload records.
- Examine Alexa interface logs and recent task records.
- Reconstruct a timeline using timestamps from multiple artefact sources.
- Assess evidence integrity, reliability, and investigative limitations.

## 4. Forensic Tools and Technologies

The following tools were used during the examination:

| Tool | Purpose |
|---|---|
| Kali Linux | Forensic examination environment |
| 7-Zip | Extraction of the supplied evidence archive |
| Sleuth Kit (mmls) | Examination of the partition structure |
| losetup | Attaching forensic images as loop devices |
| SQLite3 | Examination of application and system databases |
| bulk_extractor | Extraction of digital features such as URLs, emails and telephone-related data |
| Scalpel | File carving |
| Foremost | Recovery of JPEG and MP4 file candidates |
| PhotoRec | Recovery of file fragments |
| ExifTool | Examination of recovered image metadata |
| jq | Parsing JSON-based artefacts |
| strings and grep | Searching extracted and recovered data |

## 5. Evidence Examined

The primary evidence consisted of:

- A supplied Amazon Echo Show 8 eMMC training image.
- A derived userdata partition image.
- Android system and user configuration records.
- SQLite application databases.
- Browser history and WebView artefacts.
- Alexa interface logs.
- Photo Booth upload records.
- Recovered JPEG files and file fragments.

The full eMMC image was approximately 7.8 GB, while the derived userdata partition was approximately 3.76 GB.

## 6. Key Findings

### 6.1 Device Identification

The examination identified the device as an Amazon Echo Show 8 (2nd Generation), model AEOAT, with the device codename athena. It was running Fire OS 7.5.6.0, based on Android 9.

### 6.2 User and Account Artefacts

System and account databases contained one local user profile and Amazon account-related records using the display name "Sarfraz".

These records establish account and profile information stored on the device but do not independently establish the identity of the person operating it.

### 6.3 Network and Bluetooth Artefacts

The examination identified two saved Wi-Fi network configurations and two paired Bluetooth devices.

These records establish stored network and pairing configurations. They do not independently prove that a particular network or paired device was actively used at a specific time.

### 6.4 Web and Application Activity

Browser history and application records contained searches, YouTube-related activity, Microsoft sign-in pages, and Prime Video viewing-history entries.

These artefacts helped reconstruct activity recorded by the device during the examination period.

### 6.5 Photo Booth and Recovered Media

Photo Booth databases contained image upload records and video upload information.

The investigation also recovered JPEG candidates through file carving. Most recovered images were cached media artwork and thumbnails.

A video upload record remained in a QUEUED state, without a confirmed completed upload.

### 6.6 Alexa Interface Logs

Alexa interface logs contained Amazon Music RecentlyPlayed card impressions, including an entry referring to a "money heist theme song".

The same title was identified in a recovered earlier log fragment. These records indicate that the item appeared as a recent-content suggestion; they do not establish an exact playback event.

### 6.7 Event Timeline

The investigation reconstructed a device activity timeline covering 21–23 October 2023.

Timestamp analysis involved Unix epoch milliseconds, Unix epoch seconds, WebKit timestamps, ISO-8601 timestamps and local textual timestamps.

Cross-source comparisons helped establish relationships between account activity, Photo Booth records, browser activity, recent tasks and Alexa interface logs.

## 7. Forensic Methodology

The examination followed a structured forensic workflow:

1. **Evidence preparation:** Extraction of the supplied compressed eMMC image.
2. **Evidence identification:** Examination of image size, partition structure and device information.
3. **Evidence handling:** Creation of loop devices and examination of relevant partitions.
4. **Artefact extraction:** Examination of SQLite databases, system files, logs and application records.
5. **File recovery:** Use of Scalpel, Foremost and PhotoRec to identify recoverable file candidates.
6. **Metadata examination:** Analysis of image metadata and timestamp information.
7. **Correlation:** Comparison of independent artefact sources to identify relationships.
8. **Timeline reconstruction:** Conversion of timestamps and reconstruction of relevant device activity.
9. **Reporting:** Documentation of findings, alternative explanations and limitations.

## 8. Evidence Integrity and Limitations

Several limitations were identified:

- No issuer-provided checksum was available for comparison.
- A second loop-device attachment was not configured strictly read-only.
- Read-only handling was not fully documented for every userdata examination step.
- No post-examination hash was recorded.
- Some live SQLite databases were opened in place.
- Phone-call artefacts were not fully examined.
- Cloud-held data and live device activity were outside the investigation scope.
- Device activity records cannot independently identify the person responsible for an action.

These limitations were considered when interpreting the findings and assessing their evidential reliability.

## 9. Repository Structure

The repository may contain the following materials:

```text
CIP_B106_EchoShow8/
│
├── README.md
│
├── Report/
│   └── Digital_Forensic_Examination_Report.pdf
│
├── Evidence_Screenshots/
│   ├── Device_Identification/
│   ├── Partition_Analysis/
│   ├── Database_Examination/
│   ├── File_Carving/
│   └── Timeline_Analysis/
│
├── Commands/
│   └── forensic_commands.md
│
└── Supporting_Materials/
    └── findings_summary.md
```

This structure is a documentation suggestion. Only include files and directories that are actually present in the repository.

## 10. Ethical and Privacy Considerations

The investigation was conducted using authorised course training materials.

Personal identifiers, account details, network credentials, Bluetooth keys, private addresses and potentially sensitive recovered images should not be publicly disclosed.

The examination findings should be interpreted within the limits of the available evidence and should not be used to make unsupported claims about the identity or conduct of individuals.

Raw evidence images and recovered personal data should not be uploaded to a public repository without explicit authorisation.

## 11. Conclusion

The examination demonstrated the use of digital forensic techniques to investigate an IoT device through its eMMC image and userdata partition.

By examining system records, application databases, browser history, media artefacts and Alexa interface logs, the investigation reconstructed aspects of the device's configuration and recorded activity.

The case also demonstrated the importance of evidence integrity, timestamp validation, cross-source corroboration, privacy protection and transparent reporting of forensic limitations.

## 12. Academic Context

This investigation was completed as part of the CIP-B106 Mobile and IoT Forensics course, Case Study 3 – Echo Show 8 IoT Evidence Investigation.

**Author:** [Your name]

**Registration Number:** [Add only if appropriate for the repository's intended audience]

**Cohort:** Cohort 11

**Submission Date:** [Insert confirmed submission date]
