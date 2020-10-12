# test page

{% api-method method="get" host="https://grcschema.p.rapidapi.com/ADHierarchy" path="/" %}
{% api-method-summary %}
Geographic Hierarchy List
{% endapi-method-summary %}

{% api-method-description %}
This method provides the AD Hiearchy list providing a means to assemble the structure of authority documents and their parent categories.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="useQueryString" type="string" required=true %}
true
{% endapi-method-parameter %}

{% api-method-parameter name="x-rapidapi-key" type="string" required=true %}
your API key goes here
{% endapi-method-parameter %}

{% api-method-parameter name="x-rapidapi-host" type="string" required=true %}
grcschema.p.rapidapi.com
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The Hierarchy List is a collection of Authority Documents \(category\_id=1\), Categories \(category\_id=2\), Glossaries \(category\_id=3\), and Organizations \(category\_id=4\).   
  
The response returned by the ADHierarchy endpoint allows you to build the full hierarchy structure as demonstrated in the response sample data.  
  
&gt; id:20000 - **Sample Category Name** \(sort value 1, has children\)  
      id:100000 - **Sample AD Name** \(sort value 1, has no children\)  
   &gt; id:400000 - **Sample Organization Name** \(sort value 2, has children\)  
         id:300000 - **Sample Glossary Name** \(sort value 1, has no children\)
{% endapi-method-response-example-description %}

```
[
	{
		"@context": "http://grcschema.org/",
		"@type": "ADHierarchy",
		"parent_id": 200000,
		"sort_value": 1,
		"genealogy": "0000000",
		"organization_id": null,
		"organization_name": null,
		"ad_id": 100000,
		"ad_name": "Sample AD Name",
		"category_id": 1,
		"category_name": "AD",
		"has_children": null
	},
	{
		"@context": "http://grcschema.org/",
		"@type": "ADHierarchy",
		"parent_id": null,
		"sort_value": 1,
		"genealogy": "0000000",
		"organization_id": null,
		"organization_name": null,
		"ad_id": 200000,
		"ad_name": "Sample Category Name",
		"category_id": 2,
		"category_name": "CA",
		"has_children": 1
	},
	{
		"@context": "http://grcschema.org/",
		"@type": "ADHierarchy",
		"parent_id": 400000,
		"sort_value": 1,
		"genealogy": "0000000",
		"organization_id": null,
		"organization_name": null,
		"ad_id": 300000,
		"ad_name": "Sample Glossary Name",
		"category_id": 3,
		"category_name": "GL",
		"has_children": null
	},
	{
		"@context": "http://grcschema.org/",
		"@type": "ADHierarchy",
		"parent_id": 200000,
		"sort_value": 2,
		"genealogy": "0000000",
		"organization_id": null,
		"organization_name": null,
		"ad_id": 400000,
		"ad_name": "Sample Organization Name",
		"category_id": 4,
		"category_name": "OR",
		"has_children": 1
	}
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



