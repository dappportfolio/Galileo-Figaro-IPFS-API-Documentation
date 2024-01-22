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
    - `parameters_json_string: "{\"key1\":\"value1\",\"key2\":\"value2\",\"key3\":\"value3\"}"`
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
