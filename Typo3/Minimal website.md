# Steps for a minimal Typo3 website

## Ceate the root page
Add a new page.
In "Behavior" tab, check "Use as Root Page".

## Add domain name to the root page

## Create the main template
In "Options" tab, check "Constants", "Setup" and "Rootlevel".
In "Includes" tab, add "Content Elements (fluid_styled_content)" in the "Include static (from extensions)" section.

In "General" tab, add the following in the setup :
    page = PAGE
    page.typeNum = 0 
    page.10 = TEXT
    page.10.value = HELLO WORLD!
