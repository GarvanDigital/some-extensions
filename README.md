# some-extensions
Some Extension ideas

**Not officially supported by Contentstack**

## dropdown-field-key-value
The built-in select field in Contentstack does not give the user the chance to have key values in the select field. This custom extension is a dropdown field (single choice) that separates the key (label shown to the editor) and value (Actual value that the API sees).

Config Parameter Example:
```
{
    "One": 1,
    "Two": 2,
    "Three": 3
}
```
The key is what the editor sees. The value is the actual JSON value.

**NOTE:** Set the _"Field data type"_ in Contentstack to match the type definition of the value in the config parameters above. This example uses _Number_

**ANOTHER NOTE:** Change every mention of the `config`, from `extensionField.config` to `extensionField.fieldConfig` if you want to define the available options inside the content type builder instead of in the extension itself.

## key-value-from-a-different-stack
A key value field that looks up entries of defined content type and language in an different stack (can be configured to use the same stack).

Fetches a field value from the external entry. Example content type definition included in the folder (key-value-from-a-different-stack/key_value_lookup.json) and can be imported via Contentstack web application UI.

Extension Config Parameter Example:
```
{
	"region": "https://eu-cdn.contentstack.com/v3", // or https://cdn.contentstack.io/v3
	"api_key": "<stack api key>",
	"access_token": "<environment delivery token)",
	"content_type": "key_value_lookup",
	"environment": "<environment name - e.g. development>",
	"locale": "<locale - e.g. en-us>"
}
```

## image-preview
A preview of the image in the entry - Just a bigger view. Using the image delivery API.

Config Parameter Example:
```
{
    "imageField": "image",
    "region": "https://eu-images.contentstack.com"
}
```
`imageField` is just the uid of the image field that the preview will be created from.

`region` can be https://eu-images.contentstack.com or https://images.contentstack.io

## quill-rte
https://quilljs.com/ - Custom field RTE
## summernote-rte
https://summernote.org/ - Custom field RTE

## value-in-master-locale
Shows the value of some entry in the master language. Nice to have in localized versions of entries if you quickly want to see a field value from the master language.

Config Parameter Example:
```
{
    "field_uid": "textfield",
    "master_locale": "en-us"
}
```
`field_uid` is the field you want to show the value from


## Nested References Custom Field
Shows all available nested references from the current entry. 
Current limitations:

1. It does not publish the current entry.
2. It does not publish the current entry assets.
3. Currently it uses on change to check for reference updates, so it checks for everytime a field changes (obviously not good). Needs to be updated to check only when references change.

Config Parameter Example:
```
{
	"environments": [
		"production",
		"staging"
	],
	"locales": [
		"en-us"
	]
}
```

## Dashboard extension access based on custom Role
This is a workaround to restrict Dashboard extension view based on custom role

1. Create a custom role (suppose i.e Access to DB Extension) and assign this role to stack users whom you don't wanna give access to the specific DB extension .
2. Set hosted method as Hosted by Contentstack 
3. Use [Html Code](https://github.com/Contentstack-Solutions/some-extensions/blob/main/Dashboard-Extension-role-based-access/index.html) in Dashboard-Extension-role-based-access Folder and use it in your Dashboard Extension to check if logged in stack user is having access or not i.e if isDBExtensionAccess is true then you can write code for conditionally display Dashboard extensions view.
4. Even you can do diffrent Functionality or view for diffrent custom Roles by conditional rendering.
5. You can also use extension Config to have array of roles or roles-uid to be restricted and write some code to restrict them.
