# Github Readme Blog Post Action

A (somewhat) simple github action that generates a set of cards for recent blog posts.

Here's an example of how it looks given the URLs for DEV Community, JavaScript Weekly, and Echo JS:

<!-- post-list:start -->
## DEV Community 👩‍💻👨‍💻

The most recent home feed on DEV Community 👩‍💻👨‍💻.

[Read more](https://dev.to)
> Last updated: Friday, September 9, 2022 at 6:22:03 AM

> Showing 5 of 12 posts.

[![Introduction to Nodejs](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Introduction_to_Nodejs.svg)](https://dev.to/savvyshivam/introduction-to-nodejs-b4c)
[![Overview of 11 AWS Developer Tools](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Overview_of_11_AWS_Developer_Tools.svg)](https://dev.to/aws-builders/overview-of-11-aws-developer-tools-53hf)
[![Beautiful button animation](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Beautiful_button_animation.svg)](https://dev.to/designyff/beautiful-button-animation-e3c)
[![Being Highly Agreeable Is All You Need To Land Your First Job In Tech.](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Being_Highly_Agreeable_Is_All_You_Need_To_Land_Your_First_Job_In_Tech..svg)](https://dev.to/wiseai/being-highly-agreeable-is-all-you-need-to-land-your-first-job-in-tech-2c2c)
[![How to Push an empty commit?](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/How_to_Push_an_empty_commit_.svg)](https://dev.to/devsimc/how-to-push-an-empty-commit-28dd)


## JavaScript Weekly

A newsletter of JavaScript articles, news and cool projects

[Read more](https://javascriptweekly.com/)
> Last updated: Friday, September 9, 2022 at 6:22:07 AM

> Showing 4 of 4 posts.

[![David's handy JS debugging tip](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/David's_handy_JS_debugging_tip.svg)](https://javascriptweekly.com/issues/604)
[![The future JavaScript features at TC39](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/The_future_JavaScript_features_at_TC39.svg)](https://javascriptweekly.com/issues/603)
[![A way to automatically generate regexes from examples](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/A_way_to_automatically_generate_regexes_from_examples.svg)](https://javascriptweekly.com/issues/602)
[![Genius misuse of WOFF 2 and Brotli to win a JavaScript contest.](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/JavaScript_Weekly/Genius_misuse_of_WOFF_2_and_Brotli_to_win_a_JavaScript_contest..svg)](https://javascriptweekly.com/issues/601)


## Echo JS

Description pending

[Read more](
http://www.echojs.com
)
> Last updated: Friday, September 9, 2022 at 6:22:09 AM

> Showing 5 of 30 posts.

[![Creating Charts with JavaScript: 13 Popular Libraries - Stack Diary](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Creating_Charts_with_JavaScript__13_Popular_Libraries_-_Stack_Diary.svg)](https://stackdiary.com/javascript-chart-libraries/)
[![Debugging Three.js Projects Just Got a Whole Lot Easier](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Debugging_Three.js_Projects_Just_Got_a_Whole_Lot_Easier.svg)](https://medium.com/@bacetools/debugging-three-js-projects-just-got-a-whole-lot-easier-451344c5b697)
[![Working with the Node.js assert Library](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Working_with_the_Node.js_assert_Library.svg)](
https://masteringjs.io/tutorials/node/assert
)
[![Introduction to Data Modeling and dbSpy2.0](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Introduction_to_Data_Modeling_and_dbSpy2.0.svg)](https://medium.com/@ejmebasser/introduction-to-data-modeling-and-dbspy2-0-fba07ada6a0b)
[![How to debug better using $ sign shortcuts in Chrome devtools - Wisdom Geek](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/How_to_debug_better_using_$_sign_shortcuts_in_Chrome_devtools_-_Wisdom_Geek.svg)](https://www.wisdomgeek.com/development/web-development/how-to-debug-better-using-sign-shortcuts-in-chrome-devtools/)


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
