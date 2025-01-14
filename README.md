# MDAnalysis Web Site #

The home page [www.mdanalysis.org](https://www.mdanalysis.org) is maintained as
a [GitHub pages](https://pages.github.com) site. The home page is also
accessible as [mdanalysis.github.io](https://mdanalysis.github.io).

Pages are generated 

## General page authoring guide ##

- use [GitHub-flavored Markdown](https://github.github.com/gfm/)
- use utf-8 encoding
- The top-level heading (h1) is set by the *title:* attribute in the
  front matter of each page.
- In-text headings start at h2, i.e., `## heading title ##` in
  Markdown. There should *not be any h1 headings inside the page*.
  
For further notes see [Web development](#web-development) below.


## Blog [mdanalysis.org/blog](https://www.mdanalysis.org/blog) ##

Check out the repository, edit the pages under `_posts`, and push
commits. The published pages are on the *master* branch.

Blog posts should be placed under `_posts`. These should have names
according to:

    YEAR-MONTH-DAY-title.md

where `YEAR` is a four-digit number, and `MONTH` and `DAY` are both two-digit
numbers. Each post should have a header with:

    ---
    layout: post
    title: The title of this post
    ---

in order for it to be picked up by the paginator. The `blog` directory should
not be touched, as this is only here to set the paginator.

* The `_site` directory is generated by Jekyll on the GitHub server side and
  should not be included in commits.
* You can sign posts with your
  [@mention](https://help.github.com/articles/mentions-on-github-pages/)
  and it will link to your GitHub profile.
* If the date on a post is in in the future at the time of the commit,
  it will not be built *and will not appear* (until the next commit on
  or after the time of the post).


## Web development ##

Check out the repository, edit the pages, and push commits. The
published pages are on the *master* branch.

We are using the minimalist [Hyde](https://github.com/poole/hyde) theme for
[Jekyll](https://help.github.com/articles/using-jekyll-with-pages/).

Additional static pages go under `pages`. If they have the layout type "page"
they will be automatically included in the sidebar. We've left the static
"about" page is left at the top level.


### Mark-up format: Markdown ###

The GitHub pages can either use HTML or
[markdown](http://daringfireball.net/projects/markdown/) as processed by
[Jekyll](https://help.github.com/articles/using-jekyll-with-pages/).

The actual markdown processor is
[kramdown](http://kramdown.gettalong.org) so it parses more than basic
markdown --- see the
[kramdown syntax](http://kramdown.gettalong.org/syntax.html),
including MathJax.

### Images ###

Drop images into the `public/images` directory and include them like

```html
  <img src="{{site.images}}/imagename.png"
   style="float: right" alt="alternative text" width="30%"/>
   ```

or use Markdown
```markdown
![alternative text]({{site.images}}/imagename.png)
```


### Notes on using Jekyll ###

For links between pages to work, generate absolute links with `site.baseurl`
liquid tag:

```
[see citations]({{ site.baseurl }}/pages/citations
```

The example will link to the file `/pages/citations`. Also note that one does
not need spaces between the configuration variable and the curly braces (i.e.
`{{ site.baseurl }}/` as typical seen), so I avoid them to prevent the editor
breaking the line inside the curly braces (which upsets Jekyll greatly).

We define additional variables in `_config.yml` and use them with liquid tags.
In particular, the sidebar `_includes/sidebar.html` is configured with
additional links that are all stored in the config file.


### Local testing ###

To locally test that your edits look ok before pushing them, install
[Jekyll](https://help.github.com/articles/using-jekyll-with-pages/) as
described in the docs.

#### Build site locally ####

To run Jekyll in a way that matches the GitHub Pages build server, run `Jekyll`
with `Bundler`. Use the command

    bundle exec jekyll serve

in the root of your repository (after switching to the gh-pages branch for
project repositories), and your site should be available at
<http://localhost:4000>. For a full list of Jekyll commands, see the Jekyll
documentation.

**NOTE:**

In case the you get an error that a javascript environment is missing. Install a
javascript environment like `nodejs` from your distribution repositories.

#### Updating the github-pages plugin ####

If you try out new functionality or plugins locally and you get error
messages then try to
[update the github-pages plugin](https://help.github.com/articles/setting-up-your-pages-site-locally-with-jekyll/#keeping-your-site-up-to-date-with-the-github-pages-gem)
with


    bundle update github-pages
