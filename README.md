# MDHB: Multi-Dimensional Online Harm Detection Benchmark

Official repository for the EMNLP 2026 paper:  
**"MDHB: A Multi-Dimensional Online Harm Detection Benchmark with Self-Refining Sentinel"**

[![Conference](https://img.shields.io/badge/EMNLP-2026-blue.svg)](https://2026.emnlp.org/)
[![License](https://img.shields.io/badge/License-Academic%20DUA-red.svg)](#data-access-policy)
[![Access](https://img.shields.io/badge/Data%20Access-Controlled%20Application-orange.svg)](#how-to-apply-for-data-access)
[![Dataset](https://img.shields.io/badge/Instances-7%2C500-green.svg)](#benchmark-overview)

---

## 📖 Benchmark Overview

Online harm detection is a critical cornerstone of trustworthy AI and content safety governance. However, existing benchmarks primarily focus on isolated single-task violations or explicit lexical insults, leaving models vulnerable to covert, multi-dimensional, and structurally intricate threats.

To address these challenges, we introduce **MDHB (Multi-Dimensional Online Harm Detection Benchmark)**, comprising **7,500** standardized high-quality textual instances spanning four core harm dimensions alongside a benign control group:

- **Misinformation (1,500 samples)**: False factual claims with misleading intent, categorized into Political Manipulation, Health & Pseudoscience, Social Emergencies, and Urban Legends.
- **Toxicity (1,500 samples)**: Implicit hate speech, identity-based derogation, and veiled hostility.
- **Sarcasm (1,500 samples)**: Pragmatic reversals split into **Offensive Sarcasm** (harmful attacks veiled in irony) and **Non-Offensive Sarcasm** (benign self-deprecation and venting, serving as a challenging hard-negative).
- **Logical Fallacies (1,500 samples)**: Structurally flawed argumentation across formal and informal fallacies (e.g., False Dilemma, Slippery Slope, Ad Hominem).
- **Normal / Benign (1,500 samples)**: Safe social media discourse serving as the control baseline.

The dataset is strictly partitioned into a **Validation Set (1,250 samples, 250 per category)** and a **Test Set (6,250 samples, 1,250 per category)**.

---

## 🔒 Data Access Policy & Ethical Statement (受控访问策略与伦理声明)

> ### ⚠️ Important Notice / 重要声明
> **English**: Given that MDHB contains real-world instances of online harms, misinformation, offensive language, and covert malicious content, releasing the raw dataset unconditionally to an open public repository presents substantial risks of data abuse, toxic model fine-tuning, and secondary dissemination of harmful content.  
> Therefore, we adopt a **Controlled Access Release Policy**. The dataset is **NOT directly hosted in this public repository**. Access is strictly limited to non-commercial academic research and defensive safety alignment, subject to formal identity verification and a signed **Data Usage Agreement (DUA)**.
> 
> **中文说明**：鉴于 MDHB 包含网络有害言论、虚假信息及其他潜在有害内容，将其无条件公开发布至公开平台可能带来数据滥用和有害内容二次传播的风险。因此，我们采用**数据集受控访问（Controlled Access）**策略：原始数据不会直接公开托管在开放仓库中。申请人需下载并签署《数据使用许可协议》，经作者团队核验申请人学术身份与研究用途后，通过邮件单独发放私有下载链接。

---

## 📝 How to Apply for Data Access (数据集申请流程)

To obtain access to the MDHB benchmark, please follow the steps below:

```
┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│ 1. Download Agreement   │ ──> │ 2. Fill & Sign DUA      │ ──> │ 3. Email Application    │ ──> │ 4. Receive Secure Link  │
│ (PDF / Word in repo)    │     │ (Institutional Info)    │     │ (Attach Signed DUA)     │     │ (Within 2-3 Workdays)   │
└─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘
```

### Step 1: Download the Data Usage Agreement
Download the formal agreement template from this repository:
- 📄 **PDF Version**: [`MDHB_Data_Usage_Agreement.pdf`](./MDHB_Data_Usage_Agreement.pdf)
- 📝 **Word Version**: [`MDHB_Data_Usage_Agreement.docx`](./MDHB_Data_Usage_Agreement.docx)
- 📋 **Markdown Preview**: [`DATA_USAGE_AGREEMENT.md`](./DATA_USAGE_AGREEMENT.md)

### Step 2: Fill in Applicant Information & Sign
- Please complete all required fields on the last page of the agreement:
  - **Requester's Name** (申请者姓名)
  - **Requester's Institutional Email** (申请者机构邮箱, prefer `.edu` / university / research institute email)
  - **Position / Title** (申请者职位: Faculty, Postdoc, Ph.D. Student, Graduate Student, Researcher)
  - **PI / Supervisor's Name & Email** (项目负责人/导师姓名及邮箱)
  - **Affiliation & Department** (所属机构及院系/实验室)
  - **Detailed Research Purpose** (具体学术研究用途描述)
  - **Handwritten or Verified Digital Signature** (手写或经核验的电子签名) and **Date** (日期)

### Step 3: Send Application Email
Send the signed agreement (scanned PDF or clear photo) to the dataset management team:
- **Recipient Email**: `[Contact Email: e.g., your_email@domain.edu / corresponding_author@domain.edu]`
- **Email Subject**: `[MDHB Dataset Application] - <Your Name> - <Your Affiliation>`
- **Email Body Template**:
  ```text
  Dear MDHB Dataset Team,

  I am writing to formally request access to the MDHB (Multi-Dimensional Online Harm Detection Benchmark) dataset for non-commercial academic research.

  - Applicant Name: [Your Name]
  - Affiliation: [Your University / Research Institution]
  - Position: [Faculty / Postdoc / Ph.D. Candidate / Master's Student]
  - Supervisor / PI: [Supervisor's Name and Email]
  - Research Topic: [Briefly describe your project, e.g., LLM Safety Alignment / Implicit Harm Detection]

  I have read, understood, and agreed to all terms in the MDHB Data Usage Agreement. Please find my signed agreement attached.

  Thank you for your time and consideration.

  Sincerely,
  [Your Name]
  [Your Title & Affiliation]
  [Institutional Email Address]
  ```

### Step 4: Verification & Data Link Delivery
- Applications will be reviewed within **2–3 business days**.
- Applications using commercial personal emails (e.g., `@163.com`, `@qq.com`, `@gmail.com` without verifiable institutional identity) or missing required information may be rejected.
- Upon successful verification, a private download link (Google Drive / Baidu Netdisk) with credentials will be dispatched to your institutional email.

---

## 📊 Dataset Schema & Format

The dataset is formatted in standard UTF-8 JSON Lines (`.jsonl`). Each instance contains the following structured fields:

```json
{
  "id": "MDHB_TEST_00124",
  "text": "Sure, because putting a completely untested surgical mask over your face all day definitely keeps all the germs away.",
  "label": "Sarcasm",
  "sub_dimension": "Offensive Sarcasm",
  "split": "test",
  "meta_info": {
    "source_corpus": "Social_Media_UGC",
    "verified_by_human": true
  }
}
```

### Label Space
| Top-Level Label | Fine-Grained Sub-Categories | Description |
| :--- | :--- | :--- |
| `Misinformation` | Political, Health, Social Emergencies, Urban Legends | Factual falsehoods intended to mislead. |
| `Toxicity` | Latent Malice, Hate Speech, Identity Derogation | Implicit attacks and targeted cyberbullying. |
| `Sarcasm` | Offensive Sarcasm / Non-Offensive Sarcasm | Pragmatic irony and hard-negative self-deprecation. |
| `Logical Fallacy`| Formal & Informal Fallacies | Structurally flawed or distracting rhetorical logic. |
| `Normal` | Benign Dialogue / Everyday Social Text | Safe, non-violating control instances. |

---

## 📜 Citation

If you use the MDHB dataset or refer to our benchmark and framework in your research, please cite our paper:

```bibtex
@inproceedings{mdhb2026srs,
  title={{MDHB}: A Multi-Dimensional Online Harm Detection Benchmark with Self-Refining Sentinel},
  author={Huang, Yuting and Huang, Xiaoyong and Wang, Hao and Sun, Heli and Wu, Jiaruo and Wang, Zejun and Shi, Yunyun and Yue, Guanlan and He, Liang},
  booktitle={Proceedings of the 2026 Conference on Empirical Methods in Natural Language Processing (EMNLP)},
  year={2026}
}
```

---

## ⚖️ Ethics & Usage Terms Summary

1. **Non-Commercial Academic Use Only**: The dataset must strictly be used for non-commercial scientific research, safety alignment, and defensive moderation algorithms.
2. **No Redistribution**: You must NOT copy, re-host, sell, redistribute, or publicly publish raw samples on any open platform.
3. **Content Disclaimer**: The instances in MDHB reflect real-world social media content compiled solely for defensive safety research and do not reflect the opinions or stances of the authors or their institutions.
4. **Access Revocation**: The dataset creators reserve the right to revoke access and request immediate deletion of data copies upon any violation of the agreement.

For inquiries, please contact: `[Corresponding Author Email]`
