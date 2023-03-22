# The Jargon Editor 

---

Creating Domains using Jargon is pretty straight forward, but there are some things to look out for if you're not familiar with it.

## Overview of the Editor

The Jargon Editor has three areas of focus:

![Showing the layout of the Jargon editor](../static/media/editor_layout.png)

1. Editor - where you create and edit the structure of your Domain
2. Sidebar - where you update specific details of the Domain, like Definitions, Code Tables, Business Rules and Filters
3. Toolbar - where you interact with the Domain, by saving, importing, changing the view, etc:

## The Editor

### Editing the Domain

You will spend most of your time in the Editor area, where you type and layout your Domains.

As you type the [Jargon Language](/pages/language) on the left, the diagram will update on the right. Following the auto classification of Domain Driven Design Class types, the colours here will update in real-time as you type.

Once you have a few Classes, spend a little time dragging them around to help make your Domain clearer to understand. Jargon will atttempt to route the connection lines intelligently, but it's not perfect so you might have to try a few different layouts before you find something you like.

### Some notes on a text-first approach

Because Jargon Domains are described with text, there are a few compromises that have been made to the editing experience.

1. Renaming things - If you change the name of something in the text editor, Jargon will attempt to detect and apply that name change everywhere throughout the Editor, but sometimes things get missed.
2. Cutting and Pasting - If ever you remove a chunk of the text, Jargon will try to remember all the other details about the Classes and Properties you removed, like definitions and layouts. Whenever Jargon will remembe and save the details of things you've removed. These remembered things can be viewed using the [Lost & Found](pages/the_jargon_editor?id=lost-amp-found-definitions) button.



## Toolbar Buttons

The Editor's Toolbar Buttons are separated into two groups. The left set operate on the entire Domain, the right control the Sidebar.


### Left side buttons
![Left side buttons](../static/media/toolbar_buttons_left.png ' :size=400')

### Save

Saves the Domain. You can also choose to create a Snapshot of the Domain, allowing people to see the changes you've made. Snapshots need a description of the work you've done, which is handy when it is time to create a Release.

### Imports

Shows the Domains you are currently importing, and allows you to Import more. The button will show a notification badge with the number of Imports.

### Upload

Upload a file from your computer into this Domain. Jargon can read OpenAPI specifications, XSD and JSON-LD files.

### Import / Export Classes, Properties and Codes

Jargon can Export parts of one Domain so that you can move them to another Domain.

To Export:

- Click the Import/Export button in the Domain you want to export from
- Type the names of the Classes you want to Export, separated by a space
- As you type, the lower half of the screen updates with a textual representation of the Classes you listed, including all their Properties, Codes and related definitions
- Copy this text into your clipboard

To Import:

- Click the Import/Export button in the Domain you want to import into
- Paste a copied import representation into the lower half of the screen
- Clicking the 'Import' button will create the Classes, Properties and Codes that you exported

### Lost & Found Definitions

This button will show you all the Classes and Properties in your Domain that don't have definitions.
You will also see a list of definitions that you have previously entered into your Domaim but aren't being used at the moment.
Using the buttons on this screen you will be able to assign unused defintions to Classes or Properties that don't currently have defintions.
The Lost & Found button will show a notifiction badge with the number of missing definitions

### Errors, Warnings & Information

Jargon will scan you Domain for errors and report them here. The button will show a notification badge indicating the number of errors or warnings in your Domain.


### Right side buttons
![Right side buttons](../static/media/toolbar_buttons_right.png ' :size=400')

### Reports and Analytics

Changes the Sidebar to display the reports that Jargon can run on this Domain

### Tree of Imports

Changes the Sidebar to display all the Imports and Imported Classes this Domain uses.

### Code Tables

Changes the Sidebar to display the current [Code Tables](/pages/code_tables) 

### Definitions editor

Changes the Sidebar to display the [Defintions Editor](pages/data_definitions). It shows the definition of the item on the current row in the model text editor.
You can scroll to the previous and next definition using the left and right buttons in the Sidebar.

### API Paths

Changes the Sidebar to display the current [API Paths](pages/api_paths) for this Domain.

### Zoom Controls

Zoom in and out. Reposition the diagram if you get lost.


