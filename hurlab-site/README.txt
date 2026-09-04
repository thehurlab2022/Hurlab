HUR Lab — static site
=====================

Six HTML pages. No build step, no framework, no server code.

  index.html         Home
  research.html      Research (Metrology / Cooling / Harvesting)
  people.html        PI, researchers, alumni
  publications.html  Papers, with search and filtering
  projects.html      Funded projects on a timeline
  news.html          Press coverage, grouped by research story

  content/           THE TEXT OF THE SITE — edit these, not the HTML
    people.js  projects.js  publications.js  news.js  research.js

  UPDATING-ko.md     How to run and edit this site (Korean) — read this first

Every page reads its text from the matching file in content/. To change what
the site says, edit one of those five files and re-upload it. The HTML never
needs touching.

Fonts load from Google Fonts. Everything else is self-contained.
