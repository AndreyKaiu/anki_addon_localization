# anki_addon_localization
A method for localizing Anki add-ons using a special, translator-friendly format


  Everyone has trouble translating programs into another language. I used ".json" before, but both AI and Google Translate love to break things—commas, quotation marks, and in some languages, even naming words without spaces doesn't save variables; it'll just translate them anyway.
So it's easier to tell the AI ​​not to translate lines starting with === or !!! at all. And in other lines to be translated, if you encounter the $ symbol, everything up to the next $ symbol can't be translated.
At least that makes things a bit simpler.
The first line contains: ```!!! === $ $ ; setting, block separator, variable start and end, comment start marker```
This allows you to flexibly change the settings to accommodate any symbols convenient for your language or your text.
Everything is easily typed in a text file; no need to specifically type "\n" for a new line. Of course, you need to ensure that your text doesn't contain the $ symbol or any other character (others, since it's not necessarily just one character, but one or more) you specify. Make sure the beginning of the line isn't the two specified words "!!!" and "===" (or any other words you specify). If the line contains the $ symbol, you can change the setting above, for example:
```!!! === « » ;```
and now, instead of $, you can use «Name of the block that can be inserted.»

For more details, see the file "adv_settings.py," which you can run to see the example output.

Here's the second test from there:
```
!!! === $ $ ; setting, block separator, variable start and end, comment start marker
=== company ; company information
"Volkswagen Group"
=== text1 ; when it works
$company$ works
===
!!! *** { } % let's change the setting
*** text2 % check for two
{text1} successfully. Contacts: {company}, tel.:12345
***
!!! === $ $ ; let's return the setting
=== text3 ; output for three
$text2$ The financial performance of $company$ is not very good. $text1$ has been having some difficulties lately!
```

