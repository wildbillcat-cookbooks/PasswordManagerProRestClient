Password Manager Pro Rest Client
===================================
Provides a Rest Client for use by Chef Client in Recipes.

Attributes
----------
* `node['PasswordManagerProRestClient']['PMPServer']` - Used to store the dns name of the pmp server. Typically should be overridden by environment. default is LocalHost
* `node['PasswordManagerProRestClient']['api_key']` - Used to Store the API Key of the Host. Typically should be overridden by environment or stored in a databag. default is 1234abcd
* `node['PasswordManagerProRestClient']['port']` - Used to store the port number the PMP rest service runs on. Typically should be overridden by environment. default is 7272
* `node['PasswordManagerProRestClient']['enable_insecure_ssl']` - Used to store if SSL validation should be skipped. Typically should be overridden by environment. default is false


Examples
---------
  
```ruby
# Fetch Password Using Rest Client and Attributes
rest_client = PasswordManagerProRestClient.new(node['PasswordManagerProRestClient']['PMPServer'], node['PasswordManagerProRestClient']['api_key'])
rest_client.get_resource_account_password("RemoteServerResource", "AccountName")
```
  
  
```ruby
# Fetch Password Using Rest Client with Attributes and Data Bag
APIKey = (search(:client_keys, "id:#{node.name}").first)["api_key"]
rest_client = PasswordManagerProRestClient.new(node['PasswordManagerProRestClient']['PMPServer'], node['PasswordManagerProRestClient']['api_key'], node['PasswordManagerProRestClient']['port'], true)
rest_client.get_resource_account_password("RemoteServerResource", "AccountName")
```