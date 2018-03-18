---
title: Create a peer-to-peer blog
section: tutorials
sectionTitle: Tutorials
order: 1
---

Creating a blog on Beaker is easy to do with a static site generator. In this
tutorial, we’ll use [Jekyll](https://jekyllrb.com/). Start by following their instructions for creating a new blog:

<figcaption class="code">bash</figcaption>
```bash
~$ gem install jekyll bundler
~$ jekyll new my-awesome-p2p-blog
~$ cd my-awesome-p2p-blog
```

My blog is located at `~/my-awesome-p2p-blog`, which means that the site it generates is located at `~/my-awesome-p2p-blog/_site`.

Update your `_config.yml`:

<figcaption class="code">_config.yml</figcaption>
```yaml
# Blog settings
title: My Awesome P2P Blog
email: "pfrazee@foo.com"
description: Software, decentralization, and peer-to-peer systems.
twitter_username: pfrazee
github_username:  pfrazee

# Build settings
markdown: kramdown
theme: minima
gems:
  - jekyll-feed
exclude:
  - Gemfile
  - Gemfile.lock
```

Run `jekyll build` to generate your site’s files:

<figcaption class="code">bash</figcaption>
```bash
~/my-awesome-p2p-blog $ jekyll build

Configuration file: /Users/paulfrazee/my-awesome-p2p-blog/_config.yml
            Source: /Users/paulfrazee/my-awesome-p2p-blog
       Destination: /Users/paulfrazee/my-awesome-p2p-blog/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.854 seconds.
 Auto-regeneration: disabled. Use --watch to enable.
```

Now, let’s create the site in Beaker. Open the dropdown menu in Beaker, and select “New site”:

<figure>
<img data-src="/img/docs/tut-create-a-blog/new-site.jpg" >
<figcaption>Click "New site" in the dropdown menu</figcaption>
</figure>

Fill in the title and description of your blog:

<figure>
<img data-src="/img/docs/tut-create-a-blog/site-details.jpg" >
<figcaption>Set the title and description</figcaption>
</figure>

Click "Create site" and Beaker will take you to the library page for your site:

<figure>
<img data-src="/img/docs/tut-create-a-blog/library-page.jpg" >
<figcaption>Your new site in your Library</figcaption>
</figure>

By default, Beaker creates a new folder for you under the `~/Sites` directory. In this case, we want to pick our own folder, because we want to use the `./_site` folder within our Jekyll blog. To select the `_site` directory, click "Change folder" in the Library dropdown menu.

<figure>
<img data-src="/img/docs/tut-create-a-blog/change-folder.jpg" >
<figcaption>Select "Change folder" in the library dropdown</figcaption>
</figure>

For my blog, I set the folder to `~/my-awesome-p2p-blog/_site`:

<figure>
<img data-src="/img/docs/tut-create-a-blog/select-folder.jpg" >
<figcaption>Choose ~/my-awesome-p2p-blog/_site</figcaption>
</figure>

You’ll see Beaker's staging area populate with the new changes immediately.

<figure>
<img data-src="/img/docs/tut-create-a-blog/staging-area.jpg" >
<figcaption>The staging area shows unpublished changes</figcaption>
</figure>

We'll publish in a moment. First, let's click “View site” to see how the site looks.

<figure>
<img data-src="/img/docs/tut-create-a-blog/view-site.png">
<figcaption>The unpublished site</figcaption>
</figure>

OK! It looks pretty good so far. Check out the [Jekyll documentation](https://jekyllrb.com/docs/home/) to learn how to author content and change the styles.

Jekyll has a builtin command, `bundle exec jekyll serve`, for previewing your site on a local development server. But Beaker serves your site for you at its Dat URL, so you just need Jekyll to do the build process:

<figcaption class="code">bash</figcaption>
```bash
~/my-awesome-p2p-blog$ jekyll build --watch
```

There’s one last step before you can share your blog; you need to publish your files. Back in the Library page for your blog, you should see your changes listed:

<figure>
<img data-src="/img/docs/tut-create-a-blog/staging-area.jpg" >
<figcaption>The staging area shows unpublished changes</figcaption>
</figure>

This is the staging area. It shows all the local changes that you’ve made, but haven’t yet published. Until you publish, only you will be able to see the changes.

Click “Publish,” and the changes will be committed to your site.

<figure>
<img data-src="/img/docs/tut-create-a-blog/published.jpg" >
<figcaption>Click “Publish” and the site is ready</figcaption>
</figure>

Now you can share the URL to anybody using Beaker, and keep your computer online, and they’ll be able to download the site.

One last tip: once you have `jekyll build --watch` running, Jekyll will automatically generate a new version of your site when you make updates. If you want Beaker to automatically reload the page too, you can turn on Live reloading:

<figure>
<img data-src="/img/docs/tut-create-a-blog/live-reloading.jpg" >
<figcaption>Turn on live reloading</figcaption>
</figure>

Navigate to the site, click the dropdown menu in the top right, then click “Turn on live reloading.” You'll see a lightning symbol in the URL bar. Now, any time you make a change, the site will auto-refresh.