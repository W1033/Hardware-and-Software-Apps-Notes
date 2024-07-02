# Tip of the day

1. Type-Matching code completion 类型匹配代码完成（/补全）

Use the Type-Matching completion ^ . after the new keyword to instantiate an object of the expected type.

<img src="./readme.assets/image-20240702090833626.png" alt="image-20240702090833626" style="zoom:50%;" />


2. Show usages 

You can view the list of all usages of a class, method or variable across the whole project, and quickly navigate to the selected item. Place the caret at a symbol and press T (Edit | Find Usages | Show Usages). To jump to a usage, select it from the list and press ~ Return.

<img src="./readme.assets/image-20240702090935446.png" alt="image-20240702090935446" style="zoom:50%;" />


3. The Rename refactoring 

You can easily rename your classes, methods, and variables with automatic correction of all places where they are used. Position the caret at the symbol you want to rename, and press * F6 (Refactor | Rename). Type the new name and press • Return .

<img src="./readme.assets/image-20240702090957097.png" alt="image-20240702090957097" style="zoom:50%;" />


4. Improve code with context actions 

Press T Return in the editor to fix a highlighted error or warning, improve, or optimize a code construct. For some intention actions, you can open a preview or an action description by pressing F1 (View | Quick Documentation).

<img src="./readme.assets/image-20240702091017547.png" alt="image-20240702091017547" style="zoom:50%;" />


5. Preview search results 

You can use the Preview area of the Find in Files dialog ( 4 * F) for quicker search without leaving the dialog. The Preview dialog displays the first 100 results.note

<img src="./readme.assets/image-20240702091037655.png" alt="image-20240702091037655" style="zoom:50%;" />


6. Speed search in tree views

 Speed search is available in all tree views, for example, in the Project tool window. Start typing, and you'll quickly locate the necessary item.CF3C5FAC-BF66-4AB9-B8CE-E2EE36A7452A)

<img src="./readme.assets/image-20240702091048845.png" alt="image-20240702091048845" style="zoom:50%;" />


7. Comment and uncomment code

 Use shortcuts to comment and uncomment lines and blocks of code: 88 1 : for single line comments (// ...) T 8 / : for block comments ( /*...*/)

<img src="./readme.assets/image-20240702091104414.png" alt="image-20240702091104414" style="zoom:50%;" />


8. Expand code selection

Press T to expand code selection. Each time you press 1P, the selection expands to other areas of code. For example, the selection expands from a method name to the expression calling this method, then to the whole statement, then to the containing block, and so on.

<img src="./readme.assets/image-20240702091116786.png" alt="image-20240702091116786" style="zoom:50%;" />


9. Show file structure

 You can quickly navigate within the current file with 2 F12 (Navigate | File Structure). File structure shows the list of members of the current class. To navigate to an element, select it and press Return or &+. To easily locate an item in the list, start typing its name.

<img src="./readme.assets/image-20240702091136915.png" alt="image-20240702091136915" style="zoom:50%;" />


10. Select In

 To quickly select the currently edited element (a class, file, method, or field) in another view, press T F1 or call Navigate | Select In.

<img src="./readme.assets/image-20240702091148373.png" alt="image-20240702091148373" style="zoom:50%;" />


11. Postfix code completion

Postfix code completion is applied from right to left to avoid backward caret jumps when coding. Type a dot after the code fragment that you want to change and select the desired option. To see the suggestion list with postfix templates, you can also press

<img src="./readme.assets/image-20240702091214918.png" alt="image-20240702091214918" style="zoom:50%;" />


12. View Git blame annotations

 Git annotations show detailed information on the origin of each code line (rightclick the gutter and select Annotate with Git Blame). Right-click an annotation and choose Show Diff to review the differences between the current and the previous version of the file.

<img src="./readme.assets/image-20240702091225395.png" alt="image-20240702091225395" style="zoom:50%;" />


13. Reformat code

To reformat code according to the current code style settings, select Code | Reformat Code from the main menu or press T 8L.

<img src="./readme.assets/image-20240702091236729.png" alt="image-20240702091236729" style="zoom:50%;" />

 

14. Create code constructs with completion You can create code constructs using statement completion. Start typing a method declaration, a method call or a statement such as if, do while, try -catch, or return. Press * 2 • Return to complete the statement into a syntactically correct construct.

<img src="./readme.assets/image-20240702091249922.png" alt="image-20240702091249922" style="zoom:50%;" />

 

15. Navigate to implementation To navigate to the implementations of an abstract method, position the caret at its usage or its name in the declaration and press T * B.

<img src="./readme.assets/image-20240702091303083.png" alt="image-20240702091303083" style="zoom:50%;" />


16. Camel case in code completion You can narrow down a list of code completion suggestions by using camel case prefixes.

<img src="./readme.assets/image-20240702091312954.png" alt="image-20240702091312954" style="zoom:50%;" />

 

17. Override methods You can easily override methods of the base class by pressing ^ 0 (Code | Override Methods). To implement methods of the interfaces (or of the abstract base class) that the current class implements, press ^ | (Code | Implement Methods).

<img src="./readme.assets/image-20240702091402386.png" alt="image-20240702091402386" style="zoom:50%;" />


18. Quick code documentation To quickly see the documentation for a class or method at the caret, press F1 (View | Quick Documentation).

<img src="./readme.assets/image-20240702091412932.png" alt="image-20240702091412932" style="zoom:50%;" />


19. View recent files Press 2 E (View | Recent Files) to view the list of recently opened files.

<img src="./readme.assets/image-20240702091429296.png" alt="image-20240702091429296" style="zoom:50%;" />


20. Evaluate expression You can execute expressions or reassign values for variables while your script is stopped by a breakpoint. The Evaluate Expression functionality helps you to obtain additional details about the program state or test various scenarios at • If the expression is present in the code, hold Alt (on Windows and Linux) or T (on macOS) and click it. If you want to evaluate a specific code fragment, select it before clicking. • To evaluate an arbitrary expression, select Run | Debugging Actions | Evaluate Expression. A separate dialog opens that supports various constructs including loops, assignments, lambdas, and so on.D1A7B76A-E155-4E5C-BB36-9ECD64DCCBB9)

<img src="./readme.assets/image-20240702091454797.png" alt="image-20240702091454797" style="zoom:50%;" />


21. Debugger If you want to log program state during debugging, use non-suspending breakpoints. Select the expression that you want to log, hold Shift, and click the gutter at the line where the expression should be logged. In the example,sent. size() will be logged upon reaching line 24.

<img src="./readme.assets/image-20240702091504720.png" alt="image-20240702091504720" style="zoom:50%;" />


22. Change focus in tool windows O Esc in any tool window moves the focus to the editor. • O Esc moves the focus to the editor and hides the current or the last active tool window. F12 moves the focus from the editor to the last focused tool window.

<img src="./readme.assets/image-20240702091514145.png" alt="image-20240702091514145" style="zoom:50%;" />


23. Local History Local History lets you track all changes to files, classes, methods, or any code fragments and roll back to any stable point if necessary. To view local history, from the main menu, select File | Current File | Show History.

<img src="./readme.assets/image-20240702091523838.png" alt="image-20240702091523838" style="zoom:50%;" />


24. Extract Variable refactoring The Extract Variable refactoring wraps a selected expression into a variable. It adds a new variable declaration and uses the expression as an initializer. Select an expression and press T% V (Refactor | Extract/Introduce | Variable).

<img src="./readme.assets/image-20240702091533284.png" alt="image-20240702091533284" style="zoom:50%;" />


25. Find usages Press T F7 to quickly locate all occurrences of code referencing the symbol at the caret, no matter if the symbol is a part of a class, method, field, parameter, or another statement.

<img src="./readme.assets/image-20240702091543257.png" alt="image-20240702091543257" style="zoom:50%;" />


26. Access VCS-related options Press ^ V to access all VCS-related commands available in the current context.

<img src="./readme.assets/image-20240702091559168.png" alt="image-20240702091559168" style="zoom:50%;" />































































































































