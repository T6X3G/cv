# Tuguldur Ganbaatar — CV website

Personal CV site (single static page) plus a printable PDF resume.

```
public/                      site served by nginx
  index.html                 the website (images embedded)
  Tuguldur-Ganbaatar-CV.pdf  resume linked from the "Resume" button
resume/
  cv.html, photo.jpg         source of the PDF
Dockerfile
.github/workflows/pages.yml  publishes public/ to GitHub Pages
```

## Publish (GitHub Pages)

Every push to `main` deploys `public/` via GitHub Actions.
One-time setup: repo **Settings → Pages → Source: GitHub Actions**.
The site is then live at https://t6x3g.github.io/cv/

## Run locally

```sh
docker build -t tuguldur-cv .
docker run -d --name tuguldur-cv -p 3000:80 tuguldur-cv
# open http://localhost:3000
```

## Rebuild the PDF

```sh
# macOS: use "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" instead
google-chrome --headless=new \
  --no-pdf-header-footer --print-to-pdf="public/Tuguldur-Ganbaatar-CV.pdf" \
  "file://$PWD/resume/cv.html"
```
