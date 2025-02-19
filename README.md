# Addis Restaurant website

# How to make updates to the site for free
It's likely that after some time I would have removed the wordpress site from AWS Lightsail and exported the project using the `All-in-one-wp-migration` plugin. If we need to make an update then we'll need to spawn a new wordpress instance on AWS Lightsail and import the latest exported file. 

## How to start an instance on AWS Lightsail
- Go to AWS console and search for Lightsail service.
- Create a new instance
- Connect to terminal
- run `cat bitnami_credentials`. This will show the username and password for your dashboard, but they will be temporary. I'll explain in a minute.
- Go to `ip_address.com/wp-admin` and enter credentials.

## How to import .wpress file
- Go to plugins and deactivate the `All-in-One-WP-Migration` plugin if activated.
- Import the 6.7 version of the `All-in-One-WP-Migration` plugin. You can find it here: `https://victorchinedu.com/rollback`
- Activate the plugin.
- Go to Tools -> Plugin File Editor
- On the top right select the drop down and look for the `All-in-One-WP-Migration` plugin.
- On the right sidebar select the `constants.php` file then search for `Max file`
- Update the value from 28 -> 40 then press `Update File` on the bottom. This should increase the file size you can upload.
- Go to the `All-in-One-WP-Migration` plugin and import the zip file of the website.
- Note: You'll likely get logged out but the old password won't work because it's tied to password from the initial instance. The password is in 1password under `addis-restaurant`

## Install Simply Static
- This will export your project into static files and directories: `index.html`, `wp-content`, `wp-includes`. 
- When we're done making updates and ready to export go to the `Simply Static` settings.
- Under Settings go to General
- Make sure to set `Replacing URLS` to `Offline Usage` and enable `Force URL replacements`
- Scroll down to `Save Settings`
- On the left side bar go to `Activity Log`
- Then press `Generate` on the top-left sidebar.
- The process should begin and you'll see a link in the Activity log section to download the site files.
- You'll have to dig into directory to find the 3 files/directories mentioned earlier and they will be your static website.

## How to host on Github Pages
- Go to Github
- Create a new public repo and commit the 3 files/directories to the repo.
- Go the Settings -> Pages
- Under `Branch` select the `main` branch
- This should make your app available under the following domain: `https://www.megulo25.github.io/PROJECT_NAME`
- You can configure it to work for a custom domain.

## How to configure a custom domain on Github Pages

Done! The site should be available with the changes! It may take a while for the servers to update the cache.
