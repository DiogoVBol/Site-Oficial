---
title: Ideias e Resumos
description: |
  This is a fully featured blog that supports categories, 
  tags, series, and pagination.
author: "Diogo Vieri Bolzan"
show_post_thumbnail: true
thumbnail_left: true # for list-sidebar only
show_author_byline: true
show_post_date: true
show_button_links: false
# for listing page layout
layout: list-sidebar # list, list-sidebar, list-grid

# for list-sidebar layout
sidebar: 
  title: Ideias e Resumos!
  description: |
    Essa é um área para compartilhar algumas ideias, resumos e análises!
    
    *"Consultar o estatístico depois que um experimento terminar é muitas vezes apenas pedir a ele para realizar um exame Pós Morte. Ele pode dizer que o experimento morreu."* 
      
      *Sir Ronald Aylmer Fisher, 1938.*
  author: "Diogo Vieri Bolzan"
  categories_link: true
  series_link: false
  tags_link: false
  show_sidebar_adunit: false # show ad container

# set up common front matter for all pages inside blog/
cascade:
  author: "The R Markdown Team @RStudio"
  show_author_byline: true
  show_post_date: true
  show_comments: false # see site config to choose Disqus or Utterances
  # for single-sidebar layout
  sidebar:
    text_link_label: View recent posts
    text_link_url: /blog/
    show_sidebar_adunit: false # show ad container
---

** No content below YAML for the blog _index. This file provides front matter for the listing page layout and sidebar content. It is also a branch bundle, and all settings under `cascade` provide front matter for all pages inside blog/. You may still override any of these by changing them in a page's front matter.**
