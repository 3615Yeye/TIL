It's possible to use Typo3 system categories with extensions records.

# Add a categorized flag in the extension records table
Connect to your database, identify the table used for your records and add a category column flag with the following SQL statement :
ALTER TABLE recordsTableName ADD categories int(11) NOT NULL DEFAULT 0;

# Declare you want to associate records with system categories
In ext_tables.php, add and adapt the following code :

\TYPO3\CMS\Core\Utility\ExtensionManagementUtility::makeCategorizable(
    'examples', // Point of this parameter ?
    'recordsTableName', // Name of the table storing the records to be categorized
    'categories', // Name of the created flag if system categories are used
    array(
        // Set a custom label
        'label' => 'LLL:EXT:examples/Resources/Private/Language/locallang.xlf:additional_categories',
        // This field should not be an exclude-field
        'exclude' => FALSE,
        // Override generic configuration, e.g. sort by title rather than by sorting
        'fieldConfiguration' => array(
            'foreign_table_where' => ' AND sys_category.sys_language_uid IN (-1, 0) ORDER BY sys_category.title ASC',
            ),  
        // string (keyword), see TCA reference for details
        'l10n_mode' => 'exclude',
        // list of keywords, see TCA reference for details
        'l10n_display' => 'hideDiff',
    )   
);

Uninstall/reinstall your extension, you can now enjoy system categorization ;)
