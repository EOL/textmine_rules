# Textmine rules

Filters, remapped lists, subset labels, etc. used in textmining connector.

1. <a href="#for-all-resources">For all resources</a>
2. <a href="#for-specific-resources">For specific resource(s)</a>

<a name="for-all-resources"></a>

## For all resources

#### Remove across all resources:

<table>
<tr><td>https://github.com/EOL/textmine_rules/blob/main/terms_to_remove.txt</td></tr>
<tr><td>https://github.com/EOL/textmine_rules/blob/main/geo_synonyms.txt</td></tr>
</table>

#### Delete MoF with these labels:

<table>
<tr>
    <td>https://github.com/EOL/textmine_rules/blob/main/del_MoF_with_these_labels.tsv</td>
</tr>
</table>

#### Patterns for all textmined resources:

<table>
<tr>
    <td>life history ontology</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/life_history.tsv</td>
</tr>
</table>

#### Others:

<table>
<tr>
    <td>Re-mapped across all resources:</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/Terms_remapped/DATA_1841_terms_remapped.tsv</td>
</tr>
<tr>
    <td>mRemark assignments</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/mRemarks_assignments.tsv</td>
</tr>
</table>

<a name="for-specific-resources"></a>

## For specific resource(s)

#### Wikipedia (inferred records)

<table>
<tr>
    <td>Remove traits for specific taxon ranks</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/Wikipedia_excluded_ranks.tsv</td>
</tr>
</table>

#### Wikipedia (inferred records) AND TreatmentBank

<table>
<tr>
    <td>Soil compositions:</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/soil_composition.tsv</td>
</tr>
<tr>
    <td>Set measurementType to:</td>
    <td>http://purl.obolibrary.org/obo/ENVO_09200008</td>
</tr>
</table>

<table>
<tr>
    <td>Exclude these labels:</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/blacklist_labels.txt</td>
</tr>
</table>

#### WoRMS

<table>
<tr>
    <td>Delete URIs</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/WoRMS_only_delete_URIs.tsv</td>
</tr>
<tr>
    <td>Re-mapped terms:</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/Terms_remapped/WoRMS_only_terms_remapped.tsv</td>
</tr>
</table>

#### AntWeb

<table>
<tr>
    <td>Exclude descendants of: “aquatic”</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/AmphibiaWeb/descendants_of_aquatic.tsv</td>
</tr>
</table>
    
#### AmphibiaWeb articles
<table>
<tr>
    <td>Exclude descendants of: “saline water”</td>
    <td>https://github.com/EOL/textmine_rules/blob/main/AmphibiaWeb/descendants_of_salt_water.tsv</td>
</tr>
</table>
