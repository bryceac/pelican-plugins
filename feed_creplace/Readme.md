# Feed CReplace #
This plugin replaces a certain string with the url for the site in feeds.

## Usage ##
To use this plugin, ensure the following are set in your `pelicanconf.py` file:

    PLUGIN_PATH = '/path/to/pelican-plugins'
    PLUGINS = [
		'feed_creplacey',
		]
    FEED_CONTENT_SUBSTITUTE = 'String to replace'

If FEED_CONTENT_SUBSTITUTE is empty or does not exist, feed should parse normally.


## Implementation Notes ##

This plugin derives `FeedCReplaceWriter` from the `Writer` class, duplicating code of the `Writer._add_item_to_the_feed` method, and is a modified version of the feed summary plugin.

When the `initialized` signal is sent, it alternates the `get_writer` method of the `Pelican` object to use `FeedCReplaceWriter` instead of `Writer`.

A little hackish, but currently this can't be done otherwise via the regular plugin methods.

 * *Initial Code (PR #36): Michelle L. Gill <michelle.lynn.gill@gmail.com>*
 * *Resumption of PR and Maintainer: Florian Jacob ( projects[PLUS]pelican[ÄT]florianjacob.de )*
