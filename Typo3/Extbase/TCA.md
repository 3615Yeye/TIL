# TCA

## Typo3 link wizard
To add in 'config' of the element : 
'wizards' => array(
    'link' => array(
        'type' => 'popup',
        'title' => "Utiliser l'assistant",
        'icon' => '../typo3/sysext/backend/Resources/Public/Images/FormFieldWizard/wizard_link.gif',
        'module' => array(
            'name' => 'wizard_element_browser',
            'urlParameters' => array(
                'mode' => 'wizard',
                'act' => 'page'
                ) ,
            ) ,
        'JSopenParams' => 'height=600,width=500,status=0,menubar=0,scrollbars=1'
        ) 
    ),
'softref' => 'typolink'

