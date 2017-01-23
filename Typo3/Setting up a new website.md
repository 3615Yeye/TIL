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

# To be continued to a basic Hello world from a content in the backend
