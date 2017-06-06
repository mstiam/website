---
layout: toc
title: Edit This Website
---

# Edit This Website

## Simple

This section contains step-by-step instructions for making modifications to the dynamically generated content of this website.
Data on group members, projects and related publications, facilities, and slideshow pictures is all stored in text files.
These text files are then parsed to generate the web pages you see.

### Obtain Permissions

The easiest way to modify the text files is via GitHub, a website we use to track changes to the codes.
However, you will need to be granted access, which requires the following:

1. [Make a GitHub account](https://www.github.com/join)
2. Request owner permissions to Innovative Additive Manufacturing GitHub Group by contacting [Dr. Ming Leu](mailto:mleu@mst.edu) or an existing authorized group member.
    - Provide them with your *GitHub username*
3. Check your email and accept the group invitation

If you have already done the steps above, go to the next step.

### Make Modifications

The next step is to actually make your desired changes.
The type of change you want to make will determine the file you need to edit.
The table below tries to direct you to the proper file.

| What You Want to Modify     | File to Edit          |
| :-------------------------- | :-------------------- |
| Faculty Members             | [faculty.yml][1]      |
| Postdoctoral Fellow Members | [postdocs.yml][2]     |
| Student Members             | [students.yml][3]     |
| Staff Members               | [staff.yml][4]        |
| Projects                    | [projects.yml][5]     |
| Publications                | [publications.bib][6] |
| Facilities                  | [facilities.yml][7]   |
| Slideshow Pictures          | [slideshow.yml][8]    |
{:.table .table-condensed}

Once you know which you want to modify, click on its appropriate link above to go its GitHub page.
Next, assuming you are logged in to GitHub, click on the pencil icon in the upper righthand corner of the text file content window.

![GitHub Edit File Button Location](edit-data.png){:.img-responsive .img-thumbnail width="800px"}

This will take you to a page where you can edit the contents of the file directly in the browser.

**<i class="fa fa-exclamation-triangle"></i>
Each text file in the table above has documentation at the top of it explaining its structure - you must follow the file formats.**

Files with `.yml` extension are based on a simple format called [YAML](https://en.wikipedia.org/wiki/YAML).

The file `publications.bib` is in [BibTeX](https://en.wikipedia.org/wiki/BibTeX) format. It is easiest if the BibTeX entry for each publication is downloaded directly from the website of the publisher. Almost all of the major publishers have **citation export** links for each publication in different formats including BibTeX. The BibTeX entry should then be placed in `publications.bib`. It is advised that the fields of each new BibTeX entry be carefully checked for errors. Note that you need to add specific non-standard fields to the new BibTeX entries in order to make sure they will be listed under appropriate project (read instructions at the top of `publications.bib`).

If you need to upload a file (e.g., member photos), navigate to the destination directory and click on **upload files** button.

![GitHub Edit File Button Location](upload-files.png){:.img-responsive .img-thumbnail width="800px"}

Once you are done making your changes, do the following:

- Scroll to the "commit changes" area at the bottom of the page
- Provide a short description of your change(s) in one or both of the text boxes
- Click on the green **commit changes** button to update the file

### Deployment

Once you have edited the file, the website is is automatically built and deployed using a continuous integration tool called [BuddyWorks](https://buddy.works/) whenever the files are updated.

## Advanced

This section discusses how to modify the website in a variety of other ways, each of which require additional knowledge.

### Clone from GitHub with Git

All of the files for this website are kept within a *repository*, which you can think of simply as special folder/directory where changes are tracked.
Changes to the repository (e.g., the website) are tracked with Git, a version control system.

GitHub is website that provides hosting for Git repositories.
In other words, you can store you repositories on their remote servers for safekeeping.

In simple cases, you can make changes to a repository directly from their website.
However, to modify the folder structure of a repository or add/remove files, you must modify the repository locally on your computer.
This requires basic knowledge of how Git works, and links to an introductory article and a tutorial video can be found [here](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) and [here](https://www.youtube.com/watch?v=0fKg7e37bQE).

### Make Modifications

With the repository cloned to your local computer, you can make any changes you desire to the files within the repository.

**It is recommended that you always pull the latest changes before making your changes (`git pull` command).**

Once you are done making changes, you will need to stage all of your changes (`git add` command) and then commit them (`git commit` command).

Lastly, push your changes to GitHub (`git push` command) so that others can see your changes.

### Build

Once the website has been cloned from GitHub, you will need to build it.

This website uses [Jekyll](http://jekyllrb.com/), which is a software tool for generating static websites from templates and plain text.
Jekyll makes it easier to maintain the website because there is less repeated code.
Another benefit of this is that those without background knowledge of the inner workings of the website can make simply changes to the website, e.g., the data files.

If you wish to build the website, you will need to follow the [installation instructions on Jekyll website](http://jekyllrb.com/docs/installation/).

After you cloned the website repository and installed Jekyll, navigate to the repository directory via the command line. The following lines are only required to be executed the first time:

- `gem install jekyll-scholar`
- `bundle config build.nokogiri --use-system-libraries`
- `bundle install`

Execute the following line after making changes so that Jekyll generates the static website:

- `bundle exec jekyll build`

Alternatively, if you want to preview the website on your local machine, do the following:

- Navigate to the repository directory via the command line
- Execute `bundle exec jekyll serve`
- Navigate to 127.0.0.1:4000/~mstiam/ on your browser.

### Deploy

This website is hosted by Missouri S&amp;T.

Before changes are visible on the actual website, the static website generated by Jekyll must be deployed to the school server.

The `_deploy.rb` script (which requires [Ruby](https://www.ruby-lang.org/en/downloads/) and the [NetSSH Gem](https://github.com/net-ssh/net-ssh#install)) located in the website repository will do this for you quickly. Simply execute `ruby _deploy.rb` and enter credentials of an S&amp;T account that has been authorized to access and edit the contents of `mstiam` web space.

[1]: https://github.com/mstiam/website/blob/master/_data/faculty.yml
[2]: https://github.com/mstiam/website/blob/master/_data/postdocs.yml
[3]: https://github.com/mstiam/website/blob/master/_data/students.yml
[4]: https://github.com/mstiam/website/blob/master/_data/staff.yml
[5]: https://github.com/mstiam/website/blob/master/_data/projects.yml
[6]: https://github.com/mstiam/website/blob/master/_data/publications.bib
[7]: https://github.com/mstiam/website/blob/master/_data/facilities.yml
[8]: https://github.com/mstiam/website/blob/master/_data/slideshow.yml
