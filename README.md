# Getting Started with Youtube Search API

## Getting Started

### Introduction

Serach api of youtube data

### Installation

The following section explains how to use the Youtube Search APILib library in a new project.

### Initialize the API Client

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| `timeout` | `number` | Timeout for API calls.<br>*Default*: `0` |
| `accessToken` | `string` | The OAuth 2.0 Access Token to use for API requests. |

The API client can be initialized as follows:

```ts
const client = new Client({
  timeout: 0,
  accessToken: 'AccessToken',
})
```

### Authorization

This API uses `OAuth 2 Bearer token`.

### API Errors

Here is the list of errors that the API might throw.

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Key is not valid | `ApiError` |

## Client Class Documentation

### Youtube Search API Client

The gateway for the SDK. This class acts as a factory for the Controllers and also holds the configuration of the SDK.

### Controllers

| Name | Description |
|  --- | --- |
| aPI | Gets ApiController |

## API Reference

### List of APIs

* [API](#api)

### API

#### Search

:information_source: **Note** This endpoint does not require authentication.

```ts
async search(
  key: string,
  q?: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<unknown>>
```

##### Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `key` | `string` | Query, Required | - |
| `q` | `string \| undefined` | Query, Optional | - |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

##### Response Type

`unknown`

##### Example Usage

```ts
const key = 'key0';
try {
  const { result, ...httpResponse } = await apiController.search(key);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch(error) {
  if (error instanceof ApiError) {
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```

##### Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Key is not valid | `ApiError` |

## Common Code Documentation

### ApiResponse

An interface for the result of an API call.

#### Properties

| Name | Type | Description |
|  --- | --- | --- |
| request | HttpRequest | Original request that resulted in this response. |
| statusCode | number | Response status codee. |
| headers | Record<string, string> | Response headers. |
| result | T | Response data. |
| body | string \| Blob \| NodeJS.ReadableStream | Original body from the response. |

### ApiError

Thrown when the HTTP status code is not okay.

The ApiError extends the ApiResponse interface, so all ApiResponse properties are available.

#### Properties

| Name | Type | Description |
|  --- | --- | --- |
| request | HttpRequest | Original request that resulted in this response. |
| statusCode | number | Response status codee. |
| headers | Record<string, string> | Response headers. |
| result | T | Response data. |
| body | string \| Blob \| NodeJS.ReadableStream | Original body from the response. |

