# SiteTemplate
Miro Manestar &copy; 2020. All Rights Reserved.

BASIC USE
    In the body tag of your base-level index.html only, include the attribute onload="onFirstLoad();"
        What this will do it will redirect the user to the last page they were on before a page refresh, or otherwise load the homepage
    Furthermore, have a <main> tag with id="page-content" inside your body tag. This is where your page content will be displayed.
    Other things you must include in your top-level index.html:
        - This file
        - jQuery (3.5.1 or newer)
        - <base href='/' /> (DO NOT FORGET TO ADD THIS TAG)
    Optional:
        - Bootstrap (Any version)
        - FancyBox (For Lightbox) http://fancyapps.com/fancybox/3/

    In your top-level directory, also create a 404.html only with the content shown in this template.
        Your actual 404 page content will be located in the /pages/404 folder, inside index.html.
        The loadContent() function will automatically redirect here if a page doesn't exist.
    
    ---- LOADING A PAGE ----
        When you want to load another page, call loadContent('path/to/pageFolder').
        This will look inside the pages folder and load the index.html inside the subfolder. I.e. if your have a folder 'test' inside pages, and test has
        an index.html file inside it, calling loadContent('test') will load the index.html file inside /pages/test.
        To do sub pages, make a subfolder. I.e. /pages/test/subtest can be loaded with loadContent('test/subtest').

        The content from the index.html in the loaded folder will be placed inside the <main> tag

        There are only two special folders inside /pages/ - home & 404.
        Whatever is inside the home folder will be loaded on first visitation to page unless the user refreshed while on a different page. In that case,
        that page will be loaded. When calling loadContent('home'), it will load the content in the folder /pages/home, but the URL displayed will be the
        base URL

        This will also update the URL and history (And breadcrumbs, if they're enabled).
        Furthermore, it will add an active class to the appropriate element inside the header, highlighting whichever page is currently displayed. 

        ---- CUSTOM TEXT IN TAB BAR AND BREADCRMBS----
        In each page index.html, have a element with the id 'page-title'. The text content of that element will be used in breadcrumbs and the page title
        if the appropriate settings are enabled.

        If changePageTitle is enabled, the title in the tab bar will be modified on each page load. By default, it will append the current page title to the
        text inside the <title> tag in the primary index.html. If you disable appendPageTitle, the text in the tab bar will be replaced by whatever the current
        text inside the page-title element is.

        ---- LOADING WEBSITE CONTENT ON A PAGE ----
        When referencing other files to be loaded by a page's index.html, you must use the full path from the top level.
        I.e. if you're editing index.html in /pages/test and you wanted to load something from that same folder, the path would be
        /pages/test/file.whatever. This is because it allows you to access content from anywhere else in the website directory.
    
    ---- LIGHTBOX ----
    Lightbox is when you click on an element (Usually an image), and it opens up enlarged in a modal view overlaying everything else.
    This is accomplished using this library: http://fancyapps.com/fancybox/3/. Refer to there for documentation on how to use it's more advanced features.
    However, this script will automatically cycle through all images and enable lightbox on them (Basically click to enlarge), and use the alt attribute as
    the caption. It will ignore any <img> element which has the class logo-image or no-lightbox.

    ---- PARTIALS ----
    Partials are stored just like pages inside the /partials/ folder.
    It's used by setting a partial attribute in an element. I.e., say you had a partial stored in /partials/clock
    If you had an element with the attribute partial="clock", that element would get replaced with the content of index.html inside /partials/clock.
    Essentially, it's like loading a mini page.

    ---- THEME-SENSITIVE FAVICON ----
    main.js will detect the preferred color scheme of the user. The darkIcon variable should be a string of the path to the icon which is appropriate for dark
    mode users. I.e., it'd probably be a lighter color to contrast against the dark background of the browser.
    This is disbaled by default
