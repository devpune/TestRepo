# PRODUCT-TRANSLATIONS

### What is this repository for?
This repository contains string bundles for all products, organised by product (e.g. concierge-itinerary, ada, fusion, engage) and domain (mobile, server or web).

It is designed to be used by the translations-fetcher plugin to construct string bundle files for Android, iOS and Server projects.

This repository is shared with Transperfect - a Translations service provider who clone this repository and fill in the translations.

### How to use this repository

## Branching strategy

* Use feature branches for all new features and bug fixes
* Merge feature branches into develop branch using pull requests when strings are ready to be translated. Translations that are added to the develop branch will be added to the translation process by our translation provider automatically. ONLY MERGE STRINGS THAT YOU ARE SURE WE NEED TRANSLATED. EVERY STRING COSTS US MONEY.
* Strings on develop branch will be translated by translation provider and will be pushed to the 'transperfect-translations' branch. These must be merged back to develop using a PR.
* Once your story/feature is done and has passed QA, the translations can be merged to master branch using a pull request. We need to keep a high quality, up-to-date master branch. The translations in master should pass tests, libraries that use them should build cleanly and should always be up-to-date.
* Create a release branch from master as required. Ex. When releasing a new version of a library.
* When all release activities have been complete, use cherry-picking instead of merging to select which commmits are ported back into master.
* Tag master branch after release of library to mark new version of library. Ex. for concierge-itinerary use tag "CI_3.2.0". This can be used by translation plugin to explicity set the commit to pull translations from.

NOTE: ONLY MERGE STRINGS TO DEVELOP BRANCH THAT YOU ARE SURE WE NEED TRANSLATED. EVERY STRING COSTS US MONEY.

### Format

Each string is represented as follows:

``` {
      "key":"put.dots.between.words",
      "value":"This is the value of the string"
    }
```

The key and value fields are required by the translations-fetcher plugin to enable construction of string bundle files.

However, as each messages.json file is intended to be read by translators, it's possible to add extra fields to help clarify what a string is for.

In order to maintain compatibility with the translations-fetcher, all parameters must be consistent with the following format:

* Strings: %@
* Numbers: %lu
* New Lines: \\\\n


The translations-fetcher plugin will replace these with the format required for the desired OS.

### Format for Engage Web

Each string is represented as follows using camelCase notation for keys:

``` "webComponent":{
      "key1":"string to be translated with {{variable}}",
      "key2":"string to be translated without variable"
    },
```

### How to add a new translation

1 - Update [product-translations](https://bitbucket.org/mttnow/product-translations/src/master/) with the new keys in **develop branch**.
2 - Every Friday Transperfect will pull changes on develop branch and translate the new keys. They will add the new translations to **transperfect-translations branch**.
3 - We have to manually check if everything is ok and create a PR to merge the new translations to develop.
4 - Once QA is completed, we have to create a PR to merge develop into master.