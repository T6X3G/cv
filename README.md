# Tuguldur Ganbaatar — CV website

Personal CV site (single static page) plus a printable PDF resume.

```
public/                      site served by nginx
  index.html                 the website (images embedded)
  Tuguldur-Ganbaatar-CV.pdf  resume linked from the "Resume" button
resume/
  cv.html, photo.jpg         source of the PDF
Dockerfile
```

## Run locally

```sh
docker build -t tuguldur-cv .
docker run -d --name tuguldur-cv -p 3000:80 tuguldur-cv
# open http://localhost:3000
```

## Rebuild the PDF

```sh
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new \
  --no-pdf-header-footer --print-to-pdf="public/Tuguldur-Ganbaatar-CV.pdf" \
  "file://$PWD/resume/cv.html"
```
