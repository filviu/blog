---
title: vi usage reference
author: silviu
type: post
date: 2011-06-16T11:35:00+00:00
url: /2011/06/16/vi-usage-reference/
categories:
  - old
tags:
  - console
  - solaris
  - sun
  - temp_on
  - vi

---
Recently I had to do some work on a Solaris Server. This meant two things: finding a new appreciation for the user friendliness of the linux console and second it meant that I had to use the barebones vi. You know, the one where the arrows and backspace won't work. Smart. So here's a little list compiled with the more important functions

First I had to

```bash
export TERM=xterm
```

before vi worked correctly.

**Create new file or Open existing file in vi**
vi without any file name will open a new file where you can enter and edit text and when coming out you will be asked to enter a file name where to save the text. vi with a file name as argument will open that file for editing if the file already exists it opens it otherwise it creates a new one.

**Modes
**
vi operates in following two modes :
- **Command Mode** : After a file is opened it is opened in command mode ,that is , input from the keyboard will be treated as vi commands

**- Insert Mode**: To enter the text you have to put vi in insert by pressing ‘i’ or ‘a’ after which you can write the text and you will see it on the screen. To switch between these modes press Esc

**Saving & Exiting vi editor**
You can exit vi in different ways :

  * _Quit without saving_ : If you don’t want to save the work :q will take you out without saving your editing in vi.
  * _Write & quit_ : . Simple :w saves the current file but don’t exit. For save and quit :wq is used in vi.
  * _Forced Quite_ : An ! after exit commands ( :q! , :wq! ) forces quit from vi after ignoring editing (for :q!) or writing (for :wq!) all the change


| (vi) Command                                            |                |
|---------------------------------------------------------|----------------|
| Moving Cursor in File                                   |                |
| Left                                                    | h              |
| Right                                                   | l              |
| Up                                                      | k              |
| Down                                                    | j              |
| Line                                                    |                |
| First                                                   | ^ or B         |
| Last                                                    | $              |
| Sentence                                                |                |
| Next sentence                                           | )              |
| Previous sentence                                       | (              |
| Paragraph                                               |                |
| Next                                                    | }              |
| Previous                                                | {              |
| file                                                    |                |
| Go to end of file                                       | :$             |
| on character forward                                    | :w             |
| One word forward                                        | :W             |
| go to a line number                                     | :line_number   |
| display file info                                       | ^g             |
| Inserting and appending text                            |                |
| inserts text to the left of cursor                      | i              |
| inserts in the beginning of line                        | I              |
| appends text to right of cursor                         | a              |
| appends to the end of line                              | A              |
| Adding new line                                         |                |
| add a new line below the current line                   | o              |
| adds a new line above the current line.                 | O              |
| Deleting the text :                                     |                |
| deletes text above the text                             | x              |
| deletes text character on right of cursor               | X              |
| deletes line 25                                         | 25d            |
| deletes current line                                    | dd             |
| delete till end of current line                         | D              |
| Replacing a character & word                            |                |
| replace the character above the cursor                  | r              |
| replaces characters until Esc is pressed                | R              |
| replaces the word from cursor to the end indicated by $ | cw             |
| replaces till end of line                               | C              |
| Substitute                                              |                |
| substitutes current character                           | s              |
| substitutes entire line                                 | S              |
| Undo last changes                                       |                |
| undo last change                                        | u              |
| undo changes to the current line                        | U              |
| Copy and pasting lines                                  |                |
| copies the current line into buffer                     | yy             |
| copies 5 lines from the current line                    | 5yy            |
| pastes the current buffer                               | p              |
| Searching                                               |                |
| Searches for name in the file                           | :/name         |
| n continues search forward.                             | n              |
| N searches backwards                                    | N              |
| Saving                                                  |                |
| saves the text but does not quit                        | :w             |
| saves & quit                                            | :wq!           |
| save                                                    | ZZ             |
| Quit without saving                                     | q!             |
|                                                         |                |
| Search & Replace                                        | s///g .        |
| Repeat last command                                     | .              |
| Recovering an unsaved file                              | vi -r filename |

I created this page using vi's man page and various pages found on the web.
