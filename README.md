# General Notes

## Mindbru

Mindbru is a re-occuring name you'll find across older Kru sites, commonly used by a previous developer named Oz. You'll often find Mindbru as a plugin or a theme, and it will often be the source of many issues. If you're ever scratching your head wondering "where the hell is this coming from", check those two places.

## Beaver Builder

`Beaver Builder` is a website builder plugin / theme we use to create Wordpress sites. The few things to understand about `Beaver Builder` are these:
**1.** `Beaver Builder` has its own cache clearing tool found in (Settings > `Beaver Builder` > Tools), and proves useful changes aren't reflected properly. I mostly see this with sites hosted on servers using Varnish Cache.
**2.** Custom CSS and JS is used page to page, accessible by editing a page with `Beaver Builder`, then navigating to the (Tools > Layout CSS & Javascript) in the top left corner.
**3.** `Beaver Builder` plays really well with `Pods` and `Advanced Custom Fields`, allowing you to directly connect them to modules. For example if you have a custom field on the Home page that allows you to input a string, we can hook that field directly into a module via the module settings in the builder.
**4.** `Beaver Builder` supports conditional logic, meaning we can choose if an element is displayed based on specific criteria. While editing, you can tell when an element is using conditional logic because when you hover over it, a red-eye icon displays in the top right corner. Conditional logic can be accessed on each element by navigating to (Column Settings > Advanced). I almost always use conditional logic on columns specifically. This allows us to tell `Beaver Builder` "hey, if this custom field has (value), do (this)". Most cases are "if this custom field has a value, display the column".

## Impreza

`Impreza` is a builder plugin / theme we often use for smaller projects. A few things to understand about `Impreza` are as follows:
**1.** `Impreza` allows for whitelabeling, and so sometimes displays differently in the Wordpress dashboard, but always in the same place.
**2.** Most of the settings of any site built with `Impreza` are all found in (Impreza > Theme Options). This includes custom CSS and JS found in (Theme Options > Custom Code).
**3.** `Impreza` manages headers (Impreza > Headers).
**4.** `Impreza` uses Grid Layouts, Page Templates, and Reusable Blocks to display content. I'm not quite sure how they work because I'm more of a Beaver Builder guy, but be mindful of this.
**5.** From what I understand, `Impreza` handles forms right out of the box, no SMTP required? A few times that hasn't been the case, but idk.

## Instagram Issues

Most of the sites use an Instagram plugin, and the fix can be as easy as resetting the feed connection by re-connecting or making a new feed (which would require shortcode re-implementation). Otherwise you're most likely looking at an API issue, and will have to find where the API call is being made from. Usually it's .js file in the (wp-content > js) folder, but sometimes it can be a function found in the function.php, or even in the one of the `mindbru` plugins or themes. If that's the case then you'll have to pull tokens via a CLI, see: https://docs.oceanwp.org/article/487-how-to-get-instagram-access-token

## Google Services

Accounts used for analytics and smtp, where the smtp is being used.

## Plugins, Themes, Add-ons and Services

Everything we use for sites can be found on the server under >>>, and all credentials can be found in Keeper in the "Kruhu" folder.

# Hosting

Kruhu maintains two hosting providers, `Cloudways` for Wordpress sites, and `Netlify` for JAMstack sites.

## IONOS

IONOS is our e-mail provider and also hosts the Kruhu (The Kru) website. IONOS manages Kruhu emails and Land of Thee emails. We also provide a few other websites with e-mail functionality via IONOS (referred to as External Domains).
Additionally, there are two old sites (Luckey Printing & New School Mosaics) located here as well. Luckey Printing can be found in the webspace (kruhu > Clients), whereas New School Mosaics is found on the root as (paul-pearman).

## Cloudways

Our hosting provider for Wordpress sites. Make sure to disable Varnish on new servers!

### Kruhu Development

This server is where we keep development projects that never left the ground, as well as a few sites from a server transfer from our old HostGator account. None of these sites are "live".

### Sage Valley

This server holds two sites, the old Sage Valley site we transferred over, and the new site we built them. The live site is built with `Impreza` and has a few notes.
You'll find some custom code for styling and a few JS functions under the Theme Options (KRUHU > Theme Options > Custom Code). The custom code here adds menu shadows, prevents bubbling on a particular button, and adds `href` tags to a few grid items found at the bottom of the home page. Some individual styling can also be found per page, but not much.
The only other "gotcha" on this site are the cottages. Under (Portfolio) you'll find the cottages, each use a preset design found in (KRUHU > Grid Layouts). The owners of this site are particular about the order of their cottages, and each time changes are published on a cottage (not often) they'll fall out of order (the last published appears first). This leads to having to run through each cottage and publish it in the correct order.

### Kendrick

This server holds two sites, the live site and a staged site. A pretty dated site but usually no trouble, there are two things you'll need to keep in mind: contact forms and the store.
From what I understand the site uses the `Contact Form 7` plugin to handle forms. They often change the email addresses these forms are sent to, which can be done from inside the particular form's settings. They also like to export these forms, the settings of which are found in (Contact > Create PDF). Each form also has its own page where the shortcode is implemented.
As for the store, its used internally to order Kendrick gear, but they haven't used it in quite some time. The page itself is disabled (set to draft) - but if changes are ever necessary, you'll most likely need to dive into the site via FTP as most custom pages can be found either as the plugin `mindbru` in the plugin directory, or the theme `mindbru` in the theme directory.

### Field Botanicals

This site sucks. Its a huge e-commerce site with a ton of functionality held together by finicky plugins. I will certainly do my best in mentioning everything I've learned from working on this frankenstein's monster. When in doubt stage the site, de-activate all the plugins, and work your way down. If you're ever stuck in the dark, check the `mindbru` plugin.
**1.** This site often experiences issues syncing the catalog with social media sites. The biggest concern is items not appearing, or displaying incorrect quantities. We aren't social media experts, and so I've deferred this issue whenever possible (but have tried many times, unsuccesfully, to fix it).
**2.** This site often experiences bot issues with empty accounts, and has had a decent amount of "protection" added to it in the form of limiting login attempts and CAPTCHAs.
**3.** There's a lot of custom CSS going on here, found both in (Appearence > Customize) and individual pages.
**4.** Changing the footer requires directly editing the `footer.php` file.
**5.** There are plenty of custom functions added to the `functions.php` file.
**6.** The two biggest culprits of broken product displays are the plugins `Shopkeeper Deprecated Features` and `Shopkeeper Extender`, the former of which should always be de-activated. If you're ever dealing with this particular issue, these are what I suggest looking at first.

### Visit Columbia County

At this particular moment, they've just launch a new site with the help of SimpleView, and we aren't hosting it at the moment either. There may be a point in time where you'll need to transfer the hosting to ours, in which case good luck!

### Design Labs

A simple, straight-forward, one page site built with `Impreza`.

### Electrical Design Consultants

An old site we took over hosting for. They came to us in 2021 to design and build their new site, but still haven't delivered all the necessary assets to begin the design process.

### Academy Art Museum

We built this site with a rich CMS - looking back I would have taken a different approach. This was before I knew about headless content management systems, and so there's a lot of jQuery and PHP playing with eachother behind the scenes, but mostly straight forward nontheless. It was built with `Beaver Builder` and makes heavy use of the `Pods`, `Advanced Custom Fields` and `Woody Snippets` plugins.
The `Pods` plugin to manage the custom post types (Collections) and (Press Releases).
The `Advanced Custom Fields` plugins creates custom fields for particular post types or pages. This is doing most of the heavy lifting when it comes to the CMS.
The `Woody Snippets` has two primary purposes. The first is feeding content into the Event page via the (Event Preloader) snippet. The second is making use of repeater fields which work in tandem with `Advanced Custom Fields` to provide a dynamic CMS.

When it comes to the Event page, there's a lot of jQuery managing the events. Basically we use PHP via `Woody Snippets` to preload every event, and then jQuery to manage the display. The jQuery can be found in the Event page by opening it via `Beaver Builder` (aka "Edit"). It would be smarter to move all of it to a single .js file and enqueue it in the functions.php, but I didn't.

Generic items such as hour of operations, admission prices and the banner can be found in (Options).

We hide most of the dashboard bloat from the users via the `Adminimize` plugin.

### Sea Island Landscape Services

Another straight-forward, small site built with `Impreza`. There's a few lines of custom CSS and JS in the (Impreza > Theme Options > Custom Code) section to handle the menu and some scrolling. There's also a few lines of custom CSS found in each individual page, and other than that I think the only thing work mentioning is how the videos are handled, which is a Raw HTML block with some goofy iframe / padding code.

### Fat Mans Catering

This server hosts five different sites, and they're all pretty straight-forward. I believe all of them are built with `Impreza`. One of the sites, Hudson, isn't live. The only thing I'll note is Southern Salad. You'll see there are multiple pages in the Dashboard, but really it is a one page site. Viewing any single page will look wonky. Some of the site can be changed via the (Options), but mostly this site only comes up when they need the Menu changed (which can be done by editing the "Menu" page).

### Land of Thee

Another e-commerce site similar to Field Botanicals but not nearly as bloated. The two main issues you might face are instagram issues, which can be fixed by resetting the feed connection in the `Instagram Feed` plugin. The other might be a styling issue, usually on a single product or the checkout page. The first place I suggest looking is in the themes and the woocommerce directories inside them.

## Netlify

Netlify hosts our JAMstack sites, usually built with Astro or React. Each of these sites provide documentation via their README.md files.

## Other

This list contains sites we don't host, but have built / work on.

### Second Harvest

Second Harvest, or Help End Hunger only approaches us for one thing: chaning a pop-up.
The file that manages the pop-up can be found at (plugins > mindbru > mindbru.php). The image and link are set all the way down at the bottom of the file. You'll want to make sure the image is already uploaded so you can link it properly.

### Georgia Lake Country

This is another Wordpress Site we built with `Beaver Builder` and a rich CMS, hosted on Bluehost. Bluehost has awful customer service and I don't recommend relying on them if you can help it.
Because they're on a shared hosting plan, they don't have access to server settings, specifically their Varnish Cache. This causes a lot of issues with the site not displaying changes that have been made to it. The clients are aware of this and are well informed of the fix: when changes are made, the cache must be cleared manually. This is done by navigating to (Settings > `Beaver Builder` > Tools) and hitting the button.
The site makes use of the `Pods` plugin to manage custom post types (which they have a lot of) and `Advanced Custom Fields` to extend the CMS.
We use `Adminimize` to clear dashboard bloat on their end.
Under (Settings > Header and Footer) you'll find some mailchimp scripts.
Again you might face an Instagram issue where the connection needs to be reset.
Lastly, most of their custom post type pages have a tab that displays "Near Lake Sinclair" and "Near Lake Oconee" - sometimes they don't have enough content to fill both areas. I believe at this point they're filled, but just in case they're not I want to note that these content tabs' / containers' display options can be changed via the `Beaver Builder` editor.

### Masters Jobs

This is a multi-site network we built using `Beaver Builder`, hosted on Pantheon with a rich CMS. When making small changes to the sites you can get away with editing the live site, but larger changes must be done on the dev site and pushed through the staging funnel (dev > test > live). Pantheon has their own CLI called Terminus that you may have to use, but has since implemented a lot of features in their Dashboard which might make it completely optional. Since we're talking about Pantheon, I'll start with the basics before moving onto the actual network.

**1.** You can switch the development site into one of two modes, `SFTP` or `Git`. Either is useful depending on what you're trying to do. You can't access the files via SFTP without enabling SFTP in the dash, vice versa.
**2.** When pushing / pulling environments (under Database / Files), you'll want to make sure you convert the URLs in the database. They now provide an interface for this.
**3.** Pantheon has their own cache which can sometimes effect updated content, but I believe we've remedied this issue by setting the cache interval to its lowest possible value (0s on the main site, 60s on the subsites). You can find the settings in the Wordpress Dashboard (Settings > Pantheon Page Cache). If you face any other issues, always try clearing the `Beaver Builder` Cache (Settings > `Beaver Builder` > Tools).
**4.** Masters has a dedicated Pantheon personnel, Drew Vachon.

Moving onto the actual network, you'll want to sign into the Network Dashboard at `/wp-admin/network/` instead of `/wp-admin/` for a full view. Each of the Dev, Test and Live environments are accessible this way. Each site on the Network represents a school except for the base `jobs.masters.com` site. They'll often like to create a new site for a new school, in which case we use the `NS Cloner` plugin to duplicate sites on the network. Depending on the site / school, its often helpful to duplicate an existing school that's already setup similarly (offers the same positions).
We use the `Pods` plugin to create new post types (Events, FAQs).
`Advanced Custom Fields` is used here to beef up the CMS.
The `Woody Snippets` plugin is used in tandem with `Advanced Custom Fields` to provide some repeater fields. Bascially saying "if this exists, show it".
They prefer using Dotdigital for their form handling, via the `Dotdigital Signup Form` plugin. In the plugin settings you can manage the API credentials, which Address Book (form) to use, and the displayed fields. It's common to run into styling issues with this form because of two particular reasons: styling overrides and placeholders. Masters often changes the field names, which in turns changes a field's #id, which is the only way to access the field to insert a placeholder attribute via jQuery. Additionally, styling overrides prevent custom styles from being applied, which forces us to use a field's #id for custom styling. See what I'm getting at here? It's a real pain in the ass. Anyway, all of the styling and jQuery can be found in the page by editing it with `Beaver Builder`.
