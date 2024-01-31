# GalileoFigaro API Documentation

## Introduction

Welcome to the GalileoFigaro API, designed to facilitate file pinning to IPFS on the GalileoFigaro platform. This documentation outlines how to interact with the API using Postman.

## Authentication

To access the API, include an `Authorization` header in your requests with a Bearer token.

**Base URL**: `https://demo.galileofigaro.io/api/ipfs/`

## Endpoints

### 1. Pin Files to IPFS

**Endpoint**: `/pinToIPFS`

**Method**: `POST`

#### Request

- **Headers:**
  - `Authorization`: Bearer Token

- **Parameters:**
  - `action`: `"pinToIPFS"`
  - `license_number`: License number associated with the files.
  - `parameters_json_string`: JSON string containing parameters.

- **Files:**
  - `file_license`: License file (PNG format).
  - `file_content`: Content file (PNG format).

#### Response

- **Success (HTTP Status 201):**
  - Returns JSON data with details about the pinned files.
    ```json
    {
      "status_code": 201,
      "msg": "Successfully Uploaded to IPFS",
      "data": {
        "points_per_request": 3,
        "current_request_amount": 6,
        "request_limit": 20,
        "license_json_cid": "your_license_json_cid",
        "license_cid": "your_license_cid",
        "content_cid": "your_content_cid",
        "license_json_ipfs_path": "https://gateway.pinata.cloud/ipfs/your_license_json_cid",
        "license_ipfs_path": "https://gateway.pinata.cloud/ipfs/your_license_cid",
        "content_ipfs_path": "https://gateway.pinata.cloud/ipfs/your_content_cid"
      }
    }
    ```

- **Error Responses:**
  - Various HTTP status codes with corresponding error messages.

## Example Usage

### 1. Pin Files to IPFS

- **Request:**
  - POST to `https://demo.galileofigaro.io/api/ipfs/`
  - Headers: `Authorization: Bearer your_token`
  - Parameters:
    - `action: "pinToIPFS"`
    - `license_number: "your_license_number"`
    - `parameters_json_string: "{"is AI generated":"no","is AI free":"yes","Are you sure?":"I'm sure", "key4": "some value"}"`
  - Files:
    - `file_license`: Your license file (PNG format).
    - `file_content`: Your content file (PNG format).

- **Response:**
  - JSON response with details about the pinned files.
 
### Example Scenario

The 'cccc' license was registered three times:

1. [https://gateway.pinata.cloud/ipfs/QmZAvXo4yVu3GMQAHXEcUdzMLrdMGJf6subhFxWp4SkFWa](https://gateway.pinata.cloud/ipfs/QmZAvXo4yVu3GMQAHXEcUdzMLrdMGJf6subhFxWp4SkFWa)
2. [https://gateway.pinata.cloud/ipfs/QmfUJFnGS3PF68qBCbx4EVdtbuXAySF42XfEjEdD7jfsJr](https://gateway.pinata.cloud/ipfs/QmfUJFnGS3PF68qBCbx4EVdtbuXAySF42XfEjEdD7jfsJr)
3. [https://gateway.pinata.cloud/ipfs/QmTXtMoz11qU7PhEYy5eocNUNzGZRypqWA1mpwYDiKiSEF](https://gateway.pinata.cloud/ipfs/QmTXtMoz11qU7PhEYy5eocNUNzGZRypqWA1mpwYDiKiSEF)

### 2. Get License Information

**Endpoint**: `/getLicense`

**Method**: `GET`

#### Request

- **Parameters:**
  - `action`: `"getLicense"`
  - `username`: Your User Name.
  - `license_number`: License number associated with the files.

  - GET to https://demo.galileofigaro.io/api/ipfs/?action=getLicense&username=your_username&license_number=your_license_number
Response:

  - JSON response with details about the retrieved license information.
 
    - **Success (HTTP Status 200):**
  - Returns JSON data with details about the pinned files.
    ```json
    { "status_code": 200, "msg": "License List retrieved successfully.", "data": { "profile": { "name": "AiID", "img": "https://demo.galileofigaro.io/api/ipfs/logo.jpeg", "username": "aiid" }, "licenses": [ { "license_number": "12345abcde", "history": [ { "path": "https://gateway.pinata.cloud/ipfs/QmThcHJCTtCX2vw3fMvtk5tLZCxVHGVTQqsVMLHPWFUtW9", "date": "2024-01-31 06:52:53", "ipfs_data": { "parameters": { "is AI generated": "no", "is AI free": "yes", "Are you sure?": "I'm sure", "key4": "some value" }, "license_cid": "https://gateway.pinata.cloud/ipfs/QmX8PsprwzYUfyXueGSRnpjRhAmEPSLvYnTjbUu7q2e5dc", "content_cid": "https://gateway.pinata.cloud/ipfs/Qmb2GPhRi5vRV65PCckKPWjkz6AB7MKLPVA6Ci9b3XBxx1" } }, { "path": "https://gateway.pinata.cloud/ipfs/QmR37YpwHq11METAJJNyVnUsUTSy1N4Tq84SmreMQdnPyP", "date": "2024-01-31 06:20:12", "ipfs_data": { "parameters": { "is AI generated": "no", "is AI free": "yes", "Are you sure?": "I'm sure", "key4": "some value" }, "license_cid": "https://gateway.pinata.cloud/ipfs/QmX8PsprwzYUfyXueGSRnpjRhAmEPSLvYnTjbUu7q2e5dc", "content_cid": "https://gateway.pinata.cloud/ipfs/QmRko9bcgfM2fJ4UWuqRXFX8XenqVXpGFc2Q6bRupvzavL" } } ] } ] } }
    ```

- **Error Responses:**
  - Various HTTP status codes with corresponding error messages.
  - Please replace your_username and your_license_number with the actual values you intend to use.

### 3. Get License List

#### Request

**Endpoint**: `/getLicenseList`

**Method**: `GET`

- **Parameters:**
  - `action`: `"getLicenseList"`
  - `username`: Your User Name.
 
  - GET to https://demo.galileofigaro.io/api/ipfs/?action=getLicenseList&username=your_username
Response:

  - JSON response with details about the retrieved license list.
 
- **Success (HTTP Status 200):**
  - Returns JSON data with details about the pinned files.
    ```json
    { "status_code": 200, "msg": "License List retrieved successfully.", "data": { "profile": { "name": "AiID", "img": "https://demo.galileofigaro.io/api/ipfs/logo.jpeg", "username": "aiid" }, "licenses": [ { "license_number": "99999aaaaa", "history": [ { "path": "https://gateway.pinata.cloud/ipfs/QmYgVDa25gYcYT3R5heSuvciKQCpiBguVDZY7TsFpcKprN", "date": "2024-01-31 06:55:28", "ipfs_data": { "parameters": { "is AI generated": "no", "is AI free": "yes", "Are you sure?": "I'm sure", "key4": "some value" }, "license_cid": "https://gateway.pinata.cloud/ipfs/QmX8PsprwzYUfyXueGSRnpjRhAmEPSLvYnTjbUu7q2e5dc", "content_cid": "https://gateway.pinata.cloud/ipfs/QmSPuLnLfAFHVoJsfZn8q9PafgAHrjMdUK1xitzRSzhA8n" } } ] }, { "license_number": "12345abcde", "history": [ { "path": "https://gateway.pinata.cloud/ipfs/QmThcHJCTtCX2vw3fMvtk5tLZCxVHGVTQqsVMLHPWFUtW9", "date": "2024-01-31 06:52:53", "ipfs_data": { "parameters": { "is AI generated": "no", "is AI free": "yes", "Are you sure?": "I'm sure", "key4": "some value" }, "license_cid": "https://gateway.pinata.cloud/ipfs/QmX8PsprwzYUfyXueGSRnpjRhAmEPSLvYnTjbUu7q2e5dc", "content_cid": "https://gateway.pinata.cloud/ipfs/Qmb2GPhRi5vRV65PCckKPWjkz6AB7MKLPVA6Ci9b3XBxx1" } }, { "path": "https://gateway.pinata.cloud/ipfs/QmR37YpwHq11METAJJNyVnUsUTSy1N4Tq84SmreMQdnPyP", "date": "2024-01-31 06:20:12", "ipfs_data": { "parameters": { "is AI generated": "no", "is AI free": "yes", "Are you sure?": "I'm sure", "key4": "some value" }, "license_cid": "https://gateway.pinata.cloud/ipfs/QmX8PsprwzYUfyXueGSRnpjRhAmEPSLvYnTjbUu7q2e5dc", "content_cid": "https://gateway.pinata.cloud/ipfs/QmRko9bcgfM2fJ4UWuqRXFX8XenqVXpGFc2Q6bRupvzavL" } } ] } ] } }
  - Please replace your_license_number with the actual value you intend to use.
