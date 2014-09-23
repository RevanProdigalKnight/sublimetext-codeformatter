CodeFormatter
=============


CodeFormatter is a Sublime Text 2/3 plugin that supports format (beautify) source code.


CodeFormatter has support for the following languages:

* PHP - By PHP_Beautifier
* JavaScript/JSON - By JSBeautifier
* HTML - By JSBeautifier
* CSS - By JSBeautifier
* Python - By PythonTidy (only ST2)



Installing
----------
**With the Package Control plugin:** The easiest way to install CodeFormatter is through Package Control, which can be found at this site: http://wbond.net/sublime_packages/package_control

Once you install Package Control, restart Sublime Text and bring up the Command Palette (`Command+Shift+P` on OS X, `Control+Shift+P` on Linux/Windows). Select "Package Control: Install Package", wait while Package Control fetches the latest package list, then select CodeFormatter when the list appears. The advantage of using this method is that Package Control will automatically keep CodeFormatter up to date with the latest version.

**Without Git:** Download the latest source from [GitHub](https://github.com/akalongman/sublimetext-codeformatter) and copy the CodeFormatter folder to your Sublime Text "Packages" directory.

**With Git:** Clone the repository in your Sublime Text "Packages" directory:

    git clone https://github.com/akalongman/sublimetext-codeformatter.git CodeFormatter


The "Packages" directory is located at:

* OS X:

        ST2: ~/Library/Application Support/Sublime Text 2/Packages/
        ST3: ~/Library/Application Support/Sublime Text 3/Packages/

* Linux:

        ST2: ~/.config/sublime-text-2/Packages/
        ST3: ~/.config/sublime-text-3/Packages/

* Windows:

        ST2: %APPDATA%/Sublime Text 2/Packages/
        ST3: %APPDATA%/Sublime Text 3/Packages/


## Formatter-specific notes
Following are notes specific to individual formatters that you should be aware of:
### PHP
PHP - Used custom fork (which works without pear) of [Php_beautifier] (http://pear.php.net/package/PHP_Beautifier) package by Claudio Bustos and Jesús Espino.

Getting and installing PHP - http://www.php.net/manual/en/install.general.php

On Linux/OSx after installation of package, you must set chmod +x to file php_beautifier in folder %PACKAGESDIR%/CodeFormatter/codeformatter/lib/phpbeautifier

Language specific options:
```js
	// Path for PHP executable, e.g. "C:/Program Files/PHP/php.exe". If empty, uses command "php" from system environments
	"codeformatter_php_path": "",
	"codeformatter_php_options":
	{
		"indent_size": 4, // Indent size
		"indent_with_tabs": false, // Indent with tabs or spaces
		"indent_style": "k&r", // Indent the code in k&r, allman, gnu or whitesmiths style
		"newline_before_comment": true, // add new line before comment block
		// Add new lines after o before specific contents The settings are 'before' and 'after'. As value, use a comma separated list of contents or tokens, e.g. switch,while,for,foreach,try,namespace,T_INTERFACE
		"new_line_before": "",
		"new_line_after": "",
		"format_array_nested": false, // Indent the array structures Ex.
		"pear": true, // Format the code to make it compatible with PEAR Coding Standards
		"pear_add_header": "", // Add one of the standard PEAR comment header (php, bsd, apache, lgpl, pear) or any file as licence header.
		// Two extra options allows to break the spec about newline before braces on function, classes and traits:
		"pear_newline_class": true, // need enabled pear option
		"pear_newline_trait": true, // need enabled pear option
		"pear_newline_function": false, // need enabled pear option
		"pear_switch_without_indent": false, // Disable extra switch identation
		"lowercase": false, // Lowercase all control structures. Such as TRUE, FALSE, SWITCH and more
		"fluent": false, // Create fluent style for multi-level object access.
		"list_class_function": false, // Create a list of functions and classes in the script By default, this Filter puts the list at the beggining of the script.
		"equals_align": false, // Align the equals symbols in contiguous lines.
		"phpbb": false // Format the code to make it compatible with phpBB Coding Standards (if enabled, overrides some another options)
	},
```



### Javascript/JSON
Javascript/JSON/JSONP - used [JSBeautifier] (http://jsbeautifier.org/) by Einar Lielmanis

Language specific options:
```js
	"codeformatter_js_options":
	{
		"indent_size": 4, // indentation size
		"indent_char": " ", // Indent character
		"indent_with_tabs": false, // Indent with one tab (overrides indent_size and indent_char options)
		"preserve_newlines": false, // whether existing line breaks should be preserved,
		"max_preserve_newlines": 10, // maximum number of line breaks to be preserved in one chunk
		"space_in_paren": false, // Add padding spaces within paren, ie. f( a, b )
		"e4x": false, // Pass E4X xml literals through untouched
		"jslint_happy": false, // if true, then jslint-stricter mode is enforced. Example function () vs function()
		"brace_style": "collapse", // "collapse" | "expand" | "end-expand". put braces on the same line as control statements (default), or put braces on own line (Allman / ANSI style), or just put end braces on own line.
		"keep_array_indentation": false, // keep array identation.
		"keep_function_indentation": false, // keep function identation.
		"eval_code": false, // eval code
		"unescape_strings": false, // Decode printable characters encoded in xNN notation
		"wrap_line_length": 0, // Wrap lines at next opportunity after N characters
		"break_chained_methods": false // Break chained method calls across subsequent lines
	}
```

### HTML
HTML - used custom python port, please use it with caution, feature in early beta

Language specific options:
```js
	"codeformatter_html_options":
	{
		"indent_size": 4, // indentation size
		"indent_char": " ", // Indentation character
		"indent_with_tabs": false, // Indent with one tab (overrides indent_size and indent_char options)
		"preserve_newlines": false, // Preserve existing line-breaks
		"max_preserve_newlines": 10, // Maximum number of line-breaks to be preserved in one chunk
		"indent_tags": "html|head|body|div|nav|ul|ol|dl|li|table|thead|tbody|tr|th|td|blockquote|select|form|option|optgroup|fieldset|legend|label|header|section|aside|footer|figure|video" // List of tags (defaults to indent) that should be reformatted. Example "div|p|li|table"
	}
```

### CSS
CSS - used [JSBeautifier] (http://jsbeautifier.org/) by Einar Lielmanis and Style Css by Harutyun Amirjanyan

Language specific options:
```js
	"codeformatter_css_options":
	{
		"indent_size": 4, // Indentation size
		"indent_char": " ", // Indentation character
		"indent_with_tabs": false, // Indent with one tab (overrides indent_size and indent_char options)
		"selector_separator_newline": false, // Add new lines after selector separators
		"end_with_newline": false // Add new line of end in file
	}
```
### Python
CSS - used [PythonTidy] (https://pypi.python.org/pypi/PythonTidy/) by Chuck Rhode

Language specific options:
```js
	"codeformatter_python_options":
	{
		"indent_size": 1, // indentation size
		"indent_with_tabs": true, // Indent with tabs or spaces
		"max_char": 80, // Width of output lines in characters.
		"assignment": " = ", // This is how the assignment operator is to appear.
		"function_param_assignment": "=", // This is how function-parameter assignment should appear.
		"function_param_sep": ", ", // This is how function parameters are separated.
		"list_sep": ", ", // This is how list items are separated.
		"subscript_sep": "=", // This is how subscripts are separated.
		"dict_colon": ": ", // This separates dictionary keys from values.
		"slice_colon": ":", // this separates the start:end indices of slices.
		"comment_prefix": "# ", // This is the sentinel that marks the beginning of a commentary string.
		"shebang": "#!/usr/bin/env python", // Hashbang, a line-one comment naming the Python interpreter to Unix shells.
		"boilerplate": "", // Standard code block (if any). This is inserted after the module doc string on output.
		"blank_line": "", // This is how a blank line is to appear (up to the newline character).
		"keep_blank_lines": true, // If true, preserve one blank where blank(s) are encountered.
		"add_blank_lines_around_comments": true, // If true, set off comment blocks with blanks.
		"add_blank_line_after_doc_string": true, // If true, add blank line after doc strings.
		"max_seps_func_def": 3, // Split lines containing longer function definitions.
		"max_seps_func_ref": 5, // Split lines containing longer function calls.
		"max_seps_series": 5, // Split lines containing longer lists or tuples.
		"max_seps_dict": 3, // Split lines containing longer dictionary definitions.
		"max_lines_before_split_lit": 2, // Split string literals containing more newline characters.
		"left_margin": "", // This is how the left margin is to appear.
		"normalize_doc_strings": false, // If true, normalize white space in doc strings.
		"leftjust_doc_strings": false, // If true, left justify doc strings.
		"wrap_doc_strings": false, // If true, wrap doc strings to max_char.
		"leftjust_comments": false, // If true, left justify comments.
		"wrap_comments": false, // If true, wrap comments to max_char.
		"double_quoted_strings": false, // If true, use quotes instead of apostrophes for string literals.
		"single_quoted_strings": false, // If true, use apostrophes instead of quotes for string literals.
		"can_split_strings": false, // If true, longer strings are split at the max_char.
		"doc_tab_replacement": "....", // This literal replaces tab characters in doc strings and comments.

		// Optionally preserve unassigned constants so that code to be tidied
		// may contain blocks of commented-out lines that have been no-op'ed
		// with leading and trailing triple quotes.  Python scripts may declare
		// constants without assigning them to a variables, but CodeFormatter
		// considers this wasteful and normally elides them.
		"keep_unassigned_constants": false,

		// Optionally omit parentheses around tuples, which are superfluous
		// after all.  Normal CodeFormatter behavior will be still to include them
		// as a sort of tuple display analogous to list displays, dict
		// displays, and yet-to-come set displays.
		"parenthesize_tuple_display": true,

		// When CodeFormatter splits longer lines because max_seps
		// are exceeded, the statement normally is closed before the margin is
		// restored.  The closing bracket, brace, or parenthesis is placed at the
		// current indent level.  This looks ugly to "C" programmers.  When
		// java_style_list_dedent is True, the closing bracket, brace, or
		// parenthesis is brought back left to the indent level of the enclosing
		// statement.
		"java_style_list_dedent": false
	}
```

Usage
-----
Tools -> Command Palette (`Cmd+Shift+P` or `Ctrl+Shift+P`) and type `Format Code`.

You can set up your own key combo for this, by going to Preferences -> Key Bindings - User, and adding a command in that huge array: `{ "keys": ["ctrl+alt+f"], "command": "code_formatter" },`. Default keybinding is `ctrl+alt+f`. You can use any other key you want, thought most of them are already taken.

TODO
-----
Add other languages support:
* Python (for ST3)
* Perl
* Ruby

Pull requests are welcome.

Troubleshooting
---------------
If you like living on the edge, please report any bugs you find on the [CodeFormatter issues](https://github.com/akalongman/sublimetext-codeformatter/issues) page.
