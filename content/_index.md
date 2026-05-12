---
# Leave the homepage title empty to use the site title
title: ''
date: 2022-10-24
type: landing

design:
  spacing: '4rem'

sections:
  - block: resume-biography-3
    content:
      username: admin
      text: ''
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: 'Professional Summary'
        education: ''
        interests: ''
    design:
      css_class: hbx-bg-gradient
      avatar:
        size: medium
        shape: circle
  - block: collection
    id: publications
    content:
      title: Publications
      text: ''
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      view: citation
  - block: collection
    id: projects
    content:
      title: Projects
      text: ''
      filters:
        folders:
          - project
    design:
      view: article-grid
      fill_image: false
      columns: 3
      show_date: false
      show_read_time: false
      show_read_more: false
  - block: resume-experience
    id: experience
    content:
      username: admin
---
