# Databricks Training Environment (Free)

Use this guide to create a no-cost Databricks workspace for learning and hands-on practice.

## 1) Prerequisites

- A personal email address (not a corporate account with strict admin policies).
- A web browser.
- Optional: a GitHub account if you want to store notebooks externally.

## 2) Create a Free Databricks Account

Databricks currently provides two free starting paths:

### What will you use Databricks for?

Get started for free. No credit card required.

### For work

- Free for 14 days with up to $400 credits*.
- Work with any data on any cloud.
- Full platform with enterprise Terms and SLAs.

### For personal use

- Free forever.
- Learn and build with exploratory datasets.
- Core features with personal-use limits, Terms and SLAs.

*[Terms apply](https://www.databricks.com/product/pricing) for credits.

Setup steps:
1. Go to the Databricks sign-up page.
2. Choose either For work or For personal use based on your goal.
3. Register with your email and verify your account.
4. Sign in to your new workspace.

## 3) Initial Workspace Setup

1. In the left navigation, open Workspace.
2. Create a new folder, for example: training.
3. Inside that folder, create a new notebook.
4. Select Python as the default language for beginner-friendly examples.

Recommended structure:
- training/01-basics
- training/02-sql
- training/03-data-engineering
- training/04-ml-intro

## 4) Attach or Start Compute

Your available compute depends on the path you selected.

- For work: temporary trial credits with broader platform access.
- For personal use: free access with personal-use limits.

1. Open your notebook.
2. Choose Select compute (or similar).
3. If prompted, start the default compute resource.
4. Wait until status shows Running.

Tips to stay within free limits:
- Stop compute when you are done.
- Run small datasets for practice.
- Avoid long-running jobs.

## 5) Load Sample Data

You can start quickly with built-in sample datasets or upload small files.

Option A: built-in sample data
1. Open Catalog or Data Explorer.
2. Browse sample datasets available in your workspace.
3. Query them directly from a notebook using SQL or PySpark.

Option B: upload your own CSV
1. Open Catalog or Data and choose Add data / Upload file.
2. Upload a small CSV file.
3. Save as a table in a personal schema.

## 6) First Validation Checks

Run these checks in a notebook to confirm your environment is ready:

1. Spark is available:
	 - Run a simple Spark command, for example creating a small DataFrame.
2. SQL works:
	 - Run a SELECT query against a sample table.
3. Storage and permissions work:
	 - Save a small result as a table and read it back.

If all three checks pass, your training environment is ready.

## 7) Common Free-Tier Issues

- Compute does not start:
	- Retry after a few minutes.
	- Create a new notebook and re-attach compute.
- Permission errors on table creation:
	- Use your personal default catalog/schema for training.
- Session timeout:
	- Keep notebooks saved in Workspace or Git-backed repos.

## 8) Suggested Next Steps

- Practice notebook fundamentals: cells, markdown, and visualizations.
- Learn Spark DataFrame basics (load, transform, write).
- Practice SQL on sample datasets.
- Build one small end-to-end pipeline and document it in your training folder.

## Quick Checklist

- Account created and verified
- Workspace folder created
- Notebook created
- Compute attached and running
- Sample data accessible
- Basic Spark + SQL checks passed
