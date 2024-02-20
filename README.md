# Disclaimer

**This repository is community supported and not maintained by Mattermost. Mattermost disclaims liability for integrations, including Third Party Integrations and Mattermost Integrations. Integrations may be modified or discontinued at any time.**

# Mattermost Profanity Filter Plugin (Beta)

[![Build Status](https://img.shields.io/circleci/project/github/mattermost/mattermost-plugin-profanity-filter/master.svg)](https://circleci.com/gh/mattermost/mattermost-plugin-profanity-filter)
[![Code Coverage](https://img.shields.io/codecov/c/github/mattermost/mattermost-plugin-profanity-filter/master.svg)](https://codecov.io/gh/mattermost/mattermost-plugin-profanity-filter)
[![Release](https://img.shields.io/github/v/release/mattermost/mattermost-plugin-profanity-filter)](https://github.com/mattermost/mattermost-plugin-profanity-filter/releases/latest)
[![HW](https://img.shields.io/github/issues/mattermost/mattermost-plugin-profanity-filter/Up%20For%20Grabs?color=dark%20green&label=Help%20Wanted)](https://github.com/mattermost/mattermost-plugin-profanity-filter/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3A%22Up+For+Grabs%22+label%3A%22Help+Wanted%22)

This plugin allows you to censor profanity on your Mattermost server. The plugin checks all messages for matches against the configured "Bad words list" before they are posted to any channel. The characters in any word matches are replaced with a series of "\*"s.

**Supported Mattermost Server Versions: 5.2+**

## Plugin Marketplace

1. Go to **Main Menu > Plugin Marketplace** in Mattermost.
2. Search for "Profanity Filter" or manually find the plugin from the list and click **Install**
3. Once the plugin has downloaded and been installed, click **Configure**.

## Manual Installation

1. Go to the [releases page of this Github repository](https://github.com/mattermost/mattermost-plugin-profanity-filter/releases) and download the latest release for your Mattermost server.
2. Upload this file in the Mattermost System Console under **System Console > Plugins > Management** to install the plugin. To learn more about how to upload a plugin, [see the documentation](https://docs.mattermost.com/administration/plugins.html#plugin-uploads).
3. Activate the plugin at **System Console > Plugins > Management**.

### Usage

You can edit the bad words list in **System Console > Plugins > Profanity Filter > Bad words list**.
In this list, you can use Regular Expressions to match bad words. For example, `bad[[:space:]]?word` will match both `badword` and `bad word`.

Choose to either censor the bad words with a character or reject the post with a custom warning message:

![Post rejected by the plugin](./images/post-rejected.gif)

![Post censored by the plugin](./images/post-censored.gif)

## Development

This plugin contains both a server and web app portion. Read our documentation about the [Developer Workflow](https://developers.mattermost.com/integrate/plugins/developer-workflow/) and [Developer Setup](https://developers.mattermost.com/integrate/plugins/developer-setup/) for more information about developing and extending plugins.

### Releasing new versions

The version of a plugin is determined at compile time, automatically populating a `version` field in the [plugin manifest](plugin.json):
* If the current commit matches a tag, the version will match after stripping any leading `v`, e.g. `1.3.1`.
* Otherwise, the version will combine the nearest tag with `git rev-parse --short HEAD`, e.g. `1.3.1+d06e53e1`.
* If there is no version tag, an empty version will be combined with the short hash, e.g. `0.0.0+76081421`.

To disable this behaviour, manually populate and maintain the `version` field.
