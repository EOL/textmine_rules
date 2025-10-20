====================================================================================================================================================================
- terms_implying_missing_filter.txt
https://github.com/eliagbayani/EOL-connector-data-files/raw/master/Pensoft_Annotator/terms_implying_missing_filter.txt
came from DATA-1713 (AntWeb task).
https://eol-jira.bibalex.org/browse/DATA-1713?focusedCommentId=65443&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-65443
Eli will add it to the list of generally excluded URIs.
LATER ON, THIS LIST WAS DISCARDED, AND WAS DISTRIBUTED ELSEWHERE - TO THOSE REMAINING .txt FILES BELOW.
====================================================================================================================================================================
- life_history.tsv
https://github.com/eliagbayani/EOL-connector-data-files/raw/master/Pensoft_Annotator/life_history.tsv
came from DATA-1893: new patterns for all textmined resources: life history ontology
Eli: this can be a placeholder for all strings that will be assigned its own measurementType and/or measurementValue
====================================================================================================================================================================
- terms_to_remove.txt
https://github.com/eliagbayani/EOL-connector-data-files/raw/master/Pensoft_Annotator/terms_to_remove.txt
came from DATA-1870 (also AntWeb task but to be used for all resources)
https://eol-jira.bibalex.org/browse/DATA-1870?focusedCommentId=65451&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-65451
Eli added it to the list of generally excluded URIs in [Pensoft2EOLAPI.php]
====================================================================================================================================================================
- geo_synonyms.txt
https://github.com/eliagbayani/EOL-connector-data-files/raw/master/Pensoft_Annotator/geo_synonyms.txt
came from: https://eol-jira.bibalex.org/browse/DATA-1870?focusedCommentId=65780&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-65780
Another set of URIs to be removed
====================================================================================================================================================================
- 2024_2remove.tsv
All these were now added to: terms_to_remove.txt
====================================================================================================================================================================
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

====================================================================================================================================================================
As of 14-Oct-2025
public function initialize_remaps_deletions_adjustments()
    self::init_DATA_1841_terms_remapped();  //generates $this->remapped_terms               -> used in apply_adjustments()
    self::initialize_mRemark_assignments(); //generates $this->mRemarks                     -> used in apply_adjustments()
    self::initialize_delete_mRemarks();     //generates $this->delete_MoF_with_these_labels -> used in apply_adjustments()
    self::initialize_delete_uris();         //generates $this->delete_MoF_with_these_uris   -> used in apply_adjustments()

    remapped_terms: 260
    mRemarks: 119
    delete_MoF_with_these_labels: 66
    delete_MoF_with_these_uris: 539

    $this->initialize_new_patterns();         //generates $this->new_patterns   -> from Functions_Pensoft.php --- DATA-1893
    new_patterns: 19

    $this->allowed_terms_URIs = self::get_allowed_value_type_URIs_from_EOL_terms_file(); //print_r($this->allowed_terms_URIs); -> from Functions_Pensoft.php
    allowed_terms_URIs from EOL terms file: [10577]

-----------sent to github ticket: https://github.com/EOL/ContentImport/issues/36
@KatjaSchulz @jhammock 
Below are the general steps how we generate our textmined resources.

After the Pensoft annotator generates its output we apply several filters/adjustments:

1st step: We apply a re-mapping of the URIs. We replace some URIs with preferred URIs.
This is the [remap file](https://github.com/EOL/textmine_rules/blob/main/Terms_remapped/DATA_1841_terms_remapped.tsv)

2nd step: We have a list of specific strings with pre-assigned URIs. We apply them.
This is the [file](https://raw.githubusercontent.com/EOL/textmine_rules/main/mRemarks_assignments.tsv).

3rd step: If label is any of these, then exclude that measurement
These are the files: [first](https://raw.githubusercontent.com/EOL/textmine_rules/main/del_MoF_with_these_labels.tsv) [second](https://raw.githubusercontent.com/EOL/textmine_rules/main/blacklist_labels.txt)

4th step: We exclude measurements with specific URIs
These are the files: [first](https://raw.githubusercontent.com/EOL/textmine_rules/main/terms_to_remove.txt) [second](https://raw.githubusercontent.com/EOL/textmine_rules/main/geo_synonyms.txt)

This [file](https://raw.githubusercontent.com/EOL/textmine_rules/main/WoRMS_only_delete_URIs.tsv) is for WoRMS resource only.

5th step: We also exclude terms that are descendants of ENVO_00000002, inclusive. 
A geographic feature resulting from the influence of human beings on nature.
This file is generated on-demand: [API call](https://editors.eol.org/eol_php_code/update_resources/connectors/get_descendants_of_term.php?term=http://purl.obolibrary.org/obo/ENVO_00000002)

6th step: For Wikipedia and TreatmentBank only.
Specific labels (related to soil composition) will be assigned to measurementType = http://purl.obolibrary.org/obo/ENVO_09200008
This is the [file](https://raw.githubusercontent.com/EOL/textmine_rules/main/soil_composition.tsv).

7th step: Patterns for all textmined resources: for life history ontology. 
Specific labels have predefined measurementValue and measurementType.
This is the [file](https://raw.githubusercontent.com/EOL/textmine_rules/main/life_history.tsv)

8th step: A big step. Exclude all URI terms not in [EOL terms file](https://raw.githubusercontent.com/EOL/eol_terms/main/resources/terms.yml).
Maybe a to-do: is to generate a report for all excluded term URIs for every textmined resource.

9th step: Assemble everything and generate a temporary DwCA file.

10th step: The latest ticket: [Revision for textmining keyword mappings](https://github.com/EOL/ContentImport/issues/36)
Implement the requirements of the latest ticket to the temporary DwCA file.
Because of the nature and the intention of our whitelist, I need to implement it lastly.

To-do: we still need to pick 1 of 2 possible solutions stated [here](https://github.com/EOL/ContentImport/issues/36#issuecomment-3375366269).
Personally, it will be easier to maintain our whitelists if we pick #1.

11th step: generate the final DwCA file.
-end-

Please comment if you have any questions.
Thanks.
