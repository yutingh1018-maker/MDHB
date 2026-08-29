# MDHB: Multi-Dimensional Online Harm Detection Benchmark

Official repository for the EMNLP 2026 paper:  
**"MDHB: A Multi-Dimensional Online Harm Detection Benchmark with Self-Refining Sentinel"**

[![Conference](https://img.shields.io/badge/EMNLP-2026-blue.svg)](https://2026.emnlp.org/)
[![License](https://img.shields.io/badge/License-Academic%20DUA-red.svg)](#-data-access-policy--ethical-statement)
[![Access](https://img.shields.io/badge/Data%20Access-Controlled%20Application-orange.svg)](#-how-to-apply-for-data-access)
[![Dataset](https://img.shields.io/badge/Instances-7%2C500-green.svg)](#-dataset-overview--statistics)

---

## 📖 Benchmark Overview

Online harm detection is a critical cornerstone of trustworthy AI and content safety governance. However, existing benchmarks primarily focus on isolated single-task violations or explicit lexical insults, leaving models vulnerable to covert, multi-dimensional, and structurally intricate threats.

To address these challenges, we introduce **MDHB (Multi-Dimensional Online Harm Detection Benchmark)**, comprising **7,500** standardized high-quality textual instances spanning four core harm dimensions alongside a benign control group. Constructed through real-world social media corpora curation, LLM-assisted reconstruction, and multi-round human verification, MDHB provides a rigorous benchmark for evaluating structured semantic reasoning and safe alignment in LLMs.

---

## 📊 Dataset Overview & Statistics

The benchmark is organized into two standardized JSON Lines (`.jsonl`) files:

| Split | File Name | Total Samples | Category Breakdown (Balanced) | Description |
| :--- | :--- | :---: | :--- | :--- |
| **Validation** | `Val.jsonl` | **1,250** | 250 samples per category (1:1:1:1:1) | For prompt engineering, hyperparameter tuning & validation |
| **Test** | `Test.jsonl` | **6,250** | ~1,250 samples per category (balanced) | For primary benchmark evaluation and model testing |
| **Total** | | **7,500** | 1,500 samples per top-level category | Full MDHB benchmark suite |

---

## 📂 Data Format & Schema Specification

The dataset is formatted in standard UTF-8 JSON Lines (`.jsonl`). Each line represents a self-contained JSON object containing the following keys:

### Field Definitions
- `id` (`string`): Unique four-digit instance identifier (e.g., `"0001"`, `"0124"`).
- `text` (`string`): The raw text of the social media instance to be evaluated.
- `gt_answers` (`string`): Ground-truth top-level harm classification label (`"Normal"`, `"Toxic"`, `"Sarcastic"`, `"Logical_Fallacy"`, `"Fake"`).
- `sub_label` (`string`): Fine-grained sub-category or specific harm type (empty string `""` for `"Normal"` instances).

### JSON Schema Examples

```json
{
  "id": "0001",
  "text": "Because the soundbite \"survival of the fittest\" was coined to explain evolution to the stupid masses.",
  "gt_answers": "Sarcastic",
  "sub_label": "harmful-sarcasm"
}
```

```json
{
  "id": "0004",
  "text": "white people are the only people hate crime laws are suppose to apply to . any hate crime committed by any other race likely had jewish victims . only way for them to make the list .",
  "gt_answers": "Toxic",
  "sub_label": "Racial Discrimination"
}
```

```json
{
  "id": "0002",
  "text": "Time for my daily scroll through the target app to feel something",
  "gt_answers": "Normal",
  "sub_label": ""
}
```

---

## 🏷️ Fine-Grained Taxonomy Hierarchy

| Top-Level Label (`gt_answers`) | Fine-Grained Sub-Categories (`sub_label`) | Description |
| :--- | :--- | :--- |
| **`Fake`**<br>*(Misinformation)* | • `Political Manipulation`<br>• `Health and Pseudoscience`<br>• `Social Emergencies and Fabrications`<br>• `Other Urban Legends` | Fabricated claims, forged policy statements, health pseudoscience, and emergency hoaxes. |
| **`Toxic`**<br>*(Toxicity)* | • `Threats and Intimidation`<br>• `Incitement to Violence`<br>• `Racial Discrimination`<br>• `Inferiority Language`<br>• `Stereotypes` | Implicit hate speech, targeted intimidation, racial animus, and identity-based derogation. |
| **`Sarcastic`**<br>*(Sarcasm)* | • `harmful-sarcasm` *(Offensive Sarcasm)*<br>• `harmless-sarcasm` *(Non-Offensive Sarcasm)*<br>• `self-depretating-sarcasm` | Pragmatic irony and mockery; includes harmless venting/self-deprecation as **hard negatives**. |
| **`Logical_Fallacy`**<br>*(Logical Fallacies)* | • `slippery slope`<br>• `false dilemma`<br>• `hasty generalization`<br>• `appeal to worse problems`<br>• `appeal to authority`<br>• `appeal to majority`<br>• `appeal to nature`<br>• `appeal to tradition` | Structurally flawed or misleading arguments diverting discourse from valid reasoning. |
| **`Normal`**<br>*(Benign Control)* | • `""` *(Empty string)* | Safe everyday social discourse, factual neutral comments, and benign conversation. |

---

## 🔒 Data Access Policy & Ethical Statement (受控访问策略与伦理声明)

> ### ⚠️ Important Notice / 重要声明
> **English**: Given that MDHB contains real-world instances of online harms, misinformation, offensive language, and covert malicious content, releasing the raw dataset unconditionally to an open public repository presents substantial risks of data abuse, toxic model fine-tuning, and secondary dissemination of harmful content.  
> Therefore, we adopt a **Controlled Access Release Policy**. The dataset is **NOT directly hosted in this public repository**. Access is strictly limited to non-commercial academic research and defensive safety alignment, subject to formal identity verification and a signed **Data Usage Agreement (DUA)**.
> 
> **中文说明**：鉴于 MDHB 包含网络有害言论、虚假信息及其他潜在有害内容，将其无条件公开发布至公开平台可能带来数据滥用和有害内容二次传播的风险。因此，我们采用**数据集受控访问（Controlled Access）**策略：原始数据不会直接公开托管在开放仓库中。申请人需下载并签署《数据使用许可协议》，经作者团队核验申请人学术身份与研究用途后，通过邮件单独发放私有下载链接。

---

## 📝 How to Apply for Data Access (数据集申请流程)

获取 MDHB 数据集访问权限，请按以下 4 个步骤进行申请：

```
┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│ 1. Download Agreement   │ ──> │ 2. Fill & Sign DUA      │ ──> │ 3. Email Application    │ ──> │ 4. Receive Secure Link  │
│ (PDF in repo)           │     │ (Institutional Info)    │     │ (Attach Signed DUA)     │     │ (Within 2-3 Workdays)   │
└─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘
```

### Step 1: Download the Data Usage Agreement (下载协议)
请下载本仓库中的正式协议模板：
- 📄 **PDF 格式（打印并签署）**：[`MDHB_Data_Usage_Agreement.pdf`](./MDHB_Data_Usage_Agreement.pdf)

### Step 2: Fill in Information & Sign (填写信息并签署)
请完整填写协议最后一页的信息表：
- **申请者姓名（Requester's Name）**
- **申请者机构邮箱（Institutional Email）**：建议使用高校或科研院所官方邮箱（如 `@*.edu.cn`、`@university.edu`）
- **职位（Position/Title）**：教师、博士后、博士生、硕士生、科研人员等
- **项目负责人/导师姓名及邮箱（PI / Supervisor's Name & Email）**
- **所属机构与实验室（Affiliation & Department）**
- **具体研究用途说明（Detailed Research Purpose）**：简要说明拟开展的学术课题
- **手写或电子签名（Signature）及日期（Date）**

### Step 3: Send Application Email (发送申请邮件)
将签署后的协议（扫描件/清晰照片/PDF）发送至数据集管理团队邮箱：
- **收件邮箱**：`yutingh1018@gmail.com`
- **邮件主题**：`[MDHB Dataset Application] - <申请者姓名> - <所在机构>`
- **邮件正文模板（可直接复制）**：
  ```text
  Dear MDHB Dataset Team,

  I am writing to formally request access to the MDHB (Multi-Dimensional Online Harm Detection Benchmark) dataset for non-commercial academic research.

  - Applicant Name: [Your Name / 姓名]
  - Affiliation: [Your University / 所在高校或机构]
  - Position: [Faculty / Ph.D. Candidate / Master's Student]
  - Supervisor / PI: [Supervisor's Name and Email / 导师姓名及邮箱]
  - Research Topic: [Briefly describe your project / 研究课题]

  I have read, understood, and agreed to all terms in the MDHB Data Usage Agreement. Please find my signed agreement attached.

  Thank you for your time and consideration.

  Sincerely,
  [Your Name]
  [Your Institutional Email Address]
  ```

### Step 4: Verification & Link Delivery (审核与链接发放)
- 团队将在 **2–3 个工作日** 内完成学术身份与用途核验。
- 审核通过后，私有下载链接（百度网盘 / Google Drive / OneDrive 提取码）将直接发送至您的机构邮箱。

---

## 📜 Citation

如在研究中使用了 MDHB 数据集或参考了本论文方法，请引用我们的 EMNLP 2026 论文：

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

For inquiries, please contact: `yutingh1018@gmail.com`
