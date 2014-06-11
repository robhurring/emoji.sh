# Emojis for your shell! :+1:

This is a goofy little hack that reads a list of emoji's from OSX's special characters panel (Edit -> Special Characters [opt+cmd+space] to open).

Inside the `CharacterPalette.app` there is a sqlite database that has a ton of characters. I'm pulling a specific range which seems to have a large chunk of emojis. This is then spit out into an `export` format that your shell can then source.

*Disclaimer:* You will probably never need this.

## Usage

1. Clone this repo somewhere
2. Link the `emoji.sh` somewhere: `ln -s emoji.sh $HOME`
3. In your ~/.bashrc add the following: `source $HOME/emoji.sh`
4. Make sure your terminal app can handle UTF-8 and all that jazz

You can then `source ~/.bashrc` and now you're ready to rock!

To use an emoji in the terminal, simply `echo` it out: `echo $EMOJI_BEER_MUG w00t!`

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
