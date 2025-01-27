---
title: Home
layout: home
---

# Tests for Just the Docs
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>


[Just the Docs] is a [remote theme] for use with the static website generator [Jekyll].
The theme is responsive, easily customizable, and hosted on [GitHub Pages].
It supports documentation pages, but (currently) not blogs.

We are developing this website to test various features of Just the Docs.
The source code of the web pages illustrates how to use the tested features,
and the published pages show their resulting effects.
See the [Just the Docs website] for the main documentation of the theme.

The rest of this page explains how to create a website using Just the Docs
so that we can build and preview the site locally before publishing it on GitHub Pages.
The explanation aims to be as simple as possible;
it could be regarded as a test of the guidance for [getting started]
shown on the current theme home page (which can confuse users new to Jekyll).

Note that some of the files listed below have been updated for use on this 
Just the Docs Tests website
To get started smoothly, copy the listed code from this webpage -- _not_ from
the files themselves.

## Using the v0.3.3 release of Just the Docs

1.  Install Bundler:

    ```sh
    gem install bundler
    ```
    
1.  Create a repository `my-github-username/my-website` on GitHub, and make a local copy.

    N.B. You do _not_ need to clone or download the code of the theme `just-the-docs`
    for building your website!
    
1.  Create `.../my-website/.gitignore`:

    ```
    _site
    .sass-cache
    .jekyll-cache
    .jekyll-metadata
    vendor
    ```

1. Create `.../my-website/_config.yml`:

    ```yml
    title: My website
    remote_theme: just-the-docs/just-the-docs@v0.3.3
    plugins:
      - jekyll-remote-theme
      - jekyll-default-layout
    aux_links:
      My website on GitHub:
        - //github.com/my-github-username/my-website
    permalink: pretty
    ```

1.  Create `.../my-website/Gemfile`:

    ```ruby
    source 'https://rubygems.org'
    gem "jekyll", "~> 3.8.7"
    gem "jekyll-remote-theme"
    gem "just-the-docs", "0.3.3"
    ```

1.  Create `.../my-website/index.md`:

    ```md
    ---
    title: Home
    ---

    # My home page
    
    ...
    ```

1.  Run `bundle install`.
    The log includes the following lines:

    ```
    Using jekyll 3.8.7
    Using just-the-docs 0.3.3
    ```

1.  Run `bundle exec jekyll serve`.
    The log depends partly on some local details, elided below:

    ```
    Configuration file: .../my-website/_config.yml
                Source: .../my-website
           Destination: .../my-website/_site
     Incremental build: disabled. Enable with --incremental
          Generating... 
          Remote Theme: Using theme just-the-docs/just-the-docs
                        done in ... seconds.
     Auto-regeneration: enabled for '.../my-website'
        Server address: http://127.0.0.1:4000
      Server running... press ctrl-c to stop.
    ```

1.  Browse your website at `localhost:4000`.

## Using RC v0.4.0.rc1 of Just the Docs

The release tag `@v0.3.3` used in `_config.yml` above ensures that Jekyll uses
the current release (version 0.3.3) of the theme when it builds your website.

To switch to using the current RC for version 0.4.0, replace `@v0.3.3`
by `@v0.4.0.rc1` in `_config.yml`:

```yml
remote_theme: just-the-docs/just-the-docs@v0.4.0.rc1
```

_and_ make the following change to the `gem` specification for `just-the-docs`
in the `Gemfile`:

```ruby
gem "just-the-docs", "v0.4.0.rc1"
```

## Using Jekyll 4 for building locally

GitHub Pages (probably) uses Jekyll version 3.8.7 to build Just the Docs websites.
The gem version specification `"~> 3.8.7"` ensures that you will
install and use the same version of Jekyll to build websites locally
(assuming that you're using Bundler).

To use Jekyll 4 _locally_, you can simply replace `"~> 3.8.7"` by `"~> 4.2"`
in your `Gemfile`.
Just the Docs aims to produce the same results when using Jekyll version 3.8.7
and 4.2.2.
Jekyll 4 is considerably faster than Jekyll 3.

Unfortunately, to use Jekyll 4 for building your website _on GitHub Pages_
is not quite so straightforward: you need to specify it using GitHub Actions.[^gh-actions]

[^gh-actions]:
    GitHub has recently introduced simple workflows for [GitHub Actions] to 
    build websites on GitHub Pages with Jekyll 4.

## Reporting issues

To report an apparent mistake on this website,
check whether it has already been reported at [Just the Docs Tests Issues],
and otherwise submit it there as a new issue.

To report an issue with using version 0.3.3 of Just the Docs,
check whether it has already been reported at [Just the Docs Issues] by searching
both open and closed issues.
If it has not been reported,
check also whether it is still an issue when using version 0.4.0.rc1.
If it is, submit it at [Just the Docs Issues] as a new issue,
mentioning that it is present in both `v0.3.3` and `v0.4.0.rc1`.

{% include links.md %}
