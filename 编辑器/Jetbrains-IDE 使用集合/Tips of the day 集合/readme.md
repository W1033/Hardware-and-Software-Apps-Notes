# Tip of the day

*Create: 2024.07.02*

*Last Edit: 2024.07.03*

## Code completion

When using code **completion**, you can accept the current **selection** in the suggestions list with   `⇧` `⌘` `↩ Return`  . IntelliJ IDEA will not only insert the selected string, but also turn the current code construct into a **syntactically** correct one (balance **parentheses**, add missing braces and semicolons, and so on).

<img src="./readme.assets/image-20240703121143338.png" alt="image-20240703121143338" style="zoom:50%;" />


## Show usages 

You can view the list of all usages of a class, method or variable across the whole project, and quickly navigate to the selected item. Place the caret at a symbol and press `⌥` `⌘` `F7` (Edit | Find Usages | Show Usages).

To jump to a usage, select it from the list and press `↩ Return`.

<img src="./readme.assets/image-20240702090935446.png" alt="image-20240702090935446" style="zoom:50%;" />



## The Rename refactoring 

You can easily rename your classes, methods, and variables with automatic correction of all places where they are used.

Position the caret at the symbol you want to rename, and press `⇧` `F6` (Refactor | Rename). Type the new name and press `↩ Return`.

<img src="./readme.assets/image-20240702090957097.png" alt="image-20240702090957097" style="zoom:50%;" />



## Improve code with context actions

Press `⌥` `↩ Return` in the editor to fix a highlighted error or warning, improve, or optimize a code construct. For some intention actions, you can open a preview or an action description by pressing `F1` (View | Quick Documentation).

<img src="./readme.assets/image-20240702091017547.png" alt="image-20240702091017547" style="zoom:50%;" />

## Preview search results

You can use the Preview area of the Find in Files dialog (**`⇧`** **`⌘`** **`F`**) for quicker search without leaving the dialog. The Preview dialog displays the first 100 results. 

<img src="./readme.assets/image-20240702091037655.png" alt="image-20240702091037655" style="zoom:50%;" />



## Speed search in tree views

Speed search is available in all tree views, for example, in the Project tool window. Start typing, and you'll quickly locate the necessary item.

<img src="./readme.assets/image-20240702091048845.png" alt="image-20240702091048845" style="zoom:50%;" />



## Comment and uncomment code

Use shortcuts to comment and uncomment lines and blocks of code:

**`⌘`** **`/`**: for single line comments (  //...  )

**`⌥`** **`⌘`** **`/`**: for block comments (  /*...*/  )

<img src="./readme.assets/image-20240702091104414.png" alt="image-20240702091104414" style="zoom:50%;" />



## Expand code selection

Press **`⌥`** **`↑`** to expand code selection. Each time you press **`⌥`** **`↑`**, the selection expands to other areas of code.

For example, the selection expands from a method name to the expression calling this method, then to the whole statement, then to the containing block, and so on.

<img src="./readme.assets/image-20240702091116786.png" alt="image-20240702091116786" style="zoom:50%;" />



## Live templates

Use live templates to insert frequent code constructs. 

<img src="./readme.assets/image-20240703135104426.png" alt="image-20240703135104426" style="zoom:50%;" />

For example, type `psvm` and press `Tab` to insert the `main()` method declaration template, then type `sout` to insert a print statement.


## Surround code fragments

You can quickly wrap a code block in useful constructs. Select it in the editor and press **`⌥`** **`⌘`** **`T`** (Code | Surround With).

The list of available options or wrappers is context-sensitive and depends on the language. 

<img src="./readme.assets/image-20240703135335049.png" alt="image-20240703135335049" style="zoom:50%;" />



## Code generation

IntelliJ IDEA can generate getter and setter methods for fields in your class. With the caret inside the class, press **`⌘`** **`N`** (Code | Generate).

<img src="./readme.assets/image-20240703140912220.png" alt="image-20240703140912220" style="zoom:50%;" />


## Version Control

IntelliJ IDEA provides out-of-the-box integration with the following version control systems: Git, Mercurial, Subversion, and Perforce.

Version your application to collaborate on it, as well as to eliminate the risks of storing all of your codebase locally. Press **`⌘`** **`9`** to view the history of the changes in the project or press **`⌘`** **`K`** to send your local changes to the repository.

<img src="./readme.assets/image-20240703141633699.png" alt="image-20240703141633699" style="zoom:50%;" />



## Paste from the clipboard history

Press **`⇧`** **`⌘`** **`V`** to select the text fragment that you have previously copied to the clipboard.



## Move statements up and down

The **Code | Move Statement Up/Down** actions are useful for reorganizing code lines, for example for bringing a variable declaration closer to the variable usage.
Select a code fragment and press `⇧` `⌘` `↑` or `⇧` `⌘` `↓`.
When nothing is selected in the editor, the line at the caret position will be moved.

<img src="./readme.assets/image-20240703142143889.png" alt="image-20240703142143889" style="zoom:50%;" />



## Quick Definitioin

Press **`⌥`** **`␣`** (View | Quick Definition) to preview the definition or content of the symbol at the caret, without opening it in a separate editor tab.

<img src="./readme.assets/image-20240703162810649.png" alt="image-20240703162810649" style="zoom:50%;" />



## Switch scheme

You can apply a different code style, coloring scheme, or keymap with a single keystroke right from the editor. Press `⌃` `\`` (View | Quick Switch Scheme) to specify the scheme you want to switch to.



## Show file structure
You can quickly navigate within the current file with `⌘` `F12` (Navigate | File Structure).

File structure shows the list of members of the current class. To navigate to an element, select it and press `↩ Return` or `⌘` `↓`.

To easily locate an item in the list, start typing its name.

<img src="./readme.assets/image-20240703165942141.png" alt="image-20240703165942141" style="zoom:50%;" />



## Select In

To quickly select the currently edited element (a class, file, method, or field) in another view, press `⌥` `F1` or call Navigate | Select In.

<img src="./readme.assets/image-20240702091148373.png" alt="image-20240702091148373" style="zoom:50%;" />



## Postfix code completion

Postfix code completion is applied from right to left to avoid backward caret jumps when coding. Type a dot   .   after the code fragment that you want to change and select the desired option.

To see the suggestion list with postfix templates, you can also press   ⌘   J  .

<img src="./readme.assets/image-20240702091214918.png" alt="image-20240702091214918" style="zoom:50%;" />



## View Git blame annotations

Git annotations show detailed information on the origin of each code line (right-click the gutter and select Annotate with Git Blame).

Right-click an annotation and choose Show Diff to review the differences between the current and the previous version of the file.

<img src="./readme.assets/image-20240702091225395.png" alt="image-20240702091225395" style="zoom:50%;" />



## Reformat code

To reformat code according to the current code style settings, select Code | Reformat Code from the main menu or press   ⌥   ⌘   L  .

<img src="./readme.assets/image-20240702091236729.png" alt="image-20240702091236729" style="zoom:50%;" />



## Create code constructs with completion

You can create code constructs using statement completion. Start typing a method declaration, a method call or a statement such as   if  ,   do -while  ,   try -catch  , or   return  . Press   ⇧   ⌘   ↩ Return   to complete the statement into a syntactically correct construct.

<img src="./readme.assets/image-20240702091249922.png" alt="image-20240702091249922" style="zoom:50%;" />



## Navigate to implementation

To navigate to the implementations of an abstract method, position the caret at its usage or its name in the declaration and press   ⌥   ⌘   B  .

<img src="./readme.assets/image-20240703170514555.png" alt="image-20240703170514555" style="zoom:50%;" />



## Find usages

Press   ⌥   F7   to quickly locate all occurrences of code referencing the symbol at the caret, no matter if the symbol is a part of a class, method, field, parameter, or another statement.

<img src="./readme.assets/image-20240702091543257.png" alt="image-20240702091543257" style="zoom:50%;" />



## Search Everywhere

Press   Shift   twice to search for files, actions, symbols, UI elements, Git branches and comments across your project. Pressing double   Shift   again, will extend the search to non-project items.

Use tabs or direct shortcuts   ⌘   O   for classes,   ⇧   ⌘   O   for files,   ⌥   ⌘   O   for symbols, and   ⇧   ⌘   A   for actions to narrow your search results.

 <img src="./readme.assets/image-20240703195313356.png" alt="image-20240703195313356" style="zoom:50%;" />



## Project tool window

Press   ⌘   1   to open the Project tool window and switch focus to it.

<img src="./readme.assets/image-20240703200742826.png" alt="image-20240703200742826" style="zoom:50%;" />



## Debugger

If you want to log program state during debugging, use non-suspending breakpoints. Select the expression that you want to log, hold `Shift` , and click the gutter at the line where the expression should be logged.

In the example, `sent.size()` will be logged upon reaching line 24.

<img src="./readme.assets/image-20240702091504720.png" alt="image-20240702091504720" style="zoom:50%;" />


## Duplicate a code block or a line

Press `⌘` `D` in the editor to duplicate the selected code block, or the current line when no block is selected.

<img src="./readme.assets/image-20240703201203266.png" alt="image-20240703201203266" style="zoom:50%;" />



## Override methods

You can easily override methods of the base class by pressing   ⌃   O   (Code | Override Methods).

To implement methods of the interfaces (or of the abstract base class) that the current class implements, press   ⌃   I   (Code | Implement Methods).

<img src="./readme.assets/image-20240703201455627.png" alt="image-20240703201455627" style="zoom:50%;" />



##  Evaluate expression

You can execute expressions or reassign values for variables while your script is stopped by a breakpoint. The Evaluate Expression functionality helps you to obtain additional details about the program state or test various scenarios at runtime.

•  If the expression is present in the code, hold   Alt   (on Windows and Linux) or   ⌥   (on macOS) and click it. If you want to evaluate a specific code fragment, select it before clicking. 

•  To evaluate an arbitrary expression, select Run | Debugging Actions | Evaluate Expression. A separate dialog opens that supports various constructs including loops, assignments, lambdas, and so on. 

<img src="./readme.assets/image-20240702091454797.png" alt="image-20240702091454797" style="zoom:50%;" />



##  Extract Variable refactoring

The Extract Variable refactoring wraps a selected expression into a variable. It adds a new variable declaration and uses the expression as an initializer. Select an expression and press   ⌥   ⌘   V   (Refactor | Extract/Introduce | Variable).

<img src="./readme.assets/image-20240702091533284.png" alt="image-20240702091533284" style="zoom:50%;" />

## Camel case in code completion

You can narrow down a list of code completion suggestions by using camel case prefixes.

<img src="./readme.assets/image-20240702091312954.png" alt="image-20240702091312954" style="zoom:50%;" />



## View recent files

Press   ⌘   E   (View | Recent Files) to view the list of recently opened files.

<img src="./readme.assets/image-20240702091429296.png" alt="image-20240702091429296" style="zoom:50%;" />



## Quick code documentation

To quickly see the documentation for a class or method at the caret, press   F1   (View | Quick Documentation).

<img src="./readme.assets/image-20240702091412932.png" alt="image-20240702091412932" style="zoom:50%;" />



## Access VCS-related options

Press `^` `V` to access all VCS-related commands available in the current context.

<img src="./readme.assets/image-20240702091559168.png" alt="image-20240702091559168" style="zoom:50%;" /> 



## Change focus in tool windows

  ⎋ Esc   in any tool window moves the focus to the editor.

  ⇧   ⎋ Esc   moves the focus to the editor and hides the current or the last active tool window.

  F12   moves the focus from the editor to the last focused tool window.

<img src="./readme.assets/image-20240702091514145.png" alt="image-20240702091514145" style="zoom:50%;" />



##  Local History 

Local History lets you track all changes to files, classes, methods, or any code fragments and roll back to any stable point if necessary. To view local history, from the main menu, select File | Current File | Show History.

<img src="./readme.assets/image-20240702091523838.png" alt="image-20240702091523838" style="zoom:50%;" />



## Compare files and folders

To compare any two files or folders, select them in the Project tool window and press   ⌘   D  .

<img src="./readme.assets/image-20240703203406238.png" alt="image-20240703203406238" style="zoom:50%;" />



## Wildcards in Search Everywhere

Use text patterns in Search Everywhere (double   Shift  ) when searching for a class, file, or symbol. Use   `*`   and   `space`  :

`*` stands for any number of arbitrary characters.

 `space` marks the end of a pattern. The preceding string is considered not just a prefix but a whole pattern.

<img src="./readme.assets/image-20240703203532660.png" alt="image-20240703203532660" style="zoom:50%;" />



##  Type-Matching code completion

类型匹配代码完成（/补全）

The type-matching code completion analyzes the expected type of the whole expression and helps to find methods and variables that are applicable in the current context. It works after the   return   keyword, in an assignment, in the argument list of a method call, and other places. Press   ⌃   ⇧   ␣   (Code | Code Completion | Type-Matching) to get the completion list filtered.<img src="./readme.assets/image-20240702090833626.png" alt="image-20240702090833626" style="zoom:50%;" />



## Type-Matching completion
Invoking Type-Matching code completion (  ⌃   ⇧   ␣  ) twice will search for chained expressions of the expected type.

<img src="./readme.assets/image-20240703203653023.png" alt="image-20240703203653023" style="zoom:50%;" />



## Horizontal scroll

To scroll a file horizontally, turn the mouse wheel while keeping `Shift` pressed.

<img src="./readme.assets/image-20240703203751088.png" alt="image-20240703203751088" style="zoom:50%;" />



## View inheritance hierarchy
To see the inheritance hierarchy for the selected class, press   ⌃   H   (Navigate | Type Hierarchy). You can also invoke the hierarchy view directly from the editor to see the hierarchy for the currently edited class.

<img src="./readme.assets/image-20240703204049542.png" alt="image-20240703204049542" style="zoom:50%;" />



## Fix a Javadoc
If a method signature has changed, IntelliJ IDEA highlights the documentation comment tags that ran out of sync and suggests a quick-fix:

<img src="./readme.assets/image-20240703204202781.png" alt="image-20240703204202781" style="zoom:50%;" />



## Highlight usages within a file
Press   ⇧   ⌘   F7   (Edit | Find Usages | Highlight Usages in File) to quickly highlight usages of a certain variable in the current file.

Press   ⌘   G   and   ⇧   ⌘   G   to navigate through the highlighted usages. Press   ⎋ Esc   to remove highlighting.

<img src="./readme.assets/image-20240703204233086.png" alt="image-20240703204233086" style="zoom:50%;" />



## Inspect code
Use Code | Inspect Code to run code analysis for the whole project or a custom scope and examine the results in a separate window.

<img src="./readme.assets/image-20240703204312510.png" alt="image-20240703204312510" style="zoom:50%;" />



## Camel case in Search Everywhere

Use camel case in the Search Everywhere popup (double   Shift  ) to filter the list of results when searching for a class, file, or symbol.

<img src="./readme.assets/image-20240703204420942.png" alt="image-20240703204420942" style="zoom:50%;" />



## Copy a path or a reference

Use the Edit | Copy Path/Reference action to insert a reference to a field/method/class/file into the current position in the editor.

Position the caret within the   myMethod   method name and press   ⌥   ⇧   ⌘   C  .
To paste the reference, press   ⌘   V  .

You can also copy references in the Go to Class/Go to Symbol/Go to File dialogs. Press   ⌘   C   on any element in the lookup list.

<img src="./readme.assets/image-20240703204520463.png" alt="image-20240703204520463" style="zoom:50%;" />



## Close all editor tabs
To close all editor tabs, right-click a tab and select Close All Tabs.

To close all tabs except the active one, press   Alt   (on Windows and Linux) /   ⌥   (on macOS) and click the Close button on the active tab.

<img src="./readme.assets/image-20240703204605894.png" alt="image-20240703204605894" style="zoom:50%;" />



## Copy a class
Use Refactor | Copy Class to create a class which is a copy of the selected class.

This is useful when you need to create a class similar to an existing one, and it's not feasible to put shared functionality in a common superclass.

<img src="./readme.assets/image-20240703204712424.png" alt="image-20240703204712424" style="zoom:50%;" />



## Compare with clipboard
To compare active editor with the clipboard contents, right-click anywhere in the editor and choose Compare with Clipboard from the context menu.

<img src="./readme.assets/image-20240703204748398.png" alt="image-20240703204748398" style="zoom:50%;" />



## Code completion 2

Code completion suggests the choices that are reachable from the current caret position as you type. Press   ⌃   ␣   twice to also see inaccessible classes and members.

<img src="./readme.assets/image-20240703204856335.png" alt="image-20240703204856335" style="zoom:50%;" />



## Code completion 3

You can accept the current selection in the code completion suggestions list with the period key (.), comma (,), semicolon (;), space, and some other characters.

<img src="./readme.assets/image-20240703204933135.png" alt="image-20240703204933135" style="zoom:50%;" />



## Recent search history
When searching for a text string in a file, use recent search history. Press   ⌘   F   to open the search bar and then press   ⌥   ↓   to show the list of recent entries.

<img src="./readme.assets/image-20240703205046407.png" alt="image-20240703205046407" style="zoom:50%;" />



## View code reference information
You can use   F1   (View | Quick Documentation),   ⌘   P   (View | Parameter Info),   ⌘   B   (Navigate | Declaration), and similar shortcuts not only in the editor but also in the suggestions list while using code completion.

<img src="./readme.assets/image-20240703205132636.png" alt="image-20240703205132636" style="zoom:50%;" />



## Use multiple carets
In IntelliJ IDEA, you can use multiple carets. Press and hold   Shift   Alt   (on Windows and Linux) /   ⇧⌥   (on macOS) and then click at different positions to set additional carets in the editor.

You can then press   Shift   with the left or right arrow keys to select multiple text fragments.

Press   ⎋ Esc   to remove all the carets except for the recently added one.

<img src="./readme.assets/image-20240703205206436.png" alt="image-20240703205206436" style="zoom:50%;" />



## See available live templates
If you do not remember a live template abbreviation, press   ⌘   J   to see a list of suggestions for the current context. 

<img src="./readme.assets/image-20240703205244714.png" alt="image-20240703205244714" style="zoom:50%;" />



## Compare archives

To compare two   .jar  ,   .zip   or   .phar   archives or even files inside an archive, select them in the Project tool window and press   ⌘   D  .

The Compare Archives feature is integrated with the Java bytecode decompiler and allows you to see what exactly has changed between two different versions of a library.

<img src="./readme.assets/image-20240703205318726.png" alt="image-20240703205318726" style="zoom:50%;" />



## Join lines
To join two lines into one and remove unnecessary spaces, press   ⌃   ⇧   J  .

<img src="./readme.assets/image-20240703205342974.png" alt="image-20240703205342974" style="zoom:50%;" />



## Change signature
You can move method parameters in both declaration and invocation with   ⌥   ⇧   ⌘   ←   and   ⌥   ⇧   ⌘   →  . Moreover, you can propagate such move in a method declaration to the method invocation: press   ⌥   ↩ Return   after the move and choose Update usages to reflect signature change.

<img src="./readme.assets/image-20240703205500823.png" alt="image-20240703205500823" style="zoom:50%;" />



## Breakpoints menu
Right-click a breakpoint marker in the gutter to quickly enable/disable the breakpoint or adjust its properties.

<img src="./readme.assets/image-20240703205524571.png" alt="image-20240703205524571" style="zoom:50%;" />



## Edit regular expressions
You can edit a regular expression in your code using a dedicated editor.

Start typing a regular expression, press   ⌥   ↩ Return   and click Edit RegExp Fragment. The regular expression opens in a separate tab in the editor where you can type backslashes as is.

All changes are synchronized with the original regular expression, and escape characters are presented automatically.

<img src="./readme.assets/image-20240703205556988.png" alt="image-20240703205556988" style="zoom:50%;" />



## Verify regular expressions
To verify that your regular expression is correct, place the caret within the expression you want to check, press   ⌥   ↩ Return  , and select Check RegExp.

In the popup, type a sample string that should match your regular expression. The   icon shows that the match occurred.

<img src="./readme.assets/image-20240703205627019.png" alt="image-20240703205627019" style="zoom:50%;" />



## Scratch files 临时文件

Scratch files are temporary files that let you experiment and prototype in the editor, without creating any project files.
To create a scratch file, press   ⇧   ⌘   N  , and then select the language to use.

<img src="./readme.assets/image-20240703205746782.png" alt="image-20240703205746782" style="zoom:50%;" />



## The Move refactoring
When you invoke the Move refactoring   F6   on an inner class that is declared static, you are prompted to either make it a top-level class, or move it to another class.

<img src="./readme.assets/image-20240703205806271.png" alt="image-20240703205806271" style="zoom:50%;" />



## Refactor This
If you position the caret at a symbol and press   ⌃   T  , the list of refactorings that are applicable to the current context will open.

<img src="./readme.assets/image-20240703205829700.png" alt="image-20240703205829700" style="zoom:50%;" />



## Highlight statements that may throw exceptions
You can view all statements within the method where certain exceptions can be thrown. Place the caret at the   throws   statement and press   ⇧   ⌘   F7  . 

<img src="./readme.assets/image-20240703205938196.png" alt="image-20240703205938196" style="zoom:50%;" />



## Navigate to recent locations
Press   ⇧   ⌘   E   to get a list of recently viewed or changed code fragments.

<img src="./readme.assets/image-20240703210007766.png" alt="image-20240703210007766" style="zoom:50%;" />



## Close editor tabs

To close all editor tabs except the current one, keep   Alt   (on Windows and Linux) /   ⌥   (on macOS) pressed and click the cross icon for the current editor tab.

<img src="./readme.assets/image-20240703210033285.png" alt="image-20240703210033285" style="zoom:50%;" />



## Create a UML diagram
Press   ⌥   ⇧   ⌘   U   to open a UML class diagram in a new editor tab.

<img src="./readme.assets/image-20240703210121283.png" alt="image-20240703210121283" style="zoom:50%;" />



## Complete variable names
Code completion can suggest a name for a variable when you declare it. For example, start typing   private FileOutputStream  . The IDE will show you a list with suggestions. 

<img src="./readme.assets/image-20240703210148040.png" alt="image-20240703210148040" style="zoom:50%;" />



## Code completion 4

To quickly complete a method call of a static method located anywhere in your project, a library, or a JDK, enter a prefix and press   ⌃   ␣   twice. You can press   ⌥   ↩ Return   to import the selected method.

<img src="./readme.assets/image-20240703210240080.png" alt="image-20240703210240080" style="zoom:50%;" />



## Manage pull requests
Manage incoming GitHub pull requests directly from IntelliJ IDEA: from the main menu select Git | GitHub | View Pull Requests. IntelliJ IDEA lets you assign and merge pull requests, view the timeline and inline comments, submit comments and reviews, and accept changes without leaving the IDE.

<img src="./readme.assets/image-20240703210310118.png" alt="image-20240703210310118" style="zoom:50%;" />



## Delete a line

Press   ⌘   ⌫ Del   in the editor to delete the whole line at the caret.

<img src="./readme.assets/image-20240703210350304.png" alt="image-20240703210350304" style="zoom:50%;" />



## Navigate to a line
You can open a file in the editor at a particular line. Press   ⇧   ⌘   O   (Navigate | File), start typing the filename, and then type   :   followed by the line number.

<img src="./readme.assets/image-20240703210419757.png" alt="image-20240703210419757" style="zoom:50%;" />



## Create Ant property tags
You can start referring to an Ant property or target even if it's not defined yet. Press   ⌥   ↩ Return   and choose Create property from the list of intention actions to create the necessary tag without leaving your current editing location.

<img src="./readme.assets/image-20240703210454466.png" alt="image-20240703210454466" style="zoom:50%;" />



## Code completion 5

If you accept a completion suggestion by pressing the exclamation mark (!), this expression will be negated.

<img src="./readme.assets/image-20240703210546025.png" alt="image-20240703210546025" style="zoom:50%;" />



## Code Completion 6

Code Completion helps you quickly complete code statements. It automatically provides a list of suggestions available from the current caret position as you type:

<img src="./readme.assets/image-20240703210607152.png" alt="image-20240703210607152" style="zoom:50%;" />



## Analyze memory snapshots
The memory viewer in IntelliJ IDEA allows you to work with a detailed breakdown of HPROF snapshots. Memory snapshots are useful to locate code that uses a large amount of memory, and to search for memory leaks.
To analyze a snapshot, go to Run | Open Profiler Snapshot | Open and select a file with the   .hprof   extension.

<img src="./readme.assets/image-20240703210629466.png" alt="image-20240703210629466" style="zoom:50%;" />



## Sort completion suggestions
You can sort completion suggestions by relevance or alphabetically.
To sort alphabetically, select the Sort by Name option. To sort by relevance, clear the Sort by Name checkbox.

<img src="./readme.assets/image-20240703210646463.png" alt="image-20240703210646463" style="zoom:50%;" />



## Search for code inspections

To quickly find and run an inspection, press   ⌥   ⇧   ⌘   I   and start typing the name of the inspection or its group. Choose the inspection from the suggestion list and specify the scope. 

<img src="./readme.assets/image-20240703210718478.png" alt="image-20240703210718478" style="zoom:50%;" />



## Line separators
To check which line separators are used in the current file, look at the status bar:

<img src="./readme.assets/image-20240703210741053.png" alt="image-20240703210741053" style="zoom:50%;" />



## External documentation
To open your browser with the documentation page for the element at the caret, press   ⇧   F1   or select Tools | Web Browsers and Preview from the main menu.

Ensure that you set a default browser in the settings. To check the default browser, open settings by pressing   ⌘   ,   and navigate to   Tools | Web Browsers and Preview  .

<img src="./readme.assets/image-20240703210807612.png" alt="image-20240703210807612" style="zoom:50%;" />



## Code completion in the search bar
Press   ⌃   ␣   in the search bar when you search for text in the current file   ⌘   F  , so that you don't need to type the entire string.

<img src="./readme.assets/image-20240703210853893.png" alt="image-20240703210853893" style="zoom:50%;" />



## Create missing targets
When you are referring to a non-existing target tag in your Ant build file, IntelliJ IDEA automatically suggests that you create the corresponding tag. This context action will not even make you change your current editing location.

<img src="./readme.assets/image-20240703210927110.png" alt="image-20240703210927110" style="zoom:50%;" />



## Find and replace
Press   ⌘   F   to display the search bar. Press   ⌘   R   to add another field where you can type the replace string.

In the Find in Files dialog, you can switch to replace by pressing   ⇧   ⌘   R  . Similarly, press   ⇧   ⌘   F   to hide the Replace with field and switch to regular search.

<img src="./readme.assets/image-20240703210948245.png" alt="image-20240703210948245" style="zoom:50%;" />



## Search structurally
Select Edit | Find | Search Structurally to search for a code pattern or a grammatical construct.

<img src="./readme.assets/image-20240703211007680.png" alt="image-20240703211007680" style="zoom:50%;" />



## Change code selection
In the editor, press   ⌥   ↑  /  ⌥   ↓   to extend or shrink your current code selection.

<img src="./readme.assets/image-20240703211044486.png" alt="image-20240703211044486" style="zoom:50%;" />



## Jump between errors
Press   F2   or   ⇧   F2   to jump to the next or previous error respectively in the current file.

<img src="./readme.assets/image-20240703211101756.png" alt="image-20240703211101756" style="zoom:50%;" />



## Add copyright notices
In IntelliJ IDEA, you can configure different copyright notices for different sets of files. For convenience, you can use variables. For example, use   $today.year   to keep the year up to date.

 In the Settings/Preferences dialog (  ⌘   ,  ), select Editor | Copyright | Copyright Profiles, create a new profile, and add the text for your copyright notice using variables.

<img src="./readme.assets/image-20240703211130031.png" alt="image-20240703211130031" style="zoom:50%;" />



## Lens mode
To preview code without actually scrolling to it, hover your mouse pointer over a warning, error stripe, or just some section of source code on the scrollbar, and you will see a lens:

To disable the lens, right-click the error stripe in the scrollbar and clear the Show code lens on scrollbar hover checkbox.

<img src="./readme.assets/image-20240703211154573.png" alt="image-20240703211154573" style="zoom:50%;" />



## View files side by side
You can view multiple files side by side in the editor. Right-click the desired editor tab and select how you want to split the editor (Split Right or Split Down).

Alternatively, drag a tab to any area of the editor to activate split-screen mode.

<img src="./readme.assets/image-20240703211219655.png" alt="image-20240703211219655" style="zoom:50%;" />



## Choose shell for the terminal
Use your favorite shell from the built-in Terminal.

In the Settings/Preferences dialog   ⌘   ,  , go to Tools | Terminal and specify the path to your shell executable.

<img src="./readme.assets/image-20240703211239913.png" alt="image-20240703211239913" style="zoom:50%;" />



......

......

......






15. Navigate to implementation
To navigate to the implementations of an abstract method, position the caret at its usage or its name in the declaration and press T * B.

<img src="./readme.assets/image-20240702091303083.png" alt="image-20240702091303083" style="zoom:50%;" />

 











































































































