# Changelog

## 2.4.1

- Fix PartValue cast

## 2.4.0

- Deprecate `@FileField`, use `@PartFile` instead
- support `chopper: ^2.4.1`

## 2.3.4

  fix trailing slash when empty path
	
## 2.3.3

- update analyzer to `0.35.0`

## 2.3.2

- do not set to null explicitly

## 2.3.1

- Fixed @Path issue, thanks to @kiruto
- update `built_collection` to `4.0.0`

## 2.3.0

- ***Breaking Change***
  `ChopperClient.errorConverter` is now taking an `ErrorConverter` as a parameter
  ```dart
  abstract class ErrorConverter {
    FutureOr<Response> convertError<ResultType, ItemType>(Response response);
  }
  ```
- Remove deprecated `Chopper.service<Type>(Type)`
- Add `QueryMap` annotation
- Fix https://github.com/lejard-h/chopper/issues/28
- Fix https://github.com/lejard-h/chopper/issues/21
- Fix https://github.com/lejard-h/chopper/issues/37

## 2.2.0

- Fix converter issue on List
  - ***Breaking Change*** 
  on `Converter.convertResponse<ResultType>(response)`, 
  it take a new generic type => `Converter.convertResponse<ResultType, ItemType>(response)`
                 
- deprecated `Chopper.service<Type>(Type)`, use `Chopper.getservice<Type>()` instead
thanks to @MichaelDark

## 2.1.0

- fix casting issue

## 2.0.0

- Request is now containing baseUrl
- Can call `Request.toHttpRequest()` direclty to get the `http.BaseRequest` will receive
- If a full url is specified in the `path` (ex: @Get(path: 'https://...')), it won't be concaten with the baseUrl of the ChopperClient and the ChopperAPI
- Add `CurlInterceptor` thanks @edwardaux
- Add `HttpLoggingInterceptor`
- Add `FactoryConverter` annotation `@FactoryConverter(request: convertRequest, response: convertResponse)`

- ***BreakingChange***
  - Method.url renamed to path
  - `Converter.encode` and `Converter.decode` removed, implement `Converter.convertResponse` and Converter.convertRequest` instead
  - `ChopperClient.jsonApi` deprecated, use a `JsonConverter` instead
  - `ChopperClient.formUrlEncodedApi`, use `FormUrlEncodedConverter` instead
  - remove `JsonEncoded` annotation, use `FactoryConverter` instead

## 1.1.0

- ***BreakingChange***
    Removed `name` parameter on `ChopperApi`
    New way to instanciate a service
        ```dart
            @ChopperApi()
            abstract class MyService extends ChopperService {
                static MyService create([ChopperClient client]) => _$MyService(client);
            }
        ```

## 1.0.1

- update build package

## 1.0.0

- Multipart request
- form url encoded
- add jsonAPI and formUrlEncodedApi boolean to ChopperClient
- json and formUrlEncoding are now builtin
- `onError`, `onResponse`, `onRequest` stream
- error converter
- add withClient constructor

## 0.1.0

- update dart sdk

## 0.0.2

- the generated extension is now `*.chopper.dart`

- rename `ServiceDefinition` to `ChopperApi`
- rename `ChopperClient.services` field to `ChopperClient.apis`

## 0.0.1

- Initial version, created by Stagehand
