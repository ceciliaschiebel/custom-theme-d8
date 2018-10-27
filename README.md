# Sub-Theme based on Drupal Bootstrap

This sub-theme applies a few templating and style changes to the original Drupal Bootstrap theme.

Read the [Sub-theming](https://drupal-bootstrap.org/api/bootstrap/docs%21Sub-Theming.md/group/sub_theming/8) topic for more information about how this sub-theme was created.

- [Prerequisite](#prerequisite)
- [Installation](#installation)

## Prerequisite
Since this is a sub-theme, you need to install [Drupal Bootstrap](https://www.drupal.org/project/bootstrap) first.

To do this, go to your admin panel, click on Appearance and then, click on **+ Install new theme**.
Once there, on the field **Install from a URL**, paste the following URL: `https://ftp.drupal.org/files/projects/bootstrap-8.x-3.13.tar.gz` and click **Install**

If that option is not available, download the file from `https://ftp.drupal.org/files/projects/bootstrap-8.x-3.13.tar.gz`, unzip it and copy the folder `bootstrap` into your project's `themes` folder. On the admin panel, click install on the theme.

## Installation
Copy the folder `custom` of this repository into the folder `themes` of your project.

Back to your Admin panel, you will see a new theme called **custom**, install and set as default.


## Implementation Details

This exercise demonstrates competency with the Drupal 8 theming system as well as a basic knowledge of interacting with the Drupal admin UI.

1) Clone https://github.com/mcewand/docker-d8 and follow the directions.  
  I had docker already installed so I just cloned the repo and run `docker-compose -f docker-compose.yml up`

2) Create a Drupal 8 theme that uses Drupal Bootstrap as a base theme.  
  First I searched for Bootstrap theme on Drupal's [directory](https://www.drupal.org/project/project_theme).  
  Following [this guide](https://www.drupal.org/docs/8/extending-drupal-8/installing-themes)   
  I downloaded the tar.gz file, decompress it and pasted the `bootstrap` folder on my project's `themes` folder.  
  After reading Drupal Bootstrap guides on how to edit the theme (by creating a sub-theme, so when the original theme is updated, your changes won't get lost); I went to the starterkit folder included inside the theme, and choose the `cdn` folder.  
  Copied it inside `themes`, and renamed the corresponding files ( [explained here](https://drupal-bootstrap.org/api/bootstrap/docs%21Sub-Theming.md/group/sub_theming/8) )

3) Make the background for the site light blue with a gradient to dark blue at the bottom of the page.  
  I added the background styling on `./css/style.css`.  
  At the beginning the changes didn't reflect on the page, so I searched a little and found out the `Clear all caches` option inside Configuration > Development > Performance

4) Change the title for all pages that display a non-blank title (e.g. node pages) to "This page is named: [page title]"  
  For this item I also needed more context about which was the Title to change, drupal blogs were helpful here.  
  Using bootstrap theme as guide, I created a copy of `page-title.html.twig` inside the custom theme templates folder. Added the `title_prefix` var on the template and then assigned a value to it on `custom.theme` file inside the hook function for page-title.

5) On Article pages, there is an image field provided. Mask the main image with a grey box.  When the mouse hovers over the image, remove the mask.  
  Similar to the previous item, I created a copy of `image.html.twig`, wrapped the img tag on a relative positioned div; and added a second div, absolute positioned with a grey background color that turns transparent on hover.

6) Check the theme into github.  
  Created the repo, copied the theme folder and pushed the changes. Then, I tested creating a base project from scratch and installing the theme and sub-theme again.
