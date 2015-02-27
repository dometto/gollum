Let's use this page to meet a nice consensus about everything, divide work, and much more...

## Some info

### Devel

1. (S)CSS is located in `lib/gollum/app/css`.
2. Changes are visible on the next refresh (no need to restart).
3. Errors are redirected to Sinatra's output and can be found in between logs of HTTP requests.

### SASS structure

* `_base` contains basic variables and global wiki layout - elements with IDs and classes prefixed with `wiki-`. Reason: all of this is used by every page (and if not, in some corner case like the editor, no harm is done).
* `_structure` contains classes for context-independent elements - containers & components defining STRUCTURE. For example: layouts with floating elements.
* `_features` should IMHO actually be renamed to something like `_util`. Useful classes and mixins solving various problems.
* Each wiki page gets its own `.scss` stylesheet.

## Some rules

Let's strive towards theming as much as possible:

1. Stylesheets dedicated to pages should only contain styles for THAT page. If a mixin has the potential to be applied in different contexts and pages, place it in a partial and make it global. When consolidating old CSS code, try to look whether the same looking blocks of style are used elsewhere.
2. When following #1, also pay attention to flexibility and templates that already exist. For example, a color of an error message may not be restricted to a certain page and a predefined value for it may already exist.
3. Don't link stylesheets of pages through `@import`.
4. Naming conventions. Let's try to use a single naming convention throughout the whole stage - all variables, mixins, IDs, classes and so on will use hyphens as separators while keywords will emphasize structure:
	* The **first keyword** should be something denoting the **LEVEL** in one way or another. E.g. `wiki` (global wiki thingy), `editor` (page-specific thingy), `float-layout` (global layout thingy).
	* The **first few keywords** should say the **WHAT** in terms of DOM structure. E.g. `editor-top-bar`.
	* After that, the details should follow - `size`, `color`, ...
5. If a block of old CSS stinks and the same could be done a lot simpler, let's do so and inject mustache templates with a little more decency.
6. **If there're more of us, let's communicate and use issues to further discuss this thing, problems & patterns we encounter.**

This way, after the old code is consolidated and the new code gets theming-ready, eventual integration with `compass` should be a lot easier. At that point, `compass` would be next awesome step in Gollum's style evolution.

## TODO

... add some

## Pending issues from original repository

... add some