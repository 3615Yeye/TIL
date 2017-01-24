# Set up Typo3

Official documentation is there : https://docs.typo3.org/typo3cms/InstallationGuide/

# Creating the directory tree view

cd /path/to/your/fileadmin/

mkdir dev && cd dev
mkdir myProject && cd myProject

mkdir templates tsconfig typoscript

mkdir typoscript/{config,ext,mapping}
touch typoscript/constants.ts

mkdir templates/{static,v1}
mkdir templates/v1/{css,js,ext,img}

# Typo3 back-end

## Create the root page

In the 'Behavior' tab, select 'Use as a root page'.
In the 'Access' tab, unselect desactivate page.
In the 'Ressources' tab, add in the TSconfig pages :
    <INCLUDE_TYPOSCRIPT: source="DIR: fileadmin/dev/myProject/tsconfig/" extensions="ts">

### Add at least a domain name

Without the http or https protocol in front.

### Add a template

Add a template called 'Main template'.

In the constants field add :
    <INCLUDE_TYPOSCRIPT: source="FILE: fileadmin/dev/myProject/typoscript/constants.ts">

In the setup field add :
    <INCLUDE_TYPOSCRIPT: source="DIR: fileadmin/dev/myProject/typoscript/config/" extensions="ts">
    <INCLUDE_TYPOSCRIPT: source="DIR: fileadmin/dev/myProject/typoscript/mapping/" extensions="ts">
    <INCLUDE_TYPOSCRIPT: source="DIR: fileadmin/dev/myProject/typoscript/ext/" extensions="ts">

In the 'Options' tab, select erase constants & setup, select root level.

In the 'Inclusion' tab, select a templating tool like Content Elements (fluid_styled_content).

### Setting up the minimum typoscript & HTML

Add to the typoscript/constants.ts file :
    baseSite = fileadmin/dev/myProject
    baseTemplate = templates/v1

    myVar = myValue

Create and add to the typoscript/mapping/page.ts file :
    page = PAGE
    page.typeNum = 0 
    page {
        10 = FLUIDTEMPLATE
        10 {
            file = {$baseSite}/{$baseTemplate}/index.html
            variables {
                mainColumn = CONTENT
                mainColumn {
                    table = tt_content
                    select {
                        orderBy = sorting
                        where = colPos=0
                        languageField = sys_language_uid
                    }
                }
            }
            # Define variables from the constants file who should be passed to the template and accessible with {settings.myVar}
            settings {
                myVar = {$myVar}
            }
        }   
    }


Create and add to the templates/v1/index.html file :
<html>
    <body>
        <h1>{data.title}</h1>
        {main->f:format.raw()}
    </body>
</html>

Tadaa !
Typo3 is now generating HTML from the content of the pages defined in the backend.
