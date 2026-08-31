# How-To

This page will cover how to set up an mkdocs website (a copy of the website you are currently on) from beginning to end. 

## Github Account Creation

1. Create a GitHub account, https://github.com/, with the username being what you want your site name to be. 
    * For example, if you would like your site to be monalisastradingemporium, use this as your username when registering for a GitHub account.

## GitHub Repository Creation
    
1. After creating an account, open the following repository, https://github.com/emotionalonbroadway/mkdocs-base-template on a browser of your choice. 
2. In the top right of the page, click the "Fork" button. The details of this step are **very important:**
    * In the repository name box, type `GITHUBUSERNAME.github.io`
        * If your username is `monalisastradingemporium`, type `monalisastradingemporium.github.io`, make sure you have the formatting correct!     
        * If your username has any capital letters in it, make sure to only use     lowercase letters here. If your username is `MonaLisasTradingEmporium`, use `monalisastradingemporium`
    * **Uncheck** the `Copy the main branch only` box
3. On the newly cloned repository, click the `Actions` tab and you will see a warning that says "Workflows aren’t being run on this forked repository", **click** "I understand my workflows, go ahead and enable them". 
4. Click the `Settings` tab, click `Pages` on the left-hand side of the screen, under `Build and Deployment`, locate the `Branch` section, change it to `gh-pages` and click `Save`
4. The GitHub repository is now configured and your website will be published shortly at `GITHUBUSERNAME.github.io`

## How to Edit the Website

In the `docs` folder, you can click `Add File` > `Create new file` and create any new file with the format `PAGENAME.md` for the filename. `md` files are Markdown files which in turn are fancy text files. You can look at https://www.markdownguide.org/basic-syntax/ for an example of how to format a Markdown file. At its basic core, it's another text file so if you ignore any Markdown formatting, you can input any text and the website will output it as is. 

Once you have written your page, click `Commit changes`, give the commit a descriptive name ("added page name to website"). 

You will now need to add the new page to the navigation. In the root folder, click `properdocs.yml`, click the pencil icon to edit the page. Under `nav`, you will see a list of basic pages. 

To add your new page as its entirely own section, under `Wants: wants.md`, add a new line, title your page (how it will appear on the website) with a `:` after the title and the name of the newly created file. For any pages with spaces, make sure to surround the page title in quotes. For example:

```
nav: 
  - Home: "index.md"
  - Haves: "haves.md"
  - Wants: "wants.md"
  - "My New Fancy Page": page.md
```

However, if you would like to create a child page, you could do something like the following instead:

```
nav: 
  - Home: "index.md"
  - Haves: "haves.md"
  - Wants: "wants.md"
    - "My New Fancy Page": page.md
```

"My New Fancy Page" would appear as a child of the "Wants" page on your website. 

Once you have added the new page, go ahead and click `Commit changes...`, give the commit a descriptive name and click `Commit Changes`. Your website will soon be deployed with the new page now visible under the navigation. 

## Site Template

When editing `properdocs.yml`, there are a couple of template lines that should be updated:

```
site_name: SITENAME
site_url: https://SITENAME.github.io/
```

Update the `site_name` to your username (recommended) or any keyword of your choice. Update the site_url to your domain name, `https://USERNAME.github.io`

```
  palette:
    scheme: slate
    primary: pink
  icon: 
    logo: material/emoticon-cry-outline
```

The scheme and primary color can be updated to your liking. See this page, https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/, for a full example of how to update these two lines.

The logo appears on the top-left of your website. You may search https://fonts.google.com/icons to find a logo of your choice and update the `logo` line accordingly. 

## CSV Files

In the `docs/tables` folder, you may upload any CSV file and the website can directly output these as raw pages. 

Open the `docs/tables` folder on a web browser, click `Add file`, and upload your CSV file.

On the page you would like to use the CSV file, use the following format (copy and paste and tweak):

{% raw %}
```
{{ read_csv('TABLENAME.csv', usecols=[0,1,2,3,4,5,6,9,10,17], na_filter=False) }}
```
{% endraw %}

Update `TABLENAME` to match the name of your CSV file. The `usecols` refers to the columns on the CSV file directly. You can open it in something like Excel or LibreOffice Calc (free alternative to Excel) and see which columns correspond to which numbers. 

Do note that you can add text above and below the CSV. A page does not need to **solely consist** of just the CSV output. 

## Deployment

Whenever you make a commit (editing or creating a new file), GitHub will run CI which is what builds your website. You can click the "Actions" tab after pushing a commit to see what GitHub is doing and to see when your new commit will be pushed to your website. If an error occurs, you can click the most recent failed run and read through the error messages to see if you can determine what is causing the error. Sometimes it's a very simple typo and can be fixed quickly. 

## Domain Name

Your newly available website will be deployed at `USERNAME.github.io`. You can see an example of that here, the website you are looking at, is deployed at `https://emotionalonbroadway.github.io/`. You can freely share your newly deployed website with other traders. 

If you would ever like to push to a custom domain (ex - going directly to a `.com` address without the `.github.io` attached), you can take a look at GitHub's documentation, https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages, to see if it is something you would be interested in doing. 

## Documentation

There is a vast amount of documentation available at https://squidfunk.github.io/mkdocs-material/setup/, to customize every aspect of the website to your liking. 
