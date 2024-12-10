# OpenSea Drop - Instructions for Media and Metadata files



## Media file instructions

Supported files include JPG, PNG, SVG, and GIF. The per file size limit is 50 MB.

All files should have the same extension (e.g. all of them should be .png).



### When there is no metadata file

Media file naming can be anything you want. The tokenID will be set based on order of submission.



### When there is a metadata file

The name of the media file should be matched in the column 'file_name' in the metadata file.





## Metadata file instructions



On the metadata file, make sure that the tokenIDs are consecutive numbers. So if you have 1000 items, you must have tokenIDs consecutive from 1 to 1000 without missing any numbers.



Mandatory columns are:

- 'tokenID' -- identification of the item, which is a number between 1 and the number of files you have, consecutively

- 'name' -- name of your item (max 200 characters)

- 'file_name' -- name of your media file, including the extension



Optional columns are:

- 'description' -- description of your item

- 'external_url' -- URL shown on your item (can be an external URL to provide more information about your item)

You can add trait columns, which must follow the convention 'attributes[name_of_trait]'. For example, if you wanted eye color to be a trait, you can have a column named 'attributes[eye color]'.



