# How to add a task in the scheduler with an extension

## Minimum task

In an extension create the directory Classes/Scheduler.

In this directory create a file MyTask.php with :
<?php
namespace Vendor\ExtensionName\Scheduler;

class MyTask extends \TYPO3\CMS\Scheduler\Task\AbstractTask {
    public function execute() {
        // Your code

        // Don't forget to return a boolean to let know the scheduler if the task have failed or successed
    }   
}
?>

More developer info about scheduler here : https://docs.typo3.org/typo3cms/extensions/scheduler/DevelopersGuide/CreatingTasks/Index.html

## Declare the task in the ext_localconf.php

$GLOBALS['TYPO3_CONF_VARS']['SC_OPTIONS']['scheduler']['tasks']['Vendor\\ExtensionName\\Scheduler\\MyTask'] = array(
    'extension' => $_EXTKEY,
    'title' => 'Your title or path to localisation file',
    'description' => 'Your title or path to localisation file',
);

## Calling a controller function from your task
Put the following code in your task to call a controller function from your task. 
Using the object manager to get the controller will inject the dependencies (like repositories), while using directly makeInstance from your task won't.

$objectManager = \TYPO3\CMS\Core\Utility\GeneralUtility::makeInstance('TYPO3\CMS\Extbase\Object\ObjectManager');
$exampleController = $objectManager->get('Vendor\ExtensionName\Controller\ExampleController');
