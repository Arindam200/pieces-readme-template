<h1 align="center">
    <b>
        <a href="https://pieces.app">
            <picture>
                <source srcset="https://camo.githubusercontent.com/69c990240f877927146712d45be2f690085b9e45b4420736aa373917f8e0b2c8/68747470733a2f2f73746f726167652e676f6f676c65617069732e636f6d2f7069656365735f7374617469635f7265736f75726365732f7066645f77696b692f5049454345535f4d41494e5f4c4f474f5f57494b492e706e67" media="(prefers-color-scheme: light)">
                <source srcset="https://github.com/Arindam200/pieces-readme-template/assets/109217591/4a8ebb8f-a46c-49fe-a0a4-a6ee41583a99" media="(prefers-color-scheme: dark)">
                <img src="https://github.com/Arindam200/pieces-readme-template/assets/109217591/4a8ebb8f-a46c-49fe-a0a4-a6ee41583a99" height="125" width="600" />
            </picture>
        </a><br>
    </b>
</h1>

# <p align="center"> Pieces OS Client SDK For TypeScript
   <p align="center">
      <a href="https://github.com/pieces-app/pieces-os-client-sdk-for-typescript" alt="GitHub contributors">
         <img src="https://img.shields.io/github/contributors/pieces-app/pieces-os-client-sdk-for-typescript.svg" />
      <a>
      <a href="https://github.com/pieces-app/pieces-os-client-sdk-for-typescript" alt="GitHub issues by-label">
         <img src="https://img.shields.io/github/issues/pieces-app/pieces-os-client-sdk-for-typescript" />
      </a>
      <a href="https://discord.gg/getpieces" alt="Discord">
         <img src="https://img.shields.io/badge/Discord-@layer5.svg?color=7389D8&label&logo=discord&logoColor=ffffff" />
      </a>
      <a href="https://twitter.com/getpieces" alt="Twitter Follow">
         <img src="https://img.shields.io/twitter/follow/pieces.svg?label=Follow" />
      </a>
      <a href="https://github.com/pieces-app/cli-agent" alt="License">
         <img src="https://img.shields.io/github/license/pieces-app/pieces-os-client-sdk-for-python.svg" />
      </a>
      <a href="https://badge.fury.io/js/@pieces.app%2Fpieces-os-client" >
         <img src="https://badge.fury.io/js/@pieces.app%2Fpieces-os-client.svg" />
      </a>
      <a href="https://img.shields.io/npm/dm/@pieces.app/pieces-os-client.svg" >
         <img src="https://img.shields.io/npm/dm/@pieces.app/pieces-os-client.svg" />
      </a>
      <a href="https://img.shields.io/npm/dt/@pieces.app/pieces-os-client.svg" >
         <img src="https://img.shields.io/npm/dt/@pieces.app/pieces-os-client.svg" />
      </a>
   </p>
</p>


## Introduction

**@pieces.app/pieces-os-client** is an open-source on-device AI development workflow assistant.

This package contains endpoints for communicating with [Pieces OS](https://docs.pieces.app/installation-getting-started/pieces-os) to add Pieces Copilot conversations or save code snippets and resources - entirely offline and on device with Local Large Language Models (LLLMs) keeping your data secure.

Follow [this guide](https://code.pieces.app/blog/build-your-own-copilot-in-less-than-10-minutes-with-pieces-os-client) to get started with the Pieces Client in your own development environment. Check out the table of contents below to understand specific functionality, but we recommend reading along the [Copilot Series](https://code.pieces.app/blog/build-your-own-open-source-copilot-with-pieces).

## Installation

To get started with the Pieces SDK, follow these steps:

### 1. Downloading Pieces OS

Pieces OS runs in the background of your computer and serves as a hub for all plugins and extensions developed by the team. In order to utilize your own Server locally and support all the functionality that powers things like [Global Search](https://docs.pieces.app/features/global-search), [Copilot Chats](https://docs.pieces.app/features/pieces-copilot), [Asset Saving](https://docs.pieces.app/features/managing-saved-materials), [context](https://docs.pieces.app/features/pieces-copilot#set-your-own-copilot-context), and more.

Select the right version to download Pieces OS for your operating system:

- [macOS](https://docs.pieces.app/installation-getting-started/macos)
- [Windows](https://docs.pieces.app/installation-getting-started/windows)
- [Linux](https://docs.pieces.app/installation-getting-started/linux) 

### 2. Downloading NPM Package

Using npm:

```bash
npm install @pieces.app/pieces-os-client
```
Using pnpm:

```bash
pnpm add @pieces.app/pieces-os-client
```

## Usage
After you install the package, you can import the library into your file(s) using require:

```javascript
const pieces = require('@pieces.app/pieces-os-client')
```

or you can import the package using import as well:

```javascript
import * as pieces from '@pieces.app/pieces-os-client'
```

> **Recommendation**
> The order that npm packages are saved and added to your dependencies is important and will affect your installation flow. **This slowed me down for quite a bit.**
>
> **If you are having issues with your installation, it is likely due to a conflict in Typescript versions - `npm uninstall typescript` - then go back and perform all other npm installations before reinstalling typescript again**.

You can get it here: [GitHub Repo](https://github.com/pieces-app/example-typescript)

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
- NodeJs environment with npm for installing the SDK package.

## Testing Usage
When your program starts, it needs to connect to Pieces OS to gain access to any functional data and to exchange information on the `localhost:1000` route. Now that you have your `tracked_application` - lets get into the details.

Start by defining you connect function and prepare the `connectorApi` on `Pieces.ConnectorApi().connect()` passing in the `tracked_applicaition` we created above:

```tsx
export async function connect(): Promise<JSON> {
  const connectorApi = new Pieces.ConnectorApi();
  const response = await connectorApi.connect({
    seededConnectorConnection: { application: tracked_application },
  });
  
  return JSON.parse(JSON.stringify(response));
}
```

Here is the entire connect function for you to double-check your work:

```tsx
const tracked_application = {
  name: Pieces.ApplicationNameEnum.OpenSource,
  version: '0.0.1',
  platform: Pieces.PlatformEnum.Macos,
}


export async function connect(): Promise<JSON> {
  const connectorApi = new Pieces.ConnectorApi();

  const response = await connectorApi.connect({
    seededConnectorConnection: { application: tracked_application },
  });

  return JSON.parse(JSON.stringify(response));
}
```

## Examples
Here are a few examples of using some of the basic endpoints for getting up and running, along with creating an asset for the first time. 

A developer documentation that outlines all the ins and outs of our available endpoints can be found [here](https://github.com/pieces-app/pieces-os-client-sdk-for-python/tree/main/docs).


<details>
<summary>Create New Assets</summary>

Now before continuing forward, we will need to prepare the `create()` function to connect to the proper creation endpoint. Create differs from connect, since previously our json object did not require any preprocessing. In this case **we will need to include the application data that was returned back from our initial call to `connect()`.**

The `createAsset()` function needs to accomplish:

1. Create our raw `data` var for seeding the asset.
2. Creating a new asset using our simple `Pieces.SeededAsset` configuration
3. Send request via `Pieces.AssetsApi().assetsCreateNewAsset()`
4. Return the created asset back after it is validated and created

Here is what the `createAsset()` function looks like in its entirety:

```tsx
// importing the package into this file.
import * as pieces from '@pieces.app/pieces-os-client'

// @var code data as a string.
var data = "<h1>Hello world</h1>";

// @var title for your snippet creation.
var name = "My First Snippet";

// the create asset function where we create our seeded asset.
// @var applicationData | look back at connect() to see where this came from
function createAsset() {
  let _seededAsset: Pieces.SeededAsset = {
    application: applicationData,
    format: {
      fragment: {
        string: {raw: data},
      },
    },
    metadata: {
      name: name
    }
  }

  // create your seed
  let _seed: Pieces.Seed = {
    asset: _seededAsset,
    type: SeedTypeEnum.Asset
  }

  // make your api call.
  new Pieces.AssetsApi().assetsCreateNewAsset({seed: _seed}).then(newAsset => {
    console.log(`New Asset Created --> ${newAsset}`);
  });
}
```

The response back will look similar to the following: [https://jwaf.pieces.cloud/?p=24e242a85e](https://jwaf.pieces.cloud/?p=24e242a85e)

</details>


<details>
<summary>Get your Assets Snapshot</summary>

When reading along, if you would like to view your data incrementally through the full browser window, you can navigate to `http://localhost:1000/assets` to view a full list of snippets that have been saved in your browser. Otherwise, you can access the snapshot with these steps:

```tsx
new Pieces.AssetsApi().assetsSnapshot({}).then(_assetList => {
    for (let i = 0; i < _assetList.iterable.length; i++) {
        // will log each asset.
       console.log(_assetsList[i]);
    }
})
```
</details>

<details>

<summary>Refresh your Assets Snapshot</summary>

In order to get updates to your assetSnapshot as a whole, you may need to update you local list in order to reflect changes that come from Pieces OS and give information on the assets stored there. In order to perform a refresh you can use this code block here:

```tsx
const [array, setArray] = useState([]);

const refresh = (_newAsset: LocalAsset) => {
    setArray(prevArray => [...prevArray, _newAsset])
}

function refreshSnippetList() {
    new Pieces.AssetsApi().assetsSnapshot({}).then((assets) => {
        
        // loop through your assets.
        for (let i = 0; i < assets.iterable.length; i++) {
            let _local: LocalAsset = {
                id: assets.iterable[i].id,
                name: assets.iterable[i].name,
                classification: assets.iterable[i].original.reference.classification.specific
            }

            refresh(_local);

        }
    })
}
```

I added this to the top level for reactivity inside the main `App()` call. You can choose to place this in a different location if you are not in need of any reactive data.
</details>

<details>

<summary>Delete your Assets Snapshot</summary>

Assets can be deleted from your Assets list entirely by passing them into the `assetsDeleteAsset` endpoint. Just like the above example to rename a specific asset, you will need the ID of the asset that you are trying to remove. In order to get that you will need to use assetSnapshot in tandem with your delete endpoint:

```tsx
 new Pieces.AssetsApi().assetsSnapshot({}).then(_assetList => {
    for (let i = 0; i < _assetList.iterable.length; i++) {
        if (_assetList.iterable[i].id == _id) {
            new Pieces.AssetsApi().assetsDeleteAsset({asset: _assetList.iterable[i].id }).then(_ => console.log("delete confirmed!"))
        }
    }
})
```

After a successful delete, you may have to reload your browser window in order to see the updated snippet list.

> **Recommendation**  
> We use [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh) internally when developing and **recommend** using some form of web based extension that assists with reading JSON DATA
</details>

<details>

<summary>Search through Snippets</summary>

The search API can be used to filter or search through snippets that have been saved, then perform specific actions on them based on a set of rules. Here is a brief example of searching where `query: "page"` is your search term:

```typescript
new Pieces.SearchApi().fullTextSearch({ query: "page" }).then( searchedAssets => {

    // get the "ID" or identifier of the first match on the string you passed in as the query:
    let firstSearchMatchAssetIdentifier = searchedAssets.iterable[0].identifier;

    let matchName: String;

    // take that identifier to get your assets name using the Pieces.AssetApi()
    new Pieces.AssetApi().assetSnapshot({asset: firstSearchMatchAssetIdentifier}).then((asset) => {
      // assign that name to the matchName variable:
      matchName = asset.name;
      console.log(matchName);
    })
    // then you can do whatever you would like with that match:   
  return matchName;
})
```
</details>



## Contributing
Contributions to the Pieces SDK are welcome! To contribute, follow these steps:

## Learn More 
Explore more about Pieces SDK and get help from the following resources:

- 🚀 [Getting Started Tutorial](https://docs.pieces.app/installation-getting-started/what-am-i-installing)
- 📜 [Pieces Docs](https://docs.pieces.app/)
- 💬 [Discord Community](https://discord.gg/getpieces)

## License

This repository is available under the [MIT License](./LICENSE).
