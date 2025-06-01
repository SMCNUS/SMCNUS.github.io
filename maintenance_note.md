# Maintenance Note

* The official website of the SMC Lab is hosted via a GitHub repository [SMCNUS.github.io](https://github.com/SMCNUS/SMCNUS.github.io). 
* To update the website, simply modify the HTML files in this repo and push the changes to the origin. 
* During the editing process, the site can be rendered locally using *Jekyll*, a static site generator, for preview before publishing.

This note will:
* Introduce the key files and directory structure of the website repository;
* Provide instructions for installing Jekyll;
* Guide through the process of previewing and publishing website updates.

If you are taking on the role of maintaining the SMC Lab webpage, please ensure the following:
* You have been added as a collaborator to the GitHub repository.
* You have cloned the repository to your local working environment.

## File Directory
This repo is arranged as follows:
* [`./_includes`](_includes) contains HTML blocks used to construct the front page (i.e., [smcnus.comp.nus.edu.sg](https://smcnus.comp.nus.edu.sg/)).

* [`./_layouts/front.html`](_layouts/front.html) assembles the HTML blocks from [`_includes`](_includes) to render the main front page layout.

* [`./_posts`](_posts) contains HTML files of subpages, such as [smcnus.github.io/video_page](https://smcnus.comp.nus.edu.sg/video_page).

* [`./archive`](archive) stores image and PDF files, including lab member photos and publication PDFs.

* Other folders include CSS and JavaScript dependencies. **These typically do not require modification**.


## Install Jekyll
Jekyll is a static site generator commonly used for building and previewing websites locally. It allows to render and review the webpage in one's local repository during the editing process. Once the updates are verified and everything looks correct, one can push the changes to the remote repository to update the live website.

### Instruction on Installation
Follow the official documentation to install Jekyll on [MacOS](https://jekyllrb.com/docs/installation/macos/) or [Windows](https://jekyllrb.com/docs/installation/windows/). The guide will walk through installing *Ruby* first, and then install Jekyll using Ruby's package manager. 

**Important**: Please make sure to install Ruby version 2.7.8, as newer versions may cause compatibility issues with the SMC Lab webpage.

### Previewing the Webpage

To preview the webpage locally:

1. Open terminal or command prompt.
2. Navigate to the local repository directory (i.e., `/path/to/SMCNUS.github.io/`).
3. Run the following command:

```bash
    jekyll serve --trace
```

The repoitory will be compiled to form a preview webpage. The following message should be seen in the termial:

```bash
    Generating...
                done in 7.129 seconds.
    Server address: http://127.0.0.1:4000/
    Server running... press ctrl-c to stop.
```
    
Open a web browser and visit `http://127.0.0.1:4000/` to view the preview.


# Maintenance Guidance

Maintaining the webpage is straightforward, as the HTML framework is already in place. In most cases, it can be done by simply copying and modifying existing blocks to add new content. Below provides several common editing examples to illustrate how the maintenance process works.

## Add New Lab Member
To add a new lab member, here's what to do:
1. **Add the Photo**: Add the new member's photo (e.g., jack_ma.jpg) to the directory [`./archive/team`](archive/team).
2. **Add a New Entry in HTML**: In [`./_includes/team.html`](_includes/team.html), locate an existing member block, and copy-paste it to the end. A typical block looks like this:
    ```html
    <div class="col-md-3">
        <div class="team-member">
            <img class="center-block img-circle" src="archive/team/joe_biden.jpg"/>
            <h4>Joe BIDEN</h4>
            <p class="text-muted">Research Assistant</p>
            <a class="btn" href="https://joebiden.com/" target="_blank"><i class="fa fa-link fa-1x wow bounceIn"></i></a>
            <a class="btn" href="mailto:biden.library@nara.gov "><i class="fa fa-envelope-o fa-1x wow bounceIn"></i></a>
            <a class="btn" href="https://scholar.google.com/citations?user=7wM1-DoAAAAJ&hl=en" target="_blank"><i class="fa fa-google-plus fa-1x wow bounceIn"></i></a>
            <a class="btn" href="https://www.linkedin.com/company/biden-2020/" target="_blank"><i class="fa fa-linkedin fa-1x wow bounceIn"></i></a>
        </div>
    </div>
    ```
    * On line 3, the `<img>` tag specifies the member's photo directory.The `src` attribute specifies the photo's file path.
    * On line 4-5, `<h4>...</h4>` specifies the member's name, and `<p>...</p>` specifies the position (e.g., PhD Student, Research Assistant).
    * On line 6-9, `<a class="btn">...</a>` defines link buttons to personal pages and social media, such as email and LinkedIn. The `href` attribute specifies the link. `<i class="fa ..."></i>` sets the button icon.
3. **Update the Content**: Edit the copied block with the new member's photo path, name, position, and links. 
    * For the photo path, make sure to use the **relative path**, e.g., `archive/team/jack_ma.jpg`
    * For the `href` attribute, if this is an email address, start with "mailto:" before the email address, e.g., `href="mailto:jack_ma@gmail.com"` 
    * For the button icon `<i class="fa ..."></i>`, supported icon types are listed in [`./font-awesome/css/font-awesome.css`](font-awesome/css/font-awesome.css).


## Add New Publication
The lab’s publications are displayed in three locations:
1. **Front Page – Selected Publications**: This is a block on the front page (https://smcnus.comp.nus.edu.sg#Publication) that highlights selected works from the past 3 years. 
    * To update this section, edit the file: [`./_includes/publication.html`](_includes/publication.html). 
2. **Front Page – Recent News**: This is a block on the front page (https://smcnus.comp.nus.edu.sg#About) that announces latest news of paper acceptance. 
    * To update this section, edit the file: [`./_includes/info.html`](_includes/info.html). 
2. **Subpage – Full Publication List**: This is a dedicated subpage (https://smcnus.comp.nus.edu.sg/full_publication_list) that lists the complete history publications. 
    * To update this full list, modify: [`./_posts/2022-07-28-publication.html`](_posts/2022-07-28-publication.html).

For example, to add a new publication to *Selected Publications* in the front page, here's what to do:
1. **Add the PDF**: Add the new pape file (e.g., 2025_ai_music.pdf) to the directory [`./archive/pdf/2025/`](archive/pdf/2025/).
2. **Add a New Entry in HTML**: In [`./_includes/publication.html`](_includes/publication.html), locate an existing publication block, and copy-paste it to the front. A typical block looks like this:
    ```html
    <li><p class="text-align">H. Liu, H. Huang, H. Wang, X. Gu, and Y. Wang, “<a href="archive/pdf/2025/2025_on_calibration.pdf" target="_blank"> On Calibration of LLM-based Guard Models for Reliable Content Moderation</a>,” in <em>Proceedings of the 13th International Conference on Learning Representations (<b>ICLR 2025</b>)</em>. OpenReview.net, 2025.</p></li>
    ```
    * `<a href>...</a>` includes the paper title, while the `href` tag specifies the path to the PDF file.
    * The purpose of attribute `target="_blank"` is that by clicking the link, the paper will be open in a new tab of the browser.
    * `<em>...</em>` makes italic fonts. `<b>...</b>` makes boldface. 
3. **Update the Content**: Edit the copied block with the new paper's author list, title, file path, venue, etc.
    * For the paper's file path, make sure to use the **relative path**, e.g., `archive/pdf/2025/2025_ai_music.pdf`.

### Format of Publication
The publication format may vary depending on the venue. As a general rule, if we already have an entry for the venue, then simply follow the format used in the existing record. Otherwise, please refer to the general guidelines below:
* If this is a conference paper, the format is typically as follows:
    * [Author list], "Paper title," *in Proceedings of [Complete conference name] (**Abbr + Year**)*. `publisher`, Year. pp. `page`.

* If this is a journal paper, the format is typically as follows:
    * [Author list], "Paper title," *[Jounral name] (**Abbr**)*, vol. `volumn number`, pp. `pages`, Year.

To retrieve accurate citation details, search for the paper title on [DBLP](https://dblp.org/) and refer to the BibTeX entry.

For newly accepted papers, page numbers may not come out yet. In that case, please update this information once it becomes available. Certain venues (e.g., NeurIPS, ICLR, ICML, ICASSP, TMLR) dont't have a page number, volumn number, and/or publisher. In that case, simply discard these entries.


## Add New Video
The lab’s video resources are displayed in two locations:
1. **Subpage – SMC Video Page**: This is a dedicated subpage (https://smcnus.comp.nus.edu.sg/video_page) that displays the lab's video resources. 
    * To update this section, edit the file: [`./_posts/2022-07-28-video.html`](_posts/2022-07-28-video.html). 
2. **Front Page – Recent Events and Videos**: This is a block in the front page (https://smcnus.comp.nus.edu.sg#Events) that lists all links for videos and other events. 
    * To update this section, edit the file: [`./_includes/events.html`](_includes/events.html). 

To add a new video, here's what to do:
1. **Upload to YouTube**: Upload the video to YouTube. The SMC lab has a dedicated youtube account([@smcnus365](https://www.youtube.com/channel/UCn4iMJjVktUb6SgprG4Eijw)). It is recommended to set the video as *unlisted*. 
2. **Add a New Entry in HTML**: In [`./_posts/2022-07-28-video.html`](_posts/2022-07-28-video.html), locate an existing video block, and copy-paste it to the front. A typical block looks like this:
    ```html
        <div class="row small-padding" id="amt2025">
            <p></p>
        </div>
        <p class="h3" style="color:#ed6502;"><b style="color:#031d83;">[2025.06] </b>CS4347/5647 Lecture on Automatic Music Transcription (AMT)</p>
        <p class='text-justify' style="text-indent: 40px">
            This lecture is presentation by <a href="https://wei-zeng98.github.io/" target="_blank" style="color:#031d83">Wei Zeng</a>, a PhD candidate from Sound and Music Computing Lab.
        </p>
        <p class="text-center">
            <iframe width="640" height="360" src="https://www.youtube.com/embed/DPCFe69-PNA?si=0IkWe3RV3FlbtIkz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
        </p>
    ```
    * On line 1, the `id` tag should be a unique name, which will be usful when linking to this video. 
    * Line 4-7 specifies the video title and a short introduction.
    * Line 9 specifies the *embedding code* of the video. On YouTube, this code can be obtained by clicking Share -> Embed. 
3. **Update the Content**: Edit the copied block with the new videos's name tag (`id`), title, intro, and embed code. 
    * When pasting the embed code, make sure to modify `width` and `height` to 640 and 360, respectively.
4. **Update Front Page Listing**: In [`./_includes/events.html`](_includes/events.html), add a new listing in the front. The hyperlink to the new video should be `./video_page#id`, where `id` is the video's name tag.


## Add New Subpage
When the lab holds an event (e.g., music concert, workshop), it is good to make a dedicated subpage to share relevant info and media. These subpages are managed in the [`_posts`](_posts) folder. To create a new subpage, here's what to do:
1. **Create New HTML File**: In the [`_posts`](_posts) folder, create a new HTML file following the naming format: `YYYY-MM-DD-name_of_the_event.html`. This naming format is mandatory in order to render this file as a subpage.
2. **Reuse Existing Template**: Copy the HTML content from an existing subpage that has a similar structure or layout. This provides a convenient framework for the new page.
3. **Edit Page Link**: At the beginning of the new file, include the following front matter:
    ```html
        ---
        permalink: /page_name
        ---
    ```
    * This will render the subpage at `https://smcnus.comp.nus.edu.sg/page_name`.
4. **Update the Content**: Replace the placeholder content with the new event’s information, media, and layout as needed.
