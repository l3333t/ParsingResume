```md
# Job-Matcher

## 🔹 Project Overview

**Job-Matcher** is an NLP-based tool that analyzes **resumes and job descriptions** to identify key sections and keywords. It enables efficient **job-to-candidate matching** by extracting relevant information from both resumes and job postings.

## 🚀 Getting Started

### 📌 Requirements
- Python 3
- Spacy (≥ 2.2.3)
- Spacy language model: `en_core_web_sm`

### 🔧 Installation

If you haven’t installed Spacy and its language model, run:

```bash
pip install -U spacy  
python -m spacy download en_core_web_sm  
```

## ⚙️ Features & Usage

### 📍 Resume & Job Description Parsing

Both **Resume** and **Position** objects use:
- `text`: Resume or job posting as a string
- `language`: Language of the text (default: `"en"`)
- `model`: Spacy model (default: `"en_core_web_sm"`)
- `options`: Custom parsing settings

By default, only **global keywords** are extracted, but additional options can be enabled.

### 📌 Basic Example

```python
from resume import Resume

resume_text = "Your resume content here..."
resume = Resume(text=resume_text)
# Extracted keywords are stored in resume.keywords (dictionary format)
```

### 🔍 Extracting Domain-Specific Keywords

To search for specific industry-related keywords:

```python
from options import Options
from resume import Resume

options = Options(domain_keywords=["Python", "JavaScript", "Agile", "Docker"])
resume = Resume(text=resume_text, options=options)
# Matched domain-specific keywords are stored in resume.domain_keywords
```

### 🏷️ Identifying Sections

To extract specific sections (e.g., Experience, Skills, Education):

```python
from options import Options
from resume import Resume
from sections import Experience, Skills, Education

options = Options(sections=[Experience, Skills, Education])
resume = Resume(text=resume_text, options=options)
# Extracted sections are stored in resume.sections
```

Check if a section exists:

```python
resume.has_section("education")
```

### 📊 Resume & Job Matching

Compare **keywords** between a resume and a job posting:

```python
resume = Resume(text=resume_text)
position = Position(text=position_text)

matching_general, missing_general = resume.compare_global_keywords(position)
```

Compare **domain-specific keywords**:

```python
options = Options(domain_keywords=["JavaScript", "C++", "HTML5"])
resume = Resume(text=resume_text, options=options)
position = Position(text=position_text, options=options)

matching_domain, missing_domain = position.compare_domain_keywords(resume)
```

## 🔜 Future Enhancements

- Linking keywords to specific sections  
- Machine Learning model for entity extraction (e.g., years of experience, skill levels)  

---

🛠 **Contributions are welcome!** Feel free to fork and improve the project.  
📧 For questions, contact the repository maintainer.

panaguzhiyev@gmail.com
```
