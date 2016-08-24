# List of method used in pibase and their replacement in extbase
t3lib_extMgm => \TYPO3\CMS\Core\Utility\ExtensionManagementUtility
t3lib_div::loadTCA Can be removed, TCA are auto loaded since Typo3 6.2
t3lib_div => \TYPO3\CMS\Core\Utility\GeneralUtility

class x extends tslib_pibase => class x extends \TYPO3\CMS\Frontend\Plugin\AbstractPlugin
