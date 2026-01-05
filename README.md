# CV Repository

Automated CV generation using Markdown and GitHub Actions.

## 🚀 Quick Setup Guide

### Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com) and click "New Repository"
2. Name it `cv` or `resume`
3. Set to **Public** or **Private** (your choice)
4. **Do NOT** initialize with README (we'll create it)
5. Click "Create repository"

### Step 2: Clone Repository Locally

```bash
git clone https://github.com/YOUR_USERNAME/cv.git
cd cv
```

### Step 3: Create Directory Structure

```bash
# Create the GitHub Actions directory
mkdir -p .github/workflows

# Create files
touch cv.md
touch .github/workflows/build-cv.yml
touch README.md
touch .gitignore
```

### Step 4: Add Files

Copy the content from the artifacts into these files:

1. **cv.md** - Your resume content in markdown
2. **.github/workflows/build-cv.yml** - GitHub Actions workflow
3. **README.md** - This file
4. **.gitignore** - See below

### Step 5: Create .gitignore

```bash
cat > .gitignore << 'EOF'
# PDF output (optional - remove this line if you want PDF committed)
# cv.pdf

# System files
.DS_Store
Thumbs.db

# Editor files
*.swp
*.swo
*~
.vscode/
.idea/

# Temporary files
*.tmp
*.bak
EOF
```

### Step 6: Initial Commit and Push

```bash
git add .
git commit -m "Initial commit: Add CV in Markdown with GitHub Actions"
git push -u origin main
```

**Note:** If your default branch is `master` instead of `main`, use:

```bash
git push -u origin master
```

### Step 7: Enable GitHub Actions (if needed)

1. Go to your repository on GitHub
2. Click "Actions" tab
3. If prompted, click "I understand my workflows, go ahead and enable them"

### Step 8: Verify Workflow

1. Go to "Actions" tab in your repository
2. You should see "Build CV PDF" workflow running
3. Wait for it to complete (green checkmark)
4. Click on the workflow run
5. Download the artifact "cv-pdf" to get your PDF

## 📥 Downloading Your CV PDF

### Method 1: From Workflow Artifacts

1. Go to "Actions" tab
2. Click on the latest successful workflow run
3. Scroll down to "Artifacts" section
4. Download "cv-pdf"

### Method 2: Auto-commit to Repository (Already Enabled)

The workflow automatically commits `cv.pdf` back to your repository. Just pull the latest changes:

```bash
git pull
```

### Method 3: Create a Release (For Versioning)

```bash
# Create and push a tag
git tag v1.0.0
git push origin v1.0.0
```

The PDF will be attached to the release automatically.

## 🔄 Updating Your CV

1. Edit `cv.md` file locally
2. Commit and push:
   ```bash
   git add cv.md
   git commit -m "Update work experience"
   git push
   ```
3. GitHub Actions will automatically generate the new PDF
4. Download from Actions artifacts or pull the committed PDF

## 🎨 Customizing PDF Appearance

Edit the pandoc command in `.github/workflows/build-cv.yml`:

```yaml
pandoc cv.md -o cv.pdf \
  --pdf-engine=xelatex \
  -V geometry:margin=0.75in \      # Adjust margins
  -V fontsize=10pt \                # Change font size
  -V mainfont="Arial" \             # Change font
  -V documentclass=article
```

## 🧪 Testing Locally (Optional)

Install Pandoc on your machine:

**macOS:**

```bash
brew install pandoc
brew install --cask basictex
```

**Ubuntu/Debian:**

```bash
sudo apt-get update
sudo apt-get install pandoc texlive-latex-base texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra
```

**Windows:**
Download from [pandoc.org](https://pandoc.org/installing.html) and install MiKTeX

**Generate PDF locally:**

```bash
pandoc cv.md -o cv.pdf --pdf-engine=xelatex -V geometry:margin=1in
```

## ✅ ATS Testing

Test your PDF with these free ATS scanners:

- [Jobscan](https://www.jobscan.co/)
- [Resume Worded](https://resumeworded.com/)
- [ZipJob Resume Scanner](https://www.zipjob.com/resume-scanner)

## 🔧 Troubleshooting

### Workflow fails with "Permission denied"

1. Go to repository Settings > Actions > General
2. Under "Workflow permissions", select "Read and write permissions"
3. Click "Save"

### PDF not being committed

Check if the last step in the workflow succeeded. If it shows "nothing to commit", the PDF might already be up to date.

### PDF formatting looks wrong

- Ensure you're using simple Markdown (headers, lists, bold)
- Avoid complex tables or nested formatting
- Test locally with pandoc first

## 📝 Tips

- Keep one version in `main` branch
- Create branches for different job applications
- Use tags for versioning (v1.0, v1.1, etc.)
- Add different CV versions (cv-software.md, cv-data.md)
- Keep bullet points under 2 lines for better readability

## 📄 License

This is your personal CV - no license needed!
