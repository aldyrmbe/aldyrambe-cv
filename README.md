# CV Repository

Automated CV generation using Markdown

## Quick Setup Guide

1. Go to "Actions" tab in your repository
2. You should see "Build CV PDF" workflow running
3. Wait for it to complete (green checkmark)
4. Click on the workflow run
5. Download the artifact "cv-pdf" to get your PDF

## 📥 Downloading Your CV PDF

From Workflow Artifacts

1. Go to "Actions" tab
2. Click on the latest successful workflow run
3. Scroll down to "Artifacts" section
4. Download "cv-pdf"

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
  --pdf-engine=pdflatex \
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

**Generate PDF locally:**

```bash
pandoc cv.md -o cv.pdf \
  --pdf-engine=pdflatex \
  -V geometry:margin=1in \
  -V fontsize=11pt \
  -V documentclass=article \
  -H header.tex
```
