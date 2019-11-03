WORDPRESS FUNCTIONS USED USUALLY IN A WEBSITE   =>    https://developer.wordpress.org/reference/functions/get_bloginfo/

function university_files() {                         =>    creating a function to declare the scripts and styles that gonna be using for the project
    wp_enqueue_style('university_main_styles', get_stylesheet_uri());
    wp_enqueue_style('font-awsome', 'https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');
}

add_action('wp_enqueue_scripts', 'university_files');                   =>    running the function in wordpress using add_action() -> function

function university_features() {                                        =>    adding a function to support the title element dynamic in every pages
    add_theme_support('title-tag');
    register_nav_menu('header_menu_location', 'Header Menu Location');  =>    registering a menu to the dashboard in Appearance tab/section
}
add_action('after_setup_theme', 'university_features');                 =>    runnding the function using add_action wordpress function



wp_nav_menu(array(
      'theme_location' => 'headerMenuLocation'  =>    displaying the custom menu that was created in the dashboard appearance menu
));
wp_nav_menu();                                  =>    displaying the menu dynamic in the website.
wp_nav_menu( array(
      'theme_location' => 'headerMenuLocation'  =>    displaying a custom menu/navbar content in the frontend of site. that is set in the Apperance -> Menu -> Add Menu
) );
bloginfo('name');             =>    display the site title
bloginfo('description');      =>    display the tagline - display the tagline
bloginfo('siteurl');          =>    display the site url or
bloginfo('url');


LANGUAGE DYNAMIC ON SETTINGS WORDPRESS
<html <?php language_attribute(); >>            =>    sets a dynamic language attributes depends on your wordpress dashboard > settings > general -> language
</html>
<meta charset="<?php bloginfo('charset'); ?>">  =>    character set utf-8 is character encoding capable of encoding all characters on the web. It replaced ascii as the default
<body <?php body_class(); ?> >                  =>    shows the class made by the wordperss -> add class attribute on what page is your at and page id and other using dynamic class with wordpress
</body>

FOR BREADCRUMBS
get_the_ID();                             =>    get the current ID of the page
wp_get_post_parent_id(param);             =>    get the parent page of the param
wp_get_post_parent_id(get_the_ID());      =>    get the parent ID of the current page


FOR DISPLAYING THE CHILD LINKS INTO THE PAGE
get_pages(paramArray())             =>    used to check and return the children of the param page
get_pages(array(
      'child_of' => get_the_ID()    =>    return the children of the current page
));
wp_list_pages();                    =>    used to display all the pages links
wp_list_pages(array());             =>    used to display all the children page link depends on the arguments if it has a children pages
<!-- Declaring the variables -->
$theParent = wp_get_post_parent_id(get_the_ID);       =>    Declared variables for the children link in the page
$findChildrenOf = get_the_ID();                       =>    Declared variables for the children link in the page 
wp_list_pages( array(
      'title_li' => NULL                  =>    removing the title li of the links
      'child_of' => $findChildrenOf       =>    declaring a parent page to show only their children paes
      'sort_column' => 'menu_order'       =>    setting the order of the children page/link to the menu order of the dashboard in pages
));


THE WHILE LOOP                =>    used in every posts to loop into it
<?php
      while( have_posts(); ) {
            the_post();

            the_post_thumbnail();         =>    display the post image
            the_title();                  =>    display the post title
            the_content();                =>    display the post content / description
            the_permalink();              =>    return the link of the particular post
            the_excerpt();                =>    return the excerpt / subtitle of the particular post
      }
?>


USEFUL FUNCTION
<?php wp_footer(); ?>                     =>    to show the shorcut dashboard top bar in the front end place this before the end tag of the body
determine_locale();                       =>    return the country request
get_stylesheet_uri();                     =>    return the style.css location / url
get_stylesheet_directory_uri();           =>    return the directory of the used stylesheet css
get_template_directory_uri();             =>    return the directory of the current template used in the wordpress


NAVIGATION LINKS
wp_list_pages();                          =>    returns all the list of pages
wp_list_pages('exclude=17,38');           =>   to exclude the input / parameters in the function
wp_list_pages('child_of=5');              =>    display only the sub-pages of a single page by ID
for more pages function and reference     =>    https://developer.wordpress.org/reference/functions/wp_list_pages/


CATEGORIES                                =>    categories created to group the post into different categories
wp_list_categories();                     =>    return all the list of categories
wp_list_categories('exclude=10, 15');     =>    exclude to limit the categories you want
wp_list_catories('child_of=8, 14');       =>    if you would like only to show the select childen categories
for more categories function              =>    https://codex.wordpress.org/Good_Navigation_Links#Categories


ARCHIVES                                  =>    archives date-based Template Tag called
wp_get_archives();                        =>    The tags allows you to display links, to arhives by year, week, day or individual posts. 
wp_get_archives();                        =>    The default usage of the wp_get_archives will show a link for each month of posts.
wp_get_archives('monthly&limit3');        =>    To show the mose recent three months of posts by month, you would use the this code
wp_get_archives('type=daily&limit=15');         =>    Displaying the archives by date, you can show the most recent 15 days:
wp_get_archives('type=postbypost&limit=25')     =>    show the actual posts use the parameter 'postbypost' which displays the most recent posts, with the number set by the limit parameter. To show the last 25 posts by post title.
for more information and reference              =>    https://codex.wordpress.org/Good_Navigation_Links#Categories
                                                =>    https://codex.wordpress.org/Template_Tags/wp_get_archives



===============================================================================================================================================================================================================================



FUNCTIONS FOR MANIIPULATING WORD (PARAGRAPH)
wp_trim_words('sentence', limitNum);          =>    used to trim words / text to shorten the characters ex: wp_trim_words($sentence, 18);      


INDUSTRY STANDARDS (CUSTOM FIELDS) -> PLUGINS
      =>    Advanced  Custom Fields / ACF
      =>    CMB2 (Custom Metaboxes 2)


FOR THE DATE FORMAT
the_field('event_date') displaying the created date using the plugin
