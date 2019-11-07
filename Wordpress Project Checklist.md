Checklist on creating a wordpress site.

Wordpress Theme Development

You must have installed these applications on your laptop
 - xampp
 - code editor (vscode is what I recommend)
 - browser ( chrome is the best option)

I.  First is to download the wordpress.zip file on this link 
        -> for japanese     https://ja.wordpress.org/download/ 
        -> for english      https://wordpress.org/download/

II. Next thing todo is goto C:\xampp\htdocs\ 
        -> create a foler for your project and name it with your project name
        -> go inside into the project folder
        -> extract the (wordpress-5.2.4-ja.zip) -> this is the wordpress japanese version that you have downloaded
        -> after that now open your browser and goto localhost/projectName or localhost:8080/projectName it depends on what port your server is using for me it is localhost:8080/projectName
        -> before you start the installation of wordpress project you need first to create a database for your wordpress site.
        -> goto localhost/phpmyadmin and create a database for your wordpress site
            --> you need the database because wordpress will store all of the post, page, images, and other that you're gonna need in your project

III. Wordpress Site Setup
        -> there will be 4 input fields that you need to fill in
            --> enter your - database name
            --> enter your - username for your project
            --> enter your - password for the project
            --> leave the wp_ in the input fields and click setup or install
            --> New Wordpress site has been set up successfully
IV. Templating Section
        -> as you can see you are running a new wordpress project next is, goto your file location htdocs/projectName/wp-content/themes
            --> create a new folder/directory and name it with your template name. ex my-theme
            --> then go into that directory and right click open with vscode.
V.  Theme Rocks!!!!!
        -> Here in this section will be going to create the necessary files for our template ohhh yeahh 
            --> starts it with style.css - this will tells about your template description
                    -->   /*
                            Theme Name: My-Theme
                            Author: Name LastName
                            Version: 1.0
                           */
        --> next is index.php. after this try to navigate to wordpress project dash board under the appearance click the themes and your template will gonna show up and select it
VI. Template Files
        --> style.css       - theme name details
        --> index.php       - where you site lives
        --> header.php      - header of the site
        --> footer.php      - footer of the site
        --> functions.php   - this is the heart of the wordpress. wherein you can control and customize some of the website components
        --> page.php        - is the template for siblings pages of your site
        --> single.php      - this is page/template for every single post
        --> archive.php     - this is template for category 
        --> assets folder included the images, css, and js
   
    =====================================

        --> lets start with index.php paste your copy and paste your index.html static site code to index.php
        --> next is to seprate the part of the index.php codes, cut the header part of your codes and paste it in your header.php
        --> cut the footer part of codes and paste it into your footer.php

VII. Remove and add an unnecessary codes that won't work in wordpress and add a piece of code for the link of the assets used in the project/website.
        --> header
                Remove 
                    - remove the title, link-css codes in the header and scripts                
                Add
                    - add this code under the meta tag <?php wp_head(); ?>
                        - wp_head() = is a function in wordpress which will handle for dynamic content of the title script and styles in the header
        
        --> footer
                Remove / Edit / Add
                    - Remove the script tag or
                    - Edit the script tag and add this code <script src="<?php echo get_template_directory_uri(); ?>./assets/js/main.js"></script>
                        - get_template_directory_uri() - is a function that return the url of the current directory of your theme that you are using.
                    - Before the end body tag add these code 
                        <?php wp_footer(); ?>   = this will add a shortcut navigation to the dashboard where your'e on the front page.

VIII. The functions.php - enabling your css and js into your project
        --> create the file functions.php = this file will be like the controller for the components of your worpress site
                --> for adding your scripts and stylesheet you need to add these function to your functions.php "note" this will work only if you have wp_header() in you header.php
                     <?php
                        function projectName_files() {
                            wp_equeue_style('my-stylesheet', get_template_directory_uri() . '/assets/js/main.js'); -> for css
                            wp_equeue_style('my-external-stylesheet', '//cdnjs.cloudflare.com/ajax/libs/Swiper/4.5.0/css/swiper.min.css'); -> for css with external link / api "note" you need to remove the https on the link or cdn
                        }
                     ?>
        --> will go back to this functions.php later

IX. Adding the link directory for the assets in the project
        --> ex <img src='./assets/img/logo.png'> = <img src='<?php echo get_template_directory_uri(); ?>/img/logo.png'>
        --> just change all the the link to directory that looks like this case.
        --> check the site if all of the file is loaded you can check the console if there is a missing file if none then we're ready to the next step

X.  Title - Make Dynamic
        --> to your title dynamic we need to go back into the functions.php and add some code for it
        --> in your functions.php file add this codes
            <?php 
                functions projectName_features() {
                    add_theme_support('title-tag');     => this will make your site title dynamic whenever what page you're in. this is connected to the wp_head();
                }
             ?>