# MyScripts

[Official Site](http://unitkay.wordpress.com/myscripts/) • Official Site: [Translation](http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Funitkay.wordpress.com%2Fmyscripts%2F) • MyScripts: [iTunes Link](https://itunes.apple.com/us/app/myscripts/id492086539?mt=8) • MyScripts LE: [iTunes Link](https://itunes.apple.com/us/app/myscripts-le/id556253271?mt=8)

## URL Scheme

### Function

    MyScripts://
        Parameter
            Example

Myscripts :/ / tag: URL scheme for selecting tag search terms myscripts :/ / search script = URL-encoded search term or the myscripts :/ / search title = URL-encoded:?? Search list screen script URL scheme? Number of columns Number of rows & column = myscripts :/ / moveCursorTo line =:? (valid only when you run the script from the edit screen) URL scheme for moving cursor tag name name = URL-encoded

Documentation: [Official](http://unitkay.wordpress.com/myscripts/) • Official [Translation](http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Funitkay.wordpress.com%2Fmyscripts%2F)• [App Lookup](http://applookup.com/App/492086539)

---

Drafts to 1Password protocol converter





---

MyScripts Help

Thank you for downloading MyScripts.

MyScripts allows you to create and execute javascript to process the text in the clipboard or the text from other apps (via Open In / MyScripts URL).

The processed text can be passed to other apps, copied back to the clipboard, opened as a URL, or displayed on the screen.

The script editor has a code completion feature that allows you to create a script easily and quickly.

If you have any comments or you have found any bugs, please make a comment at the support website or contact via Twitter.

Please check out other iOS apps by Unit Kay, too.

Creating a script

1. Tap the add button at the bottom right in the list screen to display the script editor.

2. Input the name of the script at the top left of the editor screen.

3. Select one of the actions from the buttons at the top right. The action is executed against the result of the script. The action of each button is:

 📲 opens in other apps.
 📝 copies to the clipboard.
 ⚡ calls openURL().
 ⚠ displays in a screen.

4. Input the script in the text area. The string in the last line, such as "<string>"; or <variable that holds a string>;, is passed to the action that you selected in Step 3.
Predefined variables

TEXT holds the text to be processed. If the script is for processing scripts, TEXT contains the body of the target script.

ENCTEXT holds the URL-encoded TEXT.

SONG holds the info of the song being played on the device. title / albumTitle / artist attributes are available.

ENCSONG holds the URL-encoded SONG. title / albumTitle / artist attributes are available.

TARGET holds the string of the action name specified to this script: "openin" / "copy" / "openurl" / "info". You can change the destination action by changing the value of this variable. If null is specified, no action will be performed.

If IS_HTML is set to true from the script, it means that the resulting text is HTML. If the text is passed to other apps, it will be opened as HTML, if it is displayed on the debug screen, it will be displayed as HTML.

If IS_ASYNC is set to true from the script, asynchronous code can be executed. After the processing is done, ASYNC_DONE("<text>") must be called.

FILENAME specifies the file name for the Open In action. If MyScripts is launched by other apps via Open In, FILENAME contains the file name of the input file.

CLIPBOARD holds the text in the clipboard. When TEXT parameter contains the value of the text parameter of a URL, CLIPBOARD can be used to get the text in the clipboard.

ENCCLIPBOARD holds URL-encoded CLIPBOARD.

IP_ADDRESS holds the IP address of the device. WiFi has priority over 3G. Null if the device is not connected to the network.

IS_BACKGROUND returns if the script is running in the background.

SCRIPT_TITLE holds the title of the target script when executing a script for processing scripts.

SCRIPT_ENCTITLE holds the URL-encoded SCRIPT_TITLE.

SCRIPT_TARGET holds the action name of the target script when executing a script for processing scripts.

OPTION holds the string passed by myscripts://run?option=URLEncodedString or myscripts://listing?option=URLEncodedString. It is valid for the MyScripts life until it is overwritten by another URL scheme invocation.

ENCOPTION holds the URL-encoded OPTION.

Statements

#IMPORT <script name>

Imports the named script. Multiple scripts can be specified by multiple #IMPORTs. (One script for one line.) The imported scripts are executed before the current script.

#LIB

Instructs the code completion to learn only the names of the functions in the script. Otherwise, it will learn every word in the script. The statement must be written in the beginning of the first line of the script. This statement is mainly for the performance issue when there is a big script.

#PROCESS_SCRIPT

Declares this script as a script for processing scripts. If daclared, it can be invoked from the menu in the editor.

#HTML

Declares this script as an HTML file.

COPY("<text>"[, <message>])

Copies the text to the clipboard. You can display a message instead of the copied text by specifying the message. This operation is actually performed after the script is executed. If "" is specified in the message, the copy dialog itself will not be displayed.

ASYNC_DONE("<text>")

After IS_ASYNC is set to true and asynchronous code is executed, ASYNC_DONE("<text>") must be called to execute the action against the text.

SAVE_JSON("<key>", obj)

Saves obj as JSON data associated with the key. It returns true if successful, otherwise false. Please note that the storage is shared among all the scripts; if the same key is used, the data will be overwritten.

LOAD_JSON("<key>")

Loads the data associated with the key. If the data is not found, null is returned.

LOGOUT("<log>")

Outputs the log to the debug console.

Background execution

Check the checkbox next to a script in the script list and MyScripts will monitor the clipboard for ten minutes while other app is running.

When you copy any text in the other app, MyScripts will run the script with the new text in the clipboard and notify the result to you.

If the specified action is 📝, the clipboard will be updated immediately. For other actions, the action will be executed after you select the notification message.

Other functions in the editor

Keyword list can be displayed by tapping the add button in the editor screen. Keywords such as TEXT, ENCTEXT, and #IMPORT can be easily entered from this list. The import statement in the script imported is ignored.

You can test the script by tapping the play button. The result will be displayed in a debug screen regardless of the selected action.

By tapping the action button, you can:
- generate and copy the link to register the script
- generate and copy the link to run the script using the text in the clipboard
- generate and copy the link to run the script by passing the text via a parameter in the link
- pass the script to other applications via Open In
- execute a script for processing scripts

Others

- You can pass a text file from other applications to MyScripts via Open In. You can run a script against the file, add the file as a new script, or update the existing script with the file. Note that you need to select the target action manually when adding as new script.

- You can use iTunes to save files to the document directory of MyScripts. These files can be used from the output of the script when the target action is ⚠ and the output is displayed as HTML.

- The document directory is preloaded with jquery.js, bootstrap/js/bootstrap.js, jqm/jquery.mobile.js. It can be used from the output of the script when the output is displayed as HTML.

Third party

Contains TextExpander engine library, Copyright © 2009-2010 SmileOnMyMac, LLC. TextExpander is a trademark of SmileOnMyMac, LLC

jQuery JavaScript Library v1.7.1
http://jquery.com/
Copyright 2011, John Resig
Dual licensed under the MIT or GPL Version 2 licenses.
http://jquery.org/license

Includes Sizzle.js
http://sizzlejs.com/
Copyright 2011, The Dojo Foundation
Released under the MIT, BSD, and GPL Licenses.

jQuery Mobile Framework 1.1.0
http://jquerymobile.com/
Copyright 2011 (c) jQuery Project
Dual licensed under the MIT or GPL Version 2 licenses.
http://jquery.org/license

Twitter Bootstrap v2.0.3
http://twitter.github.com/bootstrap/
Copyright 2012 Twitter, Inc.
Licensed under the Apache License, Version 2.0.
http://www.apache.org/licenses/LICENSE-2.0

Toolbar icons by Joseph Wain / 
http://glyphish.com
©2012 Unit Kay
(Web / Twitter / iOS Apps)