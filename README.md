# UniSA Data Visualization Portfolio Template

This repository provides a template for creating a personalized portfolio website using [Quarto](https://quarto.org/) with University of South Australia branding through the [brand.yml](https://posit-dev.github.io/brand-yml/) framework. The template includes support for blog posts, shinylive R applications, and automatic deployment through GitHub Pages.

## Prerequisites

Before getting started, ensure you have:

1. [R](https://cran.r-project.org/) (version 4.3.0 or higher)
2. [RStudio](https://posit.co/download/rstudio-desktop/) (recommended) or [VS Code with R extensions](https://code.visualstudio.com/)
3. [Quarto](https://quarto.org/docs/get-started/) (version 1.6 or higher)
4. A [GitHub](https://github.com/) account
5. Git installed on your computer

## Step 1: Create Your Repository

1. Visit the [template repository](https://github.com/coatless-brand-yml/quarto-unisa) - this includes an unofficial implementation of the UniSA brand using brand yml 
2. Click the "Use this template" button at the top of the page
3. Select "Create a new repository" 
4. Name your repository (e.g., `portfolio`, `data-viz-portfolio`, or `firstname-lastname-portfolio`)
   - We recommend keeping it simple and descriptive
5. Choose repository visibility:
   - **Public**: Visible to everyone (default option for GitHub Pages)
   - **Private**: Only visible to you and collaborators. This requires the [GitHub Student Developer Pack](https://education.github.com/pack), which you can get for free by registering with [GitHub Education](https://education.github.com/)
6. Click "Create repository from template"

## Step 2: Clone Your Repository

Clone your new repository to your local machine using one of these methods:

**Option A: Using RStudio**

1. In RStudio, go to File → New Project → Version Control → Git
2. Paste your repository URL (e.g., `https://github.com/yourusername/portfolio.git`)
3. Choose a directory where you want to save the project
4. Click "Create Project"

**Option B: Using command line**

```bash
git clone https://github.com/yourusername/portfolio.git
cd portfolio
```

## Step 3: Customize Your Portfolio

### Update Personal Information

1. Edit `index.qmd` to include your personal information:
   - Change the title
   - Uncomment and add your profile picture
   - Update social media links
   - Add a bio or introduction

```yaml
---
title: "Jane Doe"
image: profile.jpg  # Add your profile image to the project directory
about:
  template: jolla
  links:
    - icon: twitter
      text: Twitter
      href: https://twitter.com/yourusername
    - icon: linkedin
      text: LinkedIn
      href: https://linkedin.com/in/yourusername
    - icon: github
      text: Github
      href: https://github.com/yourusername
---

I'm a data visualization student at the University of South Australia with a passion for...
```

### Customize the Navigation

Edit `_quarto.yml` to customize your website's navigation and settings:

```yaml
website:  
  repo-url: https://github.com/yourusername/portfolio
  repo-actions: [edit, issue]
  title: "Your Name's Portfolio"
  navbar:
    right:
      - text: "Projects"
        href: projects.qmd
      - text: "Blog"
        href: blog.qmd
      - shinylive-app.qmd
      - about.qmd
      - icon: github
        href: https://github.com/yourusername
```

## Step 4: Add Your Projects

1. Create a new file called `projects.qmd` in the root directory
2. Structure it to showcase your data visualization projects:

```yaml
---
title: "Data Visualization Projects"
---

## Project 1: [Title]

![Project Image](images/project1.png)

Brief description of your project, methodologies used, and key findings.

[View Project](https://github.com/yourusername/project1)

## Project 2: [Title]

...
```

## Step 5: Create Blog Posts

1. Create a `posts` directory if it doesn't already exist
2. Inside this directory, create subdirectories for each post (e.g., `posts/first-post/`)
3. In each post directory, create an `index.qmd` file with your content:

```yaml
---
title: "My First Data Visualization Analysis"
description: "Exploring patterns in [dataset]"
author: "Your Name"
date: "2023-05-13"
categories: [R, Data Visualization, Analysis]
image: "thumbnail.png"
---

## Introduction

Describe your analysis here...

```

## Step 6: Add Shinylive Applications

You can include interactive Shiny applications using shinylive:

1. Ensure you have the shinylive package installed:

```r
install.packages("shinylive")
```

2. Add any R package dependencies to the `DESCRIPTION` file under the `Imports:` section:

```
Imports: 
    shiny,
    ggplot2,
    dplyr,
    shinylive
```
This ensures that all required packages are automatically installed when your website is built on GitHub.

3. Create a new `.qmd` file for your app or edit the existing `shinylive-app.qmd`
3. Use the following syntax to embed a Shiny app:

````md
---
title: "My Interactive Visualization"
format:
  html:
    embed-resources: false
    resources: 
      - shinylive-sw.js
      - shinylive.js
filters:
  - shinylive
---

```{shinylive-r}
#| standalone: true

library(shiny)
library(ggplot2)

ui <- fluidPage(
  titlePanel("My Interactive Visualization"),
  sidebarLayout(
    sidebarPanel(
      # Add your input controls here
    ),
    mainPanel(
      # Add your output plots here
    )
  )
)

server <- function(input, output, session) {
  # Server logic here
}

shinyApp(ui, server)
```
````

## Step 7: Preview Your Website Locally

1. In RStudio, open the `index.qmd` file (not the `_quarto.yml` file)
2. Click the "Render" button or run this command in the terminal:

```bash
quarto preview
```

This will start a local server and open your website in a browser. Changes you make will be automatically updated in real-time.

## Step 8: Deploy Your Website on GitHub Pages

1. Push your changes to GitHub:

```bash
git add .
git commit -m "Update portfolio content"
git push
```

2. Enable GitHub Pages:
   - Go to your repository on GitHub
   - Click on "Settings" → "Pages"
   - Under "Source", select "GitHub Actions"
   - **Important**: Make sure the "Enforce HTTPS" option is checked. This is required for Shinylive applications to work properly
   - Your site will be published automatically through the built-in GitHub Action workflow

3. Your site will be available at: `https://yourusername.github.io/repository-name/`

## Customizing the Brand YML Theme

The template uses UniSA's brand colors and typography. If you want to customize further:

1. Review the `_brand.yml` file to understand how the theming works
2. You can adjust colors, typography, and other brand elements as needed
3. Reference the [brand.yml documentation](https://posit-dev.github.io/brand-yml/) for detailed options

## Additional Resources

- [Quarto Documentation](https://quarto.org/docs/guide/)
- [Quarto Websites Guide](https://quarto.org/docs/websites/)
- [Shiny for R](https://shiny.rstudio.com/)
- [Shinylive Documentation](https://quarto-ext.github.io/shinylive)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

