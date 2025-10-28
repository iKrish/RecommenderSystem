# GitLab Setup & MyBinder Deployment Guide

## Step 1: Initialize Git Repository

```bash
# Navigate to project folder
cd "c:\Drexel\Coding Exp\Recommeder System\RecommenderSystem-A2"

# Initialize Git
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Movie Recommender System A2"
```

## Step 2: Create GitLab Repository

1. Go to your university GitLab: **https://gitlab.drexel.edu** (or your university's GitLab URL)
2. Click **"New Project"**
3. Choose **"Create blank project"**
4. Fill in details:
   - **Project name**: `RecommenderSystem-A2`
   - **Visibility**:  **Public** (required for MyBinder)
   - **Initialize with README**:  Uncheck (we already have one)
5. Click **"Create project"**

## Step 3: Push to GitLab

```bash
# Add GitLab as remote (replace YOUR_GITLAB_USERNAME)
git remote add origin https://gitlab.drexel.edu/YOUR_GITLAB_USERNAME/RecommenderSystem-A2.git

# Push to GitLab
git branch -M main
git push -u origin main
```

**Example**:
```bash
git remote add origin https://gitlab.drexel.edu/abc123/RecommenderSystem-A2.git
```

## Step 4: Update README with Your GitLab Username

1. Open `README.md` in the GitLab web interface
2. Click **"Edit"**
3. Find this line (near the top):
   ```markdown
   [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gl/<YOUR_GITLAB_USERNAME>%2FRecommenderSystem-A2/HEAD?labpath=movie-recommender-system-a2.ipynb)
   ```
4. Replace `<YOUR_GITLAB_USERNAME>` with your actual username
   - Example: `abc123` becomes:
   ```markdown
   [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gl/abc123%2FRecommenderSystem-A2/HEAD?labpath=movie-recommender-system-a2.ipynb)
   ```
5. Also update the clone URL in "Quick Start" section:
   ```bash
   git clone https://gitlab.drexel.edu/abc123/RecommenderSystem-A2.git
   ```
6. Update "Contact & Submission" section with your name and course info
7. Click **"Commit changes"**

## Step 5: Test MyBinder Deployment

1. Click the **"launch binder"** badge in your README
2. MyBinder will start building the environment (~3-5 minutes first time)
3. Wait for JupyterLab to load
4. Open `movie-recommender-system-a2.ipynb`
5. Click **"Run"**  **"Run All Cells"**
6. Verify all cells execute successfully

### Troubleshooting MyBinder

**Issue**: "Failed to build repository"
-  Ensure repository is **PUBLIC** (Settings  General  Visibility  Public)
-  Check `requirements.txt` exists in root folder
-  Verify all dependencies are valid package names

**Issue**: "Notebook not found"
-  Check the `labpath` parameter in the badge URL matches your notebook filename exactly
-  Ensure notebook is in the root folder (not in subdirectory)

**Issue**: Cells fail with "FileNotFoundError"
-  Verify `raw_data/` folder exists with all 3 CSV files
-  Check `DATA_DIR = Path('./raw_data')` in configuration cell

## Step 6: Share with Evaluator

**Option 1: GitLab Repository Link**
```
https://gitlab.drexel.edu/YOUR_GITLAB_USERNAME/RecommenderSystem-A2
```

**Option 2: Direct MyBinder Link**
```
https://mybinder.org/v2/gl/YOUR_GITLAB_USERNAME%2FRecommenderSystem-A2/HEAD?labpath=movie-recommender-system-a2.ipynb
```

**Recommended**: Share both links:
- GitLab link: For code review and documentation
- MyBinder link: For one-click execution

## Verification Checklist

Before submission, verify:

- [ ] GitLab repository is **PUBLIC**
- [ ] All files pushed successfully (notebook, README, requirements.txt, raw_data/)
- [ ] README.md badge URL updated with your username
- [ ] MyBinder badge works (click and test)
- [ ] Notebook runs successfully on MyBinder ("Run All" completes without errors)
- [ ] Final metrics visible in notebook output (Precision, Recall, nDCG, AUC)
- [ ] Contact information updated in README

## Expected Evaluator Experience

1. Click MyBinder badge  Wait 2-3 min for environment build
2. JupyterLab opens  Open notebook automatically
3. Click "Run All"  Wait 2-3 min for execution
4. Review results:
   -  Test Precision@10: ~0.20%
   -  Test Recall@10: ~1.13%
   -  Test nDCG@10: ~0.0055
   -  Test AUC: ~0.50
   -  Sample recommendations for 3 users

**Total time**: ~5-6 minutes from badge click to viewing results

---

## Alternative: Manual Git Commands (PowerShell)

If you prefer command-line setup:

```powershell
# Navigate to project
cd "c:\Drexel\Coding Exp\Recommeder System\RecommenderSystem-A2"

# Initialize Git
git init

# Configure user (first time only)
git config user.name "Your Name"
git config user.email "your.email@drexel.edu"

# Stage all files
git add .

# Commit
git commit -m "Initial commit: Movie Recommender System A2"

# Add remote (replace YOUR_GITLAB_USERNAME)
git remote add origin https://gitlab.drexel.edu/YOUR_GITLAB_USERNAME/RecommenderSystem-A2.git

# Push to GitLab
git branch -M main
git push -u origin main
```

---

## Quick Reference: Important URLs

| Service | URL Pattern | Your URL (fill in) |
|---------|-------------|-------------------|
| **GitLab Repo** | `https://gitlab.drexel.edu/USERNAME/RecommenderSystem-A2` | _________________ |
| **MyBinder** | `https://mybinder.org/v2/gl/USERNAME%2FRecommenderSystem-A2/HEAD?labpath=movie-recommender-system-a2.ipynb` | _________________ |
| **Clone URL** | `git clone https://gitlab.drexel.edu/USERNAME/RecommenderSystem-A2.git` | _________________ |

---

**Last Updated**: October 27, 2025
