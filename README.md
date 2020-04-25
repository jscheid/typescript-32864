This is a reproduction for https://github.com/microsoft/TypeScript/issues/32864

Run `yarn && yarn test` in this directory. It should output something
like the below (formatted for readability).

Tested with yarn v1.22.4 and node v10.16.0 and v12.16.1 on MacOS
10.14.6 (18G4032).

```
yarn run v1.22.4
$ tsserver < requests.json
Content-Length: 163

{
  "body": {
    "reason": "Creating possible configured project for input.ts to open",
    "projectName": "tsconfig.json"
  },
  "event": "projectLoadingStart",
  "type": "event",
  "seq": 0
}
Content-Length: 95

{
  "body": {
    "projectName": "tsconfig.json"
  },
  "event": "projectLoadingFinish",
  "type": "event",
  "seq": 0
}
Content-Length: 608

{
  "body": {
    "payload": {
      "version": "3.8.3",
      "languageServiceEnabled": true,
      "projectType": "configured",
      "configFileName": "tsconfig.json",
      "compileOnSave": false,
      "exclude": false,
      "include": false,
      "files": false,
      "extends": false,
      "typeAcquisition": {
        "exclude": false,
        "include": false,
        "enable": false
      },
      "compilerOptions": {
      },
      "fileStats": {
        "deferredSize": 0,
        "deferred": 0,
        "dtsSize": 1137433,
        "dts": 17,
        "tsxSize": 0,
        "tsx": 0,
        "tsSize": 48,
        "ts": 1,
        "jsxSize": 0,
        "jsx": 0,
        "jsSize": 0,
        "js": 0
      },
      "projectId": "b55cdbef4907b7045f32cc5360d48d262cca5f94062e353089f189f4460039e0"
    },
    "telemetryEventName": "projectInfo"
  },
  "event": "telemetry",
  "type": "event",
  "seq": 0
}
Content-Length: 130

{
  "body": {
    "diagnostics": [],
    "configFile": "tsconfig.json",
    "triggerFile": "input.ts"
  },
  "event": "configFileDiag",
  "type": "event",
  "seq": 0
}
Content-Length: 3130

{
  "message": "Error processing request. Cannot read property 'emitNode' of undefined
TypeError: Cannot read property 'emitNode' of undefined
    at Object.getStartsOnNewLine (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:71085:29)
    at shouldWriteSeparatingLineTerminator (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:95873:27)
    at emitNodeList (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:95658:29)
    at emitList (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:95555:13)
    at Object.writeList (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:92891:13)
    at /private/tmp/testproject/node_modules/typescript/lib/tsserver.js:119315:29
    at Object.mapToDisplayParts (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:107201:13)
    at itemInfoForParameters (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:119312:41)
    at getSignatureHelpItem (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:119278:95)
    at /private/tmp/testproject/node_modules/typescript/lib/tsserver.js:119251:79
    at Array.map (<anonymous>)
    at createSignatureHelpItems (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:119251:36)
    at /private/tmp/testproject/node_modules/typescript/lib/tsserver.js:118843:23
    at Object.runWithCancellationToken (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:34552:28)
    at Object.getSignatureHelpItems (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:118841:32)
    at Object.getSignatureHelpItems (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:135509:37)
    at IOSession.Session.getSignatureHelpItems (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:145510:62)
    at Session.handlers.ts.createMapFromTemplate._a.(anonymous function) (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:144404:61)
    at /private/tmp/testproject/node_modules/typescript/lib/tsserver.js:146003:88
    at IOSession.Session.executeWithRequestId (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:145994:28)
    at IOSession.Session.executeCommand (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:146003:33)
    at IOSession.Session.onMessage (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:146027:35)
    at Interface.<anonymous> (/private/tmp/testproject/node_modules/typescript/lib/tsserver.js:147342:27)
    at Interface.emit (events.js:198:13)
    at Interface._onLine (readline.js:308:10)
    at Interface._normalWrite (readline.js:451:12)
    at ReadStream.ondata (readline.js:165:10)
    at ReadStream.emit (events.js:198:13)
    at addChunk (_stream_readable.js:288:12)
    at readableAddChunk (_stream_readable.js:269:11)
    at ReadStream.Readable.push (_stream_readable.js:224:10)
    at lazyFs.read (internal/fs/streams.js:181:12)
    at FSReqWrap.wrapper [as oncomplete] (fs.js:467:17)",
  "success": false,
  "request_seq": "2",
  "command": "signatureHelp",
  "type": "response",
  "seq": 0
}
Content-Length: 76

{
  "body": {
    "pid": 61308
  },
  "event": "typingsInstallerPid",
  "type": "event",
  "seq": 0
}
✨  Done in 1.26s.

```
