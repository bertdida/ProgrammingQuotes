<p align="center"><img src="logo/logotype-horizontal.png"></p>

# TwitterQuoteScraper

_One day I was thinking about creating a web application that displays quotations randomly. There are already lots of this on [CodePen](https://codepen.io/search/pens?q=random%20quote%20generator&page=1&order=popularity&depth=everything), but I want to experience on how to develop both of its frontend and backend functionalities. I need the data first, and I assume Twitter can help me with this!_

TwitterQuoteScraper is a command line tool with a purpose to help in scraping quotations from the desired Twitter accounts.

## Prerequisites

- Python 3.6
- [Pipenv](https://github.com/pypa/pipenv)
- [Twitter API Keys and Tokens](https://developer.twitter.com/en/docs/basics/authentication/guides/access-tokens.html)
- [Google service account](https://developers.google.com/sheets/api/guides/authorizing) (optional)

## Installation

1. Download and extract the [zip file](https://github.com/bertdida/TwitterQuoteScraper/archive/master.zip) or use Git to clone this repository.
2. Inside the directory open a terminal and run `pipenv install`.

## Basic Usage

To get started you must first create a JSON file that holds your Twitter app's credentials (see `creds/twitter.json` for a template).

### Local file

Run `python app.py --twitter-creds creds/twitter.json local_file -h` to view help.

The command below will scrape [@prog_quotes](https://twitter.com/prog_quotes) account and will generate a `prog_quotes.csv`. If you want to get a JSON file instead, override the default file type by adding `--file-type json`.

```shell
python app.py --twitter-creds creds/twitter.json local_file --twitter-handles @prog_quotes
```

### Google spreadsheet

Run `python app.py --twitter-creds creds/twitter.json google_sheet -h` to view help.

1. Make a copy of the [template spreadsheet](https://docs.google.com/spreadsheets/d/1S8xsN8D6nD2KM5-oSZOIFnuw3zvP4_WRZLHMMfbsbPk/edit?usp=sharing).
2. Share the spreadsheet with the `client_email` you can find inside your Google service account's JSON file.
3. Note your [spreadsheet ID](https://developers.google.com/sheets/api/guides/concepts#spreadsheet_id).

The command below will scrape [@prog_quotes](https://twitter.com/prog_quotes) account and will save to the specified spreadsheet sorted by phrase column alphabetically.

```shell
python app.py --twitter-creds creds/twitter.json google_sheet --service-account creds/google.json --spreadsheet-id YOUR_SPREADSHEETS_ID
```
