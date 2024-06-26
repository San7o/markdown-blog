# My Personal Blog

The blog is currently hosted here:

[https://unavitaunviaggio.netlify.app/](https://unavitaunviaggio.netlify.app/)

### Local Instalation

To set up Jekyll on local machine please follow the official documentation that can be found here -> https://jekyllrb.com/docs/.

To run the theme locally, navigate to the theme directory and run `bundle install` to install the dependencies, then run 
```bash
bundle exec jekyll serve --incremental
```
To build the home page 
```bash 
bundle exec jekyll build
```

### Manual Deployment

Jekyll generates your static site to the **_site** directory by default. You can transfer the contents of this directory to almost any hosting provider to get your site live.

### Netlify

This theme is prepared to be hosted on [Netlify](https://www.netlify.com/). All you need to do is create a new private repository on GitHub or GitLab. Upload the theme to the repository and link your repo to Netlify. Please check [this link](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/#step-2-link-to-your-github) with the step by step guidelines.
