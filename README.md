# Mixpanel / Google Tag Manager custom tag template.

These are the source files for the Google Tag Manager custom template designed for deploying and implementing the Mixpanel JavaScript SDK.

## Manual installation

Once the template has been published, you can locate it in the [Google Tag Manager community template gallery](https://tagmanager.google.com/gallery/#/), and you can install it via the Google Tag Manager user interface.

To **manually install** the template, e.g. for debugging prior to the changes being published in the community template gallery, follow these steps.

1. Download the `./src/template.tpl` file locally.
2. Open a **Google Tag Manager** *Web* container via the [Google Tag Manager user interface](https://tagmanager.google.com/). Preferably one that is already deployed on a website where you can test the template with real use cases.
3. In the GTM UI, browse to **Templates**, and in the box titled **Tag Templates**, click the blue **New** button.
4. Once the **Template Editor** is open, click the menu (three vertical dots) in the top-right corner of the window and choose **Import**.
5. Select the `template.tpl` file you downloaded locally.
6. Follow the prompts. Once import is complete, the Template Editor should show the Mixpanel template in edit mode.
7. Click **Save** to save the template, and then proceed to close the Template Editor.
8. In the GTM UI, browse to **Tags** and click **New** to create a new tag.
9. From the list of available tag templates, choose the **Mixpanel** template you just imported to the container.

## How the template works

The template replicates the functionality of the [Mixpanel JS SDK](https://developer.mixpanel.com/docs/javascript-full-api-reference).

It utilizes a custom created [JavaScript wrapper](https://github.com/mixpanel/mixpanel-js-wrapper) to overcome the restrictions GTM's templating system places on available JavaScript APIs.

### Initialization

When *any* Mixpanel GTM tag fires, it automatically tries to initialize a new instance using the **Initialization Options** configured in the tag. If an instance with the given name has already been initialized on the page, the initialization process is skipped.

This way the user doesn't need to worry about initialization. They just need to make sure that the Initialization Options are configured consistently across the tags.

### Sending Mixpanel commands

After adding the **Project Token** to its respective field, you need to choose what **type** of tag to use. Each type corresponds with some command you can use with the Mixpanel JS API.

> Note that `'init'`, `'push'` and any of the "getter" commands are not supported in the template.

The more complex tag types (`group`, `people`, and `track`) are elevated to the top of the drop-down menu with the `-` prefix to separate them from the other commands.

Once you select a tag type, additional options may appear. Consult the SDK reference for details on how to configure these options.

### Firing the tag

Once you're happy with your tag, you need to add a **Trigger** to it. For example, to trigger it with every page load, add the **Add Pages** trigger to it.

Save the tag when done.

### Test

You can then enter **Preview** mode by clicking the blue **Preview** button in the Google Tag Manager UI. This opens a new tab with your website running the GTM container, and you can proceed to test the Mixpanel tag as if the container were published. In the Tag Assistant Preview tab, you can see additional information about the trigger events, tags, and variables that fire while you are browsing the page in Preview mode.
