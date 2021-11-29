---
title: Just the Class
layout: default
nav_exclude: true
seo:
  type: Course
  name: Just the Class
---

# {{ site.tagline }}
{: .mb-2 }
{{ site.description }}
{: .fs-6 .fw-300 }

{% if site.announcements %}
{{ site.announcements.last }}
[Announcements](announcements.md){: .btn .btn-outline .fs-3 }
{% endif %}

## Just the Class

Just the Class is a GitHub Pages template developed for the purpose of quickly deploying course websites. In addition to serving plain web pages and files, it provides a boilerplate for:

- a [course calendar](calendar.md),
- a [staff](staff.md) page,
- and a weekly [schedule](schedule.md).

Just the Class is a set of customizations on top of the popular [Just the Docs](https://github.com/pmarsceill/just-the-docs) theme, which provides a robust and thoroughly-tested foundation that makes it easy to extend for your own special use cases. These foundational features include:

- automatic [navigation structure](https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/),
- instant, full-text [search](https://pmarsceill.github.io/just-the-docs/docs/search/) and page indexing,
- and a small but powerful set of [UI components](https://pmarsceill.github.io/just-the-docs/docs/ui-components) and authoring [utilities](https://pmarsceill.github.io/just-the-docs/docs/utilities).

## Just the Class ---> Canvas
This repo contains a hurriedly hacked-together plugin that uses the Canvas LMS REST API to push content from Jekyll into Canvas. It is currently configured to:
* Update the front page in Canvas to match the front page index.md
* Create a "module" in Canvas for each lecture (the files in the `lectures/` directory). For each module that has lessons or tutorials linked, it will add a module item that links to that same content
* Create and update assignments that match the assignments here

It does not do bi-directional sync: any updates made to this content in Canvas will be overwritten. It does not delete data from Canvas if it's deleted there.

To use it, set the following environmental variables:
* `CANVAS_TOKEN` - Generate one by opening Canvas then going to Account - Settings - New Access Token
* `CANVAS_COURSE_ID` - Found in the URL of your course on Canvas, e.g. https://northeastern.instructure.com/courses/86615 -> course id is 86615
* `CANVAS_BASE_URL` - The base URL where Canvas is installed, e.g. in https://northeastern.instructure.com/courses/86615 it's https://northeastern.infrastructure.com/
* `JEKYLL_NO_BUNDLER_REQUIRE=true` - For a variety of reasons, it's a bad idea apparently to include a plugin directly in the _plugins directory. After a semester of usage, if it works OK, I will probably come back to this, clean up rough edges, and publish a gem. Until then, if you don't set this variable, Jekyll will ignore my Canvas plugin
