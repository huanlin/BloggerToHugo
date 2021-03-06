# BloggerToHugo
A simple console app for converting Blogger exported xml file to Hugo html files.

This program is based on Alan Tsai's [mhat-consoleapp-blogger_to_wyam](https://github.com/alantsai/mhat-consoleapp-blogger_to_wyam), which is for Wyam. Many thanks to Alan Tsai!

For Windows only, .NET Framework 4.5 is required.

## Usage

Rather than simply compile and run this console app, please clone or download the source code and follow instructions below:

1. Modify [Constanst.cs](https://github.com/huanlin/blogger-to-hugo/blob/master/source/Constants.cs) for your needs.
2. Build the project.
3. Export posts from your Google Blogger site, rename it from "blog-yyyy-mm-dd.xml" to "blog.xml" and copy it to the project output directory, e.g. `bin\Debug\net452`.
4. Run the application and see if there are html files generated under sub-directory "post." You might need to edit "categories" and "tags" property for each html file.
5. Copy the generated html files to your Hugo web site's content\post\ directory. Done.

*Note:*

- If you didn't rename your xml file to "blog.xml" (step 3), you'll need to add command line arguments when you run this application.
- My blog posts are using images from Google Drive, so I don't need to download images files, and I simply commented those code .
- I don't care much about SEO, so I'm not sure whether those "data:blog.canonicalUrl" strings work or not.

## Find and Replace More Text

After html files are generated, you might want to do some more modification using a find and replace tool. For example:

- Find "/s640/" and replace them with "/s1600/" so that original images are displayed instead of small sized version. Do the same with "/s400/".
- Find "`<a name="more"></a>`" and replace them with "`<!--more-->`" so that "read more" can be displayed in your posts.

## Using Aliases to Redirect Old URLs

You might want to add `aliases` property in the front matter in each html file, so that requests to old URLs can be redirected to new URLs. You can find more description about [aliases on Hugo web site](https://gohugo.io/content-management/urls/#aliases). Here is an example that worked for me.

    `aliases: ["/2013/01/aspnet-web-api-exception-handling.html"]`

That's it. If anything missed here, feel free to create an issue.
