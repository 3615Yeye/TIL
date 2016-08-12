# Define the flexform to use for the plugin
Open ext_tables.php at the root path of the extension, add and adapt the following :

// FlexForm configuration
$pluginName = 'PluginName';
$pluginSignature = preg_replace('/[^a-z0-9]/', '', strtolower($_EXTKEY)) . '_' . strtolower($pluginName);

$TCA['tt_content']['types']['list']['subtypes_addlist'][$pluginSignature] = 'pi_flexform';
\TYPO3\CMS\Core\Utility\ExtensionManagementUtility::addPiFlexFormValue(
    $pluginSignature,
    'FILE:EXT:' . $_EXTKEY . '/Configuration/FlexForms/FlexformName.xml'
);

# Define the flexform
<T3DataStructure>
	<meta>
		<langDisable>1</langDisable>
	</meta>
	<sheets>
		<sDEF>
			<ROOT>
				<TCEforms>
					<sheetTitle>Flexform Demo</sheetTitle>
				</TCEforms>
				<type>array</type>
                <el>
                    <settings.exampleText>
                        <TCEforms>
                            <exclude>1</exclude>
                            <label> Example text : </label>
                            <config>
                                <type>input</type>
                                <size>60</size>
                            </config>
                        </TCEforms>
                    </settings.exampleText>
				</el>
			</ROOT>
		</sDEF>
	</sheets>
</T3DataStructure>

# Use the data in the controller with the variable : $this->settings

# Types of elements
Each elements are to be put inside the <el></el> of the flexform.

## Text
<settings.exampleText>
    <TCEforms>
        <exclude>1</exclude>
        <label> Example text : </label>
        <config>
            <type>input</type>
            <size>60</size>
        </config>
    </TCEforms>
</settings.exampleText>

## Integer
<settings.exampleInt>
    <TCEforms>
        <exclude>1</exclude>
        <label> Example int : </label>
        <config>
            <type>input</type>
            <size>2</size>
            <eval>int</eval>
            <default>5</default>
        </config>
    </TCEforms>
</settings.exampleInt>

## Select element from database
<settings.exampleSys_pageSelect>
    <TCEforms>
        <exclude>1</exclude>
        <label> Select a sys_page (works for sys_category as well and any other databse table) : </label>
        <config>
            <type>select</type>
            <autoSizeMax>50</autoSizeMax>
            <foreign_table>pages</foreign_table>
            <foreign_table_where> ORDER BY pages.sorting ASC</foreign_table_where>
            <maxitems>1</maxitems>
            <renderMode>tree</renderMode>
            <size>10</size>
            <treeConfig>
                <appearance>
                    <expandAll>0</expandAll>
                    <showHeader>0</showHeader>
                </appearance>
                <parentField>pid</parentField>
            </treeConfig>
        </config>
    </TCEforms>
</settings.exampleSys_pageSelect>

## Select displayed controller
<switchableControllerActions>
    <TCEforms>
        <label>Controlleur</label>
        <config>
            <type>select</type>
            <items type="array">
                <numIndex index="0" type="array">
                    <numIndex index="0">List</numIndex>
                    <numIndex index="1">Fichier->list</numIndex>
                </numIndex>
                <numIndex index="1" type="array">
                    <numIndex index="0">Résults</numIndex>
                    <numIndex index="1">Fichier->result</numIndex>
                </numIndex>
            </items>
            <maxitems>1</maxitems>
            <size>1</size>
        </config>
    </TCEforms>
</switchableControllerActions>
