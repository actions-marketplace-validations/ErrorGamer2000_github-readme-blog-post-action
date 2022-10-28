# Github Readme Blog Post Action

A (somewhat) simple github action that generates a set of cards for recent blog posts.

Here's an example of how it looks given the URLs for DEV Community, JavaScript Weekly, and Echo JS:

<!-- post-list:start -->
## DEV Community 👩‍💻👨‍💻

The most recent home feed on DEV Community 👩‍💻👨‍💻.

[Read more](https://dev.to)
> Last updated: Friday, October 28, 2022 at 6:24:22 AM

> Showing 5 of 12 posts.

[![Ultimate Guide To Create an API Documentation with Examples](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Ultimate_Guide_To_Create_an_API_Documentation_with_Examples.svg)](https://dev.to/document360/ultimate-guide-to-create-an-api-documentation-with-examples-2n2d)
[![Use this to explain how to use your app | Flutter PRO tip #2](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Use_this_to_explain_how_to_use_your_app___Flutter_PRO_tip__2.svg)](https://dev.to/svprdga/use-this-to-explain-how-to-use-your-app-flutter-pro-tip-2-1clp)
[![New to Open Source? Know everything you need to!](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/New_to_Open_Source__Know_everything_you_need_to!.svg)](https://dev.to/prakhartiwari0/new-to-open-source-know-everything-you-need-to-3gl2)
[![Dynamic forms with Formik and React JS. 📝](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Dynamic_forms_with_Formik_and_React_JS._📝.svg)](https://dev.to/franklin030601/dynamic-forms-with-formik-and-react-js-3no1)
[![The Economy of Low-Code](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/The_Economy_of_Low-Code.svg)](https://dev.to/polterguy/the-economy-of-low-code-507h)


## JavaScript Weekly

A newsletter of JavaScript articles, news and cool projects

[Read more](https://javascriptweekly.com/)
> Last updated: Friday, October 28, 2022 at 6:24:26 AM

> Showing 4 of 4 posts.

[![🪜 Decorating with Dr. Axel](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/🪜_Decorating_with_Dr._Axel.svg)](https://javascriptweekly.com/issues/611)
[![Node to keep an eye on your code](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/Node_to_keep_an_eye_on_your_code.svg)](https://javascriptweekly.com/issues/610)
[![Axios turns 1.0; TypeScript turns 10](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/Axios_turns_1.0;_TypeScript_turns_10.svg)](https://javascriptweekly.com/issues/609)
[![How TypeScript 4.9 satisfies](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/How_TypeScript_4.9_satisfies.svg)](https://javascriptweekly.com/issues/608)


## Echo JS

Description pending

[Read more](
http://www.echojs.com
)
> Last updated: Friday, October 28, 2022 at 6:24:31 AM

> Showing 5 of 30 posts.

[![Javascript: forEach Is Not A Function and What To Do?](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Javascript__forEach_Is_Not_A_Function_and_What_To_Do_.svg)](https://nerdleveltech.com/javascript-foreach-is-not-a-function-and-what-to-do/)
[![Deno 1.27: Major IDE Improvements](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Deno_1.27__Major_IDE_Improvements.svg)](https://deno.com/blog/v1.27)
[![Validate Emails using Regex in JavaScript](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Validate_Emails_using_Regex_in_JavaScript.svg)](
https://masteringjs.io/tutorials/fundamentals/email-regex
)
[![GitHub - oslabs-beta/LiveStateDB: A real time state management library that allows for state to subscribe and update based on changes from a specific portion of a database.](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/GitHub_-_oslabs-beta_LiveStateDB__A_real_time_state_management_library_that_allows_for_state_to_subscribe_and_update_based_on_changes_from_a_specific_portion_of_a_database..svg)](https://github.com/oslabs-beta/LiveStateDB)
[![Svelvet 4.0 — The power of HTML is now inside your nodes!](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Svelvet_4.0_—_The_power_of_HTML_is_now_inside_your_nodes!.svg)](https://medium.com/@MauricioACastro/svelvet-4-0-the-power-of-html-is-now-inside-your-nodes-3d96823096e3)


<!-- post-list:end -->

# Quick Start

This action runs out-of-the-box, with only one provided input.

Create a `.yml` file with the desired filename, and paste the following:

```yml
on:
  push:
  schedule:
    - cron: "0 */6 * * *"
jobs:
  blog:
    runs-on: ubuntu-latest
    name: Fetch and Generate Blog Posts
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Generate
        uses: ErrorGamer2000/github-readme-blog-post-action@v1
        with:
          feed_urls: FEEDS
      - name: Commit changed files
        uses: stefanzweifel/git-auto-commit-action@v4
        with:
          commit_message: Save Generated Blog Posts
          skip_checkout: true
```

Replace the FEEDS with a comma-seperated list of [RSS feed](https://rss.com/blog/how-do-rss-feeds-work/) URLs, add

```md
<!-- blog-post-list:start -->
<!-- blog-post-list:end -->
```

in the README where you want the list, and **_BAM!_** You have yourself an automatic action that runs every 6 hours and when you change any of the files in your readme!

# Inputs

<table>
  <thead>
    <tr>
      <th>Option Name</th>
      <th>Type</th>
      <th>Default Value</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>feed_urls</code></td>
      <td><code>string</code></td>
      <td><code>""</code></td>
      <td>A (comma-seperated) list of RSS feed URLs to load posts from. This is the only required input.</td>
    </tr>
    <tr>
      <td><code>max_posts_per_url</code></td>
      <td><code>number</code></td>
      <td><code>5</code></td>
      <td>The maximum number of posts to show for each feed. If the number of posts is less than this, then all of the posts will be shown.</td>
    </tr>
    <tr>
      <td><code>position_indicator</code></td>
      <td><code>string</code></td>
      <td><code>blog-post-list</code></td>
      <td>The text of the comments that the action uses to inject the images into the README file. Everything between the two comments in the form <code>&lt;!-- position_indicator:start --&gt;</code> and <code>&lt;!-- position_indicator:end --&gt;</code> is replaced. Changing this can allow you to use multiple configurations for different feeds by using different markers for each.</td>
    </tr>
    <tr>
      <td><code>show_feed_data</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the generated markdown describing the feed, which includes the title of the feed, the description of the feed, the <code>Read More</code> link, the last updated date, and the post count. Each of these can also be individually toggled with the following options. This will override any of the specific options, so it is better to disable/enable them specifically if you want to remove some elements.</td>
    </tr>
    <tr>
      <td><code>show_feed_title</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the header containing the title of the feed. This will be formatted as an <code>h2</code> header. An option to customize this header will be in a future update.</td>
    </tr>
    <tr>
      <td><code>show_feed_description</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the title of the feed that is provided by the RSS feed.</td>
    </tr>
    <tr>
      <td><code>show_read_more</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the <code>Read More</code> link under the feed description.</td>
    </tr>
    <tr>
      <td><code>show_last_updated_date</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the date and time of the last update of the list.</td>
    </tr>
    <tr>
      <td><code>show_post_count</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the number of posts shown and the total number of posts provided by the RSS feed.</td>
    </tr>
    <tr>
      <td><code>show_post_date</code></td>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
      <td>Whether or not to show the date of each post on the card.</td>
    </tr>
    <tr>
      <td><code>locale</code></td>
      <td><code>string</code></td>
      <td><code>"en"</code></td>
      <td>The locale of the project. This is used <strong>purely</strong> for formatting the dates of the cards and last update.</td>
    </tr>
    <tr>
      <td><code>time_zone</code></td>
      <td><code>string</code></td>
      <td><code>"UTC"</code></td>
      <td>A valid time zone to use for the last updated date.</td>
    </tr>
    <tr>
      <td><code>output_dir</code></td>
      <td><code>string</code></td>
      <td><code>"blog-post-list-output"</code></td>
      <td>The directory to store the post card images in. Must be in the root directory (i.e. no path separators <code>/</code> or <code>\</code>) and cannot include the characters <code>/\?%*:|"&lt;&gt;</code>.</td>
    </tr>
<!--
    <tr>
      <td><code></code></td>
      <td><cde></cde></td>
      <td><code></code></td>
      <td></td>
    </tr>
-->
  </tbody>
</table>

# Usage Notes

- Make sure that you use an action that will commit changed files to the repository after this action has run, so that the files actually get changed.
- I am a solo dev, and will get back to you as soon as I can, so expect to wait several weeks depending on how many other issues there are.
- Enjoy and share! 🤗
