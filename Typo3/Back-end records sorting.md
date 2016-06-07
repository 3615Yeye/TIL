# SQL
It's maybe better to create the sorting field for each records type concerned with the Extension Builder, but I did after the creation of the extension directly in the database.

For each table of records like [extensionName]_domain_model_[recordsName]  
add :
ALTER TABLE [extensionName]_domain_model_[recordsName] 
ADD sorting int(11) unsigned NOT NULL DEFAULT '0'
;

# TCA
For each records type like : Configuration/TCA/[extensionName]_domain_model_[recordsName].php
add : 
$pagesTca = array(
    'ctrl' => array(
        'sortby' => 'sorting',
        'default_sortby' => 'ORDER BY sorting',
    )
)

# Repository
For each records type like : Classes/Domain/Repository/[recordsName]Repository.php 
add :
protected $defaultOrderings = array(
    'sorting' => \TYPO3\CMS\Extbase\Persistence\QueryInterface::ORDER_ASCENDING,
);
