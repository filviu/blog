---
title: vi usage reference
author: silviu
type: post
date: 2011-06-16T11:35:00+00:00
url: /2011/06/16/vi-usage-reference/
dsq_thread_id:
  - 333818529
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


<table id="AutoNumber2" border="1" cellspacing="0" cellpadding="3" width="392">
  <tr>
    <td>
      <strong>(vi) Command</strong>
    </td>
  
    <td>
      <strong> </td> </tr> 
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#cecece">
          <strong> Moving Cursor in File</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Left
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          h
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Right
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          l
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Up
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          k
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Down
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          j
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="13" align="left" bgcolor="#ffffff">
          <strong>Line</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          First
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          ^ or B
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Last
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          $
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Sentence</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Next sentence
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          )
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" valign="top" bgcolor="#EEEEEE">
          Previous sentence
        </td>
      
        <td width="297" height="23" align="left" valign="top" bgcolor="#EEEEEE">
          (
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="21" align="left" bgcolor="#ffffff">
          <strong>Paragraph</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Next
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          }
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Previous
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          {
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>file</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Go to end of file
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          :$
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          on character forward
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          :w
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          One word forward
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          :W
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          go to a line number
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          :line_number
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          display file info
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          ^g
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Inserting and appending text </strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          inserts text to the left of cursor
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          i
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          inserts in the beginning of line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          I
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          appends text to right of cursor
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          a
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          appends to the end of line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          A
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Adding new line</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          add a new line below the current line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          o
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          adds a new line above the current line.
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          O
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Deleting the text :</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          deletes text above the text
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          x
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          deletes text character on right of cursor
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          X
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          deletes line 25
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          25d
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          deletes current line
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          dd
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          delete till end of current line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          D
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Replacing a character & word</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          replace the character above the cursor
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          r
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          replaces characters until Esc is pressed
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          R
        </td>
      </tr>
    
      <tr>
        <td width="231" height="57" align="left" bgcolor="#EEEEEE">
          replaces the word from cursor to the end indicated by $
        </td>
      
        <td width="297" height="57" align="left" bgcolor="#EEEEEE">
          cw
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          replaces till end of line
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          C
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Substitute</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          substitutes current character
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          s
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          substitutes entire line
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          S
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="16" align="left" bgcolor="#ffffff">
          <strong>Undo last changes</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          undo last change
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          u
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          undo changes to the current line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          U
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Copy and pasting lines</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          copies the current line into buffer
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          yy
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          copies 5 lines from the current line
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          5yy
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          pastes the current buffer
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          p
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Searching</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          Searches for name in the file
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          :/name
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          n continues search forward.
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          n
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          N searches backwards
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          N
        </td>
      </tr>
    
      <tr>
        <td colspan="2" width="528" height="19" align="left" bgcolor="#ffffff">
          <strong>Saving</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          saves the text but does not quit
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          :w
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          saves & quit
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          :wq!
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          save
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          ZZ
        </td>
      </tr>
    
      <tr>
        <td width="231" height="23" align="left" bgcolor="#EEEEEE">
          Quit without saving
        </td>
      
        <td width="297" height="23" align="left" bgcolor="#EEEEEE">
          q!
        </td>
      </tr>
    
      <tr>
        <td width="231" height="19" align="left" bgcolor="#EEEEEE">
        </td>
      
        <td width="297" height="19" align="left" bgcolor="#EEEEEE">
        </td>
      </tr>
    
      <tr>
        <td width="231" height="19" align="left" bgcolor="#EEEEEE">
          Search & Replace
        </td>
      
        <td width="297" height="19" align="left" bgcolor="#EEEEEE">
          <strong> s/<search>/<replace>/g .</strong>
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          Repeat last command
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          .
        </td>
      </tr>
    
      <tr>
        <td width="231" height="38" align="left" bgcolor="#EEEEEE">
          Recovering an unsaved file
        </td>
      
        <td width="297" height="38" align="left" bgcolor="#EEEEEE">
          <dl>
            <dt>
              <strong>vi -r filename</strong>
            </dt>
          </dl>
        </td>
      </tr></tbody> </table> 
    
      <p>
        I created this page using vi's man page and various pages found on the web.
      </p>