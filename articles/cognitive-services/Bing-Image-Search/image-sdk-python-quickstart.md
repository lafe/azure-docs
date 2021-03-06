---
title: "Quickstart: Search for images - Bing Image Search SDK for Python"
titleSuffix: Azure Cognitive Services
description: Use this quickstart to make your first image search using the Bing Image Search SDK, which is a wrapper for the API and contains the same features. This simple Python application sends an image search query, parses the JSON response, and displays the URL of the first image returned.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-image-search
ms.topic: quickstart
ms.date: 08/28/2018
ms.author: aahi
ms.custom: seodec2018
---
# Quickstart: Search for images with the Bing Image Search SDK for Python

Use this quickstart to make your first image search using the Bing Image Search SDK, which is a wrapper for the API and contains the same features. This simple Python application sends an image search query, parses the JSON response, and displays the URL of the first image returned.

The source code for this sample is available [on GitHub](https://github.com/Azure-Samples/cognitive-services-python-sdk-samples/blob/master/samples/search/image-search-quickstart.py) with additional error handling and annotations.

## Prerequisites
Get a [Cognitive Services access key](https://azure.microsoft.com/try/cognitive-services/) under **Search**.  See also [Cognitive Services Pricing - Bing Search API](https://azure.microsoft.com/pricing/details/cognitive-services/search-api/).

* [Python 2.7 or 3.4](https://www.python.org/) and higher.

* The [Azure Image Search SDK](https://pypi.org/project/azure-cognitiveservices-search-imagesearch/) for Python
    * Install using `pip install azure-cognitiveservices-search-imagesearch`

[!INCLUDE [cognitive-services-bing-image-search-signup-requirements](../../../includes/cognitive-services-bing-image-search-signup-requirements.md)]

## Create and initialize the application

1. Create a new Python script in your favorite IDE or editor, and the following imports:

    ```python
    from azure.cognitiveservices.search.imagesearch import ImageSearchAPI
    from msrest.authentication import CognitiveServicesCredentials
    ```

2. Create variables for your subscription key and search term.

    ```python
    subscription_key = "Enter your key here"
    search_term = "canadian rockies"
    ```

## Create the image search client

3. Create an instance of `CognitiveServicesCredentials`, and use it to instantiate the client:

    ```python
    client = ImageSearchAPI(CognitiveServicesCredentials(subscription_key))
    ```
4. Send a search query to the Bing Image Search API:
    ```python
    image_results = client.images.search(query=search_term)
    ```
## Process and view the results

Parse the image results returned in the response.


If the response contains search results, store the first result and print out its details, such as a thumbnail URL, the original URL,along with the total number of returned images.  

```python
if image_results.value:
    first_image_result = image_results.value[0]
    print("Total number of images returned: {}".format(len(image_results.value)))
    print("First image thumbnail url: {}".format(first_image_result.thumbnail_url))
    print("First image content url: {}".format(first_image_result.content_url))
else:
    print("No image results returned!")
```

## Next steps

> [!div class="nextstepaction"]
> [Bing Image Search single-page app tutorial](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/tutorial-bing-image-search-single-page-app)

## See also

* [What is Bing Image Search?](https://docs.microsoft.com/azure/cognitive-services/bing-image-search/overview)  
* [Try an online interactive demo](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)  
* [Get a free Cognitive Services access key](https://azure.microsoft.com/try/cognitive-services/?api=bing-image-search-api)
* [Python samples for the Azure Cognitive Services SDK](https://github.com/Azure-Samples/cognitive-services-python-sdk-samples)  
* [Azure Cognitive Services Documentation](https://docs.microsoft.com/azure/cognitive-services)
* [Bing Image Search API reference](https://docs.microsoft.com/rest/api/cognitiveservices/bing-images-api-v7-reference)
