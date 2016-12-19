Copy the orginal template file located in the Typo3 sources somewhere in the templating directory of your website.
The original file is stored here : typo3/sysext/fluid/Resources/Private/Templates/ViewHelpers/Widget/Paginate/Index.html

Adapt and add the following the typoscript of your website : 
- Extbase wide : config.tx_extbase.view.widget.TYPO3\CMS\Fluid\ViewHelpers\Widget\PaginateViewHelper.templateRootPath = {$baseSite}/{$baseTemplate}/ext/fluid/Templates/
- Single extension wide : plugin.tx_extension.view.widget.TYPO3\CMS\Fluid\ViewHelpers\Widget\PaginateViewHelper.templateRootPath = EXT:path/to/Templates/
