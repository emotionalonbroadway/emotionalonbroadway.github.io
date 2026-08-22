# How-To

This page will cover how to set up an mkdocs patch from beginning to end. 

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
3. On the newly cloned repository, click the `Actions` tab and approve running any workflows. 
4. Click the `Settings` tab, click `Pages` on the left-hand side of the screen, under `Build and Deployment`, locate the `Branch` section, change it to `gh-pages` and click `Save`
4. The GitHub repository is now configured and your website will be published shortly at `GITHUBUSERNAME.github.io`

## How to Edit the Website

In the `docs` folder, you can click `Create new file` and create any new file with the format `PAGENAME.md` for the filename. `md` files are Markdown files which in turn are fancy text files. You can look at https://www.markdownguide.org/basic-syntax/ for an example of how to format a Markdown file. At its basic core, it's another text file so if you ignore any Markdown formatting, you can input any text and the website will output it as is. 

Once you have written your page, click `Commit changes`, give the commit a descriptive name ("added page name to website"). 

You will now need to add the new page to the navigation. In the root folder, click `mkdocs.yml`, click the pencil icon to edit the page. Under `nav`, you will see a list of basic pages. 

To add your new page as its entirely own section, under `Wants: wants.md`, add a new line, title your page (how it will appear on the website) with a `:` after the title and the name of the newly created file. For example:

```
nav: 
  - Home: "index.md"
  - Haves: "have.md"
  - Wants: "wants.md"
  - My New Fancy Page: page.md
```

However, if you would like to create a child page, you could do something like the following instead:

```
nav: 
  - Home: "index.md"
  - Haves: "have.md"
  - Wants: "wants.md"
    - My New Fancy Page: page.md
```

"My New Fancy Page" would appear as a child of the "Wants" page on your website. 

Once you have added the new page, go ahead and click `Commit changes...`, give the commit a descriptive name and click `Commit Changes`. Your website will soon be deployed with the new page now visible under the navigation. 

## CSV Files

In the `docs/tables` folder, you may upload any CSV file and the website can directly output these as raw pages. 

Open the `docs/tables` folder on a web browser, click `Add file`, and upload your CSV file.

On the page you would like to use the CSV file, use the following format (copy and paste and tweak):

```
{{ read_csv('TABLENAME.csv', usecols=[0,1,2,3,4,5,6,9,10,17], na_filter=False) }}
```

Update `TABLENAME` to match the name of your CSV file. The `usecols` refers to the columns on the CSV file directly. You can open it in something like Excel or LibreOffice Calc (free alternative to Excel) and see which columns correspond to which numbers. 

## Documentation

There is a vast amount of documentation available at https://squidfunk.github.io/mkdocs-material/setup/, to customize every aspect of the website to your liking. 
