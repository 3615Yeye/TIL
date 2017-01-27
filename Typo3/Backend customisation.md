# Override translation

TCEForm.tx_jsfaq_domain_model_expert.name.label.fr = Nom

Decomposition :
    - TCEForm
    - Tablename of the record (right click on the element, inspect and look at the data-table attribute)
    - Field name (right click on the element, inspect and look at the data-field attribute)
    - label
    - Language abbreviation

# Hide record field

TCEForm.tx_jsfaq_domain_model_answer.options.disabled = 1

Decomposition :
    - TCEForm
    - Tablename of the record (right click on the element, inspect and look at the data-table attribute)
    - Field name (right click on the element, inspect and look at the data-field attribute)

# Remove options of a field

Remove the ability to set a H1 title on the content records : 

TCEFORM.tt_content.header_layout.removeItems = 1

# Add options to a field

Add a new layout to the content records : 

TCEFORM.tt_content.layout.addItems.10 = My new layout

If there is an icon associated to the field
TCEFORM.tt_content.imageorient.addItems.10.icon = path/to/icon.gif

# Update TSconfig on page uid condition

Example of TSconfig to hide a certain field if the page uid match or hide another field if it doesn't match :

[page|uid = 405]
    TCEFORM.tx_sip_domain_model_sip.url.disabled = 1 
[ELSE]
    TCEFORM.tx_sip_domain_model_sip.telephone.disabled = 1 
[END]

