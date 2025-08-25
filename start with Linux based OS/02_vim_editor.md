## Terminal Based Editor
### vim or NeoVim
  + There are many more editor but we will go with vim only.
  + To open any file in in vim, open terminal and write command `vi filename` eg. `vi Hello.java`.
  + By default files open in normal mode.
  + we have three mode in vim
      + Normal mode
        + press `esc` to return normal mode from any other mode.
      + Visual mode
      + Insert mode
1. Normal mode
+ h → left, l → right , j → down, k → up,
0, $
e, b
gg, G
p ⇒ paste
2. Visual mode
h → left, l → right , j → down, k → up
0, $
e, b
gg, G
y ⇒ copy
d ⇒ cut
3. Insert mode
Type away!
Extra commands
Exiting out of vi
:q
:q!
:wq!
Undo redo
u - undo
ctrl + r - redo
Search
/ + what_to_search
:line_number - go to line
Logo
+ Vim is a powerful, modal text editor available in Ubuntu. The key to using Vim is understanding its modes.
+ To edit, save, and exit a file, you'll mainly use three core commands and two modes: Normal Mode and 1. Insert Mode.
+ Here are the basics you need to start editing:
  1. Opening and Closing Vim
  Action	Command/Key	Mode	Notes
  Open a file	vim filename.txt	Terminal	If the file doesn't exist, Vim creates a new one.
  Save and Quit	:wq (followed by Enter)	Normal Mode	Write (save) and Quit.
  Save only	:w (followed by Enter)	Normal Mode	Write (save).
  Quit without saving	:q! (followed by Enter)	Normal Mode	Quit, ignoring (!) changes. Use this if you make a mistake.

2. The Two Core Modes
A. Normal Mode
This is the default mode when you open Vim. You cannot type text in this mode. It's used for navigation, deletion, copying, pasting, and issuing commands.

Action	Key	Notes
Move Cursor	h (left), j (down), k (up), l (right)	The "Vim arrows".
Enter Insert Mode	i	insert text at the current cursor position.
Enter Command Mode	:	Use this to save, quit, or run complex commands.

Export to Sheets
B. Insert Mode
This mode is used only for typing (inserting) text, like a standard editor.

Action	Key	Notes
Exit Insert Mode	Esc (Escape key)	Always press Esc to return to Normal Mode to save, quit, or navigate.

Export to Sheets
3. Basic Editing Commands (In Normal Mode)
Once you're back in Normal Mode (by pressing Esc), you can use these shortcuts:

Action	Command	Notes
Delete Character	x	Deletes the character under the cursor.
Delete Line	dd	Deletes the entire current line.
Paste	p	Pastes the last deleted or copied content.
Undo	u	Undoes the last change.

Export to Sheets
In summary, the workflow is:

Open file: vim filename.txt (Starts in Normal Mode)

Type text: Press i (Switches to Insert Mode), then type.

Finish typing: Press Esc (Returns to Normal Mode).

Save and exit: Type :wq then press Enter.
