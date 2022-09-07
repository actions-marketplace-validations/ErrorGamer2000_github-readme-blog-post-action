# Github Readme Blog Post Action

A (somewhat) simple github action that generates a set of cards for recent blog posts.

Here's an example of how it looks given the URLs for DEV Community, JavaScript Weekly, and Echo JS:

<!-- post-list:start -->
## DEV Community 👩‍💻👨‍💻

The most recent home feed on DEV Community 👩‍💻👨‍💻.

[Read more](https://dev.to)
> Last updated: Wednesday, September 7, 2022 at 6:22:37 AM

> Showing 5 of 12 posts.

[![How to get started with Filament](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/How_to_get_started_with_Filament.svg)](https://dev.to/ameliniya_/how-to-get-started-with-filament-2fi1)
[![Core JavaScript: Var vs. Let vs. Const](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Core_JavaScript__Var_vs._Let_vs._Const.svg)](https://dev.to/ioanat94/core-javascript-var-vs-let-vs-const-39d7)
[![Do you know about any USEFUL web3/blockchain projects? I fail to find any...](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/Do_you_know_about_any_USEFUL_web3_blockchain_projects__I_fail_to_find_any....svg)](https://dev.to/nombrekeff/do-you-know-about-any-useful-web3blockchain-projects-i-fail-to-find-any-4c62)
[![The 31 Reserved Keywords in Solidity](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/The_31_Reserved_Keywords_in_Solidity.svg)](https://dev.to/koha/the-31-reserved-keywords-in-solidity-bda)
[![5 Free Resources to Learn Python](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/DEV_Community_👩‍💻👨‍💻/5_Free_Resources_to_Learn_Python.svg)](https://dev.to/onlydevs_/5-free-resources-to-learn-python-50k4)


## JavaScript Weekly

A newsletter of JavaScript articles, news and cool projects

[Read more](https://javascriptweekly.com/)
> Last updated: Wednesday, September 7, 2022 at 6:22:39 AM

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
> Last updated: Wednesday, September 7, 2022 at 6:22:44 AM

> Showing 5 of 30 posts.

[![Bihar’s artists seek help from Lalit Kala Akademi to tide over Covid crisis](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Bihar’s_artists_seek_help_from_Lalit_Kala_Akademi_to_tide_over_Covid_crisis.svg)](https://www.hindustantimes.com/cities/patna-news/bihars-artists-seek-help-from-lalit-kala-akademi-to-tide-over-covid-crisis-101626063460374.html)
[![Looking to develop own Airbnb Like App?](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Looking_to_develop_own_Airbnb_Like_App_.svg)](https://www.apptunix.com/solutions/airbnb-like-app/)
[![As U.S. Sanctions Loomed, a Tycoon ‘Mopped Up’ Zimbabwe’s Scarce Dollars, and Acquired a Lucrative Platinum Mine - OCCRP](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/As_U.S._Sanctions_Loomed__a_Tycoon_‘Mopped_Up’_Zimbabwe’s_Scarce_Dollars__and_Acquired_a_Lucrative_Platinum_Mine_-_OCCRP.svg)](https://www.occrp.org/en/investigations/as-us-sanctions-loomed-a-tycoon-mopped-up-zimbabwes-scarce-dollars-and-acquired-a-lucrative-platinum-mine)
[![Breaking The Factory Pattern In 2 Ways - Design Patterns In TypeScript - Talking HighTech](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/Breaking_The_Factory_Pattern_In_2_Ways_-_Design_Patterns_In_TypeScript_-_Talking_HighTech.svg)](https://www.talkinghightech.com/en/typescript-factory-pattern/)
[![How to Write Polyfill of Filter Method](https://raw.githubusercontent.com/ErrorGamer2000/github-readme-blog-post-action/main/generated_files/_Echo_JS_/How_to_Write_Polyfill_of_Filter_Method.svg)](https://www.youtube.com/watch?v=rSAyBK8pkCA)


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
