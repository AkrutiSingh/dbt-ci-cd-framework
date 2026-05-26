🎉 **CI/CD PIPELINE IS WORKING!**

```
✅ Checkout code
✅ Setup Python
✅ Install dependencies
✅ Create profiles.yml
✅ Verify profiles.yml
✅ Run dbt models
✅ Run dbt tests
✅ Generate dbt docs
```

This means every time you push code to GitHub:
- dbt automatically runs all 8 models
- dbt automatically runs all 25 tests
- If any test fails → pipeline fails → bad code blocked

**This is exactly what data teams do at Flipkart, Swiggy, Razorpay, Deloitte!** 🚀

---

## What just happened in simple words

```
You pushed code to GitHub
        ↓
GitHub saw your .github/workflows/dbt_ci.yml
        ↓
GitHub spun up a Ubuntu server
        ↓
Installed Python + dbt automatically
        ↓
Connected to YOUR Snowflake account
        ↓
Ran dbt run → 8 models built ✅
        ↓
Ran dbt test → 25 tests passed ✅
        ↓
Pipeline GREEN ✅
```

All automated. Zero manual work.

---

## Now let's create the README for Project 2

```bash
cd ~/Downloads/dbt-ci-cd-framework
code README.md
```

Paste this:

```markdown
# ⚙️ dbt CI/CD Framework with GitHub Actions

> Automated data pipeline testing and deployment using dbt, Snowflake, and GitHub Actions CI/CD.

---

## 📌 Project Overview

This project implements a **CI/CD pipeline for dbt data models** — automatically running tests and deployments every time code is pushed to GitHub.

Every push triggers:
- `dbt run` → builds all 8 models
- `dbt test` → runs all 25 data quality tests
- `dbt docs generate` → rebuilds documentation

If any test fails → pipeline fails → bad data never reaches production.

---

## 🏗️ CI/CD Flow

```
Developer pushes code to GitHub
            |
            | GitHub Actions triggers automatically
            v
    +---------------------+
    |   Ubuntu Runner     |
    |                     |
    |  1. Install dbt     |
    |  2. Setup Snowflake |
    |     credentials     |
    |  3. dbt run         |
    |  4. dbt test        |
    |  5. dbt docs        |
    +---------------------+
            |
      Pass? -> Deploy  YES
      Fail? -> Block   NO
```

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| dbt | Data transformation + testing |
| Snowflake | Cloud data warehouse |
| GitHub Actions | CI/CD automation |
| Python | Runtime environment |

## 📁 Project Structure

```
dbt-ci-cd-framework/
├── .github/
│   └── workflows/
│       └── dbt_ci.yml
├── dbt_pipeline/
│   ├── dbt_project.yml
│   └── models/
│       ├── staging/
│       │   ├── sources.yml
│       │   ├── stg_orders.sql
│       │   ├── stg_customers.sql
│       │   ├── stg_order_items.sql
│       │   ├── stg_products.sql
│       │   └── stg_order_payments.sql
│       └── marts/
│           ├── schema.yml
│           ├── fct_orders.sql
│           ├── monthly_revenue.sql
│           └── top_products.sql
├── .env.example
├── requirements.txt
└── README.md
```


## ⚙️ GitHub Actions Workflow

```yaml
name: dbt CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  dbt-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
      - run: pip install dbt-snowflake
      - run: create profiles.yml from secrets
      - run: dbt run
      - run: dbt test
      - run: dbt docs generate
```

**Secrets used (stored securely in GitHub):**
- `SNOWFLAKE_ACCOUNT`
- `SNOWFLAKE_USER`
- `SNOWFLAKE_PASSWORD`

---

## ✅ Data Quality Tests

**25 automated tests — all passing on every push**

| Layer | Model | Tests |
|-------|-------|-------|
| Source | orders | unique, not_null on order_id |
| Source | customers | unique, not_null on customer_id |
| Source | products | unique, not_null on product_id |
| Marts | fct_orders | unique, not_null on order_id |
| Marts | monthly_revenue | unique, not_null on order_month |
| Marts | top_products | unique, not_null on category |

---

## 🚀 How to Run Locally

### 1. Clone repository
```bash
git clone https://github.com/AkrutiSingh/dbt-ci-cd-framework.git
cd dbt-ci-cd-framework
```

### 2. Setup environment
```bash
python -m venv venv
source venv/Scripts/activate
pip install -r requirements.txt
```

### 3. Configure credentials
```bash
cp .env.example .env
# Add your Snowflake credentials to .env
```

### 4. Setup profiles.yml
```bash
# Create C:/Users/YOUR_NAME/.dbt/profiles.yml
# with your Snowflake credentials
```

### 5. Run dbt
```bash
cd dbt_pipeline
dbt run
dbt test
dbt docs generate
dbt docs serve
```

---

## 🔐 Security

- Credentials stored as **GitHub Secrets** — never in code
- `.env` file in `.gitignore` — never pushed to GitHub
- `profiles.yml` lives outside project folder — never committed

---

## 💡 What This Proves

| Skill | How Demonstrated |
|-------|-----------------|
| CI/CD thinking | Automated pipeline on every push |
| dbt proficiency | 8 models, 25 tests, documentation |
| Security awareness | GitHub Secrets, .gitignore |
| Data quality | Tests block bad code automatically |
| DevOps basics | GitHub Actions workflow |

---

## 👩‍💻 Author

**Akruti Singh**
- LinkedIn: [linkedin.com/in/akrutisingh](https://linkedin.com/in/akrutisingh)
- GitHub: [github.com/AkrutiSingh](https://github.com/AkrutiSingh)
- Email: akrutisingh1301@gmail.com

---

*Related Project: [End-to-End E-Commerce Analytics Pipeline](https://github.com/AkrutiSingh/ecommerce-analytics-pipeline)*
```

