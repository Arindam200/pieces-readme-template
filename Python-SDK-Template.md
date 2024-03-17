<h1 align="center">
    <b>
        <a href="https://pieces.app">
            <img src="https://github.com/Arindam200/pieces-readme-template/assets/109217591/4a8ebb8f-a46c-49fe-a0a4-a6ee41583a99" height="125" width="600" />
        </a><br>
    </b>
</h1>

# <p align="center"> Pieces OS Client SDK For Python
   <p align="center">
      <a href="https://github.com/pieces-app/pieces-os-client-sdk-for-python" alt="GitHub contributors">
         <img src="https://img.shields.io/github/contributors/pieces-app/pieces-os-client-sdk-for-python.svg" />
      <a>
      <a href="https://github.com/pieces-app/pieces-os-client-sdk-for-python" alt="GitHub issues by-label">
         <img src="https://img.shields.io/github/issues/pieces-app/pieces-os-client-sdk-for-python" />
      </a>
      <a href="https://discord.gg/getpieces" alt="Discord">
         <img src="https://img.shields.io/badge/Discord-@layer5.svg?logo=discord" />
      </a>
      <a href="https://twitter.com/Keployio" alt="Twitter Follow">
         <img src="https://img.shields.io/twitter/follow/keploy.svg?label=Follow" />
      </a>
      <a href="https://github.com/pieces-app/cli-agent" alt="License">
         <img src="https://img.shields.io/github/license/pieces-app/pieces-os-client-sdk-for-python.svg" />
      </a>
      <a href="https://pypi.org/project/pieces_os_client" >
         <img src="https://badge.fury.io/py/pieces-os-client.svg" />
      </a>
      <a href="https://pepy.tech/project/pieces_os_client" >
         <img src="https://static.pepy.tech/badge/pieces_os_client" />
      </a>
   </p>
</p>


## Introduction

The Pieces SDK is a powerful code engine package designed for writing applications on top of Pieces OS. It facilitates communication with a locally hosted server to enable features such as copilot chats, asset saving, and more.

## Installation

To get started with the Pieces SDK, follow these steps:

1. **Download Pieces OS**: Pieces OS serves as the primary backend service, providing essential functionality for the SDK. Download the appropriate version for your operating system:
   - [macOS](https://docs.pieces.app/installation-getting-started/macos) - Compatible with macOS 11 Big Sur or higher.
   - [Windows](https://docs.pieces.app/installation-getting-started/windows) - Compatible with Windows 10 version 1809 or higher.
   - [Linux](https://docs.pieces.app/installation-getting-started/linux) - Compatible with Ubuntu 18 or higher.

2. **Install the PyPI Package**: Use pip to install the Pieces SDK package:
   ```shell
   pip install pieces-os-client
   ```

## Usage
After installing the SDK, you can import the library into your project and start utilizing its features:

```shell
from pieces_os_client.models
```
For detailed usage instructions and examples, refer to the [documentation](https://docs.pieces.app/).

## Features
The Pieces SDK offers the following key features:

1. Copilot Chats: Communicate seamlessly with copilot chats functionality.
2. Asset Management: Save and manage assets and formats efficiently.
3. Local Server Interaction: Interact with a locally hosted server for various functionalities.
4. Multi LLMs support: Use any Pieces supported LLMs to power apps.

## Requirements
The Pieces SDK has the following system requirements:

- Pieces OS running as a backend service.
- Python environment with pip for installing the SDK package.

## Testing Usage

Create a wellknown.py file and add this code to confirm you have installed the correct package:

```python
# Enter a context with an instance of the API client
with pieces_os_client.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = pieces_os_client.WellKnownApi(api_client)

    try:
        # api_instance.get_well_known_version() [Get]
        api_response = api_instance.get_well_known_version()
        print("The response of WellKnownApi->get_well_known_version:\n")
        print(api_response)
    except Exception as e:
        print("Exception when calling WellKnownApi->get_well_known_version: %s\n" % e)
``` 

**Your output should appear on your IDE terminal stating the version of the Pieces OS installed.**

## Examples
Here are a few examples of using some of the basic endpoints for getting up and running, along with creating an asset for the first time. 

A developer documentation that outlines all the ins and outs of our available endpoints can be found [here](https://github.com/pieces-app/pieces-os-client-sdk-for-python/tree/main/docs).

<details>
<summary>Connect</summary>

   When developing and creating an application on top of Pieces OS, it is important that you authenticate with the application itself when performing requests.
   
   To 'connect' your application (this Python project) to the server, you will need to make a POST request to the `api_instance.connect()` endpoint of the API and print the response.

  ```
# Enter a context with an instance of the API client
with pieces_os_client.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = pieces_os_client.ConnectorApi(api_client)
    seeded_connector_connection = pieces_os_client.SeededConnectorConnection() 
    # SeededConnectorConnection |  (optional)
    try:
        # api_instance.connect() [POST]
        api_response = api_instance.connect(seeded_connector_connection=seeded_connector_connection)
        print("The response of ConnectorApi->connect:\n")
        print(api_response)
    except Exception as e:
        print("Exception when calling ConnectorApi->connect: %s\n" % e)     
  ```
  
</details>
<details>
<summary>Creating with Asset & /Assets</summary>

   **Asset** is a very important model whose primary purpose is to manage the seeded data that comes into the application and is stored inside of Pieces OS. Each asset is identifiable as a piece of saved data, or pre-seeded data.

**/Assets** is equally important, but instead of containing a single asset with parameters storing data on it, Assets serves as the list of type: Asset objects that are stored there. Also, you will find the operations for adding, deleting, searching, and other functions that are related to referencing a number of different snippets to make a comparison.

</details>
<details>
<summary>SeededAsset</summary>

   SeededAsset is the **Format** needed by `/assets/create` in order to accept the snippet, create, and return the information you need. The structure (at a bare minimum) is as follows:

```python
 
from pieces_os_client.models.seeded_asset import SeededAsset

# TODO update the JSON string below
json = "{}"
# create an instance of SeededAsset from a JSON string
seeded_asset_instance = SeededAsset.from_json(json)
# print the JSON string representation of the object
print SeededAsset.to_json()

# convert the object into a dict
seeded_asset_dict = seeded_asset_instance.to_dict()
# create an instance of SeededAsset from a dict
seeded_asset_form_dict = seeded_asset.from_dict(seeded_asset_dict)
```
</details>
<details>
<summary>Get your Assets Snapshot</summary>

   When working with your app implementation you will often need to call the entire asset snapshot in order to get the correct snippet from your storage in Pieces OS. You can use this asset snapshot by passing the asset's ID and a boolean value indicating whether or not to return transferable data. The response from the API is then printed to the console.

```python
 
# Enter a context with an instance of the API client
with pieces_os_client.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = pieces_os_client.AssetApi(api_client)
    asset = '2254f2c8-5797-40e8-ac56-41166dc0e159' # str | The id (uuid) of the asset that you are trying to access.
    transferables = True # bool | This is a boolean that will decide if we want to return the transferable data (default) or not (performance enhancement) (optional)
    seeded_accessor = pieces_os_client.SeededAccessor() # SeededAccessor |  (optional)

    try:
         # api_instance.asset_snapshot(asset, transferables=transferables, seeded_accessor=seeded_accessor) [POST] Scoped to an Asset
        api_response = api_instance.asset_snapshot_post(asset, transferables=transferables, seeded_accessor=seeded_accessor)
        print("The response of AssetApi->asset_snapshot_post:\n")
        print(api_response)
    except Exception as e:
        print("Exception when calling AssetApi->asset_snapshot_post: %s\n" % e)
```
</details>
<details>
<summary>Updating your Assets</summary>

   Individual assets can be manipulated with a number of different properties and metadata. You can add titles, annotations, tags, links, anchors, and much more all through this single endpoint. To use the asset_update method of the AssetAPi class, pass a boolean value for transferables and an instance of the Asset class for the asset. It should update the asset in the database and print the response from the API call.

```python
 
# Enter a context with an instance of the API client
with pieces_os_client.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = pieces_os_client.AssetApi(api_client)
    transferables = True # bool | This is a boolean that will decide if we want to return the transferable data (default) or not (performance enhancement) (optional)
    asset = pieces_os_client.Asset() # Asset | This is the updated Asset that needs to be updated in our db. (optional)

    try:
        # api_instance.asset_update(transferables=transferables, asset=asset) [POST] Scoped to Asset
        api_response = api_instance.asset_update(transferables=transferables, asset=asset)
        print("The response of AssetApi->asset_update:\n")
        print(api_response)
    except Exception as e:
        print("Exception when calling AssetApi->asset_update: %s\n" % e)
```
</details>
<details>
<summary>Deleting an Asset</summary>

   Similar to the previous example, you need assetSnapshot in order to access the proper asset on your list of data. You can use this endpoint to completely delete a specific asset wherever it may be in the list of all of your assets by taking a UID to delete out of the assets table.

```python
 
# Enter a context with an instance of the API client
with pieces_os_client.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = pieces_os_client.AssetsApi(api_client)
    asset = '2254f2c8-5797-40e8-ac56-41166dc0e159' # str | The id (uuid) of the asset that you are trying to access.

    try:
        # api_instance.assets_delete_asset(asset) [POST] Scoped to Asset
        api_response = api_instance.assets_delete_asset(asset)
        print("The response of AssetsApi->assets_delete_asset:\n")
        print(api_response)
    except Exception as e:
        print("Exception when calling AssetsApi->assets_delete_asset: %s\n" % e)
```
</details>

## Contributing
Contributions to the Pieces SDK are welcome! To contribute, follow these steps:

Install Poetry:

```shell
pip install poetry
```

Install dependencies:

```shell
poetry install
```

Build the project:

```shell
poetry build
```

Add project dependencies:

```shell
poetry add <dependency>
```



## Learn More / Support
Explore more about Pieces SDK and get help from the following resources:

- 🚀 [Getting Started Tutorial](https://docs.pieces.app/installation-getting-started/what-am-i-installing)
- 📜 [Pieces Docs](https://docs.pieces.app/)
- 💬 [Discord Community](https://discord.gg/getpieces)

## License

This repository is available under the [MIT License](./LICENSE).



