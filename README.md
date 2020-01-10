Dependencies
- VirtualBox VM "MSEdge on Win10 (x64) Stable 1809" - https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/
- .NET Core SDK 3.1.100 
- Node.js 12.14.1
- NPM 6.13.4
- Git 2.24.1.2

Repro Steps:
1. Either clone this repo and cd into it or run `dotnet new angular --no-https`
2. In a PowerShell terminal, run the following commands:
    ```
    PS> cd .\ClientApp\
    PS> npm install
    PS> cd ..
    PS> dotnet publish -c Release
    PS> .\bin\Release\netcoreapp3.1\publish\DotNetSpaFailure.exe
    ```
3. In another PowerShell terminal, run the following command:
    ```
    PS> iwr -Method POST http://localhost:5000/api/thisendpointdoesntexist
    ```

Expected result:
- App returns a 404

Actual Result:
- App returns a 500

NPM Install Output:
```
PS C:\Users\IEUser\DotNetSpaFailure\ClientApp> npm install

> node-sass@4.13.0 install C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\node-sass
> node scripts/install.js

Downloading binary from https://github.com/sass/node-sass/releases/download/v4.13.0/win32-x64-72_binding.node
Download complete .] - :
Binary saved to C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\node-sass\vendor\win32-x64-72\binding.node
Caching binary to C:\Users\IEUser\AppData\Roaming\npm-cache\node-sass\4.13.0\win32-x64-72_binding.node

> core-js@3.2.1 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\@angular-devkit\build-angular\node_modules\core-js
> node scripts/postinstall || echo "ignore"

Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!

The project needs your help! Please consider supporting of core-js on Open Collective or Patreon:
> https://opencollective.com/core-js
> https://www.patreon.com/zloirock

Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)


> core-js@2.6.10 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\babel-runtime\node_modules\core-js
> node postinstall || echo "ignore"

Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!

The project needs your help! Please consider supporting of core-js on Open Collective or Patreon:
> https://opencollective.com/core-js
> https://www.patreon.com/zloirock

Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)


> core-js@2.6.10 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\oidc-client\node_modules\core-js
> node postinstall || echo "ignore"


> @angular/cli@8.3.14 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\@angular\cli
> node ./bin/postinstall/script.js

? Would you like to share anonymous usage data with the Angular Team at Google under
Google’s Privacy Policy at https://policies.google.com/privacy? For more details and
how to change this setting, see http://angular.io/analytics. No

> core-js@3.3.5 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\core-js
> node postinstall || echo "ignore"


> node-sass@4.13.0 postinstall C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\node-sass
> node scripts/build.js

Binary found at C:\Users\IEUser\DotNetSpaFailure\ClientApp\node_modules\node-sass\vendor\win32-x64-72\binding.node
Testing binary
Binary is fine
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\webpack-dev-server\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\watchpack\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\@angular\compiler-cli\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.1 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.1: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

added 1332 packages from 1113 contributors and audited 17096 packages in 340.833s
found 8 vulnerabilities (3 moderate, 5 high)
  run `npm audit fix` to fix them, or `npm audit` for details
```

Dotnet Publish Output:
```
PS C:\Users\IEUser\DotNetSpaFailure> dotnet publish -c Release

Welcome to .NET Core 3.1!
---------------------
SDK Version: 3.1.100

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry

----------------
Explore documentation: https://aka.ms/dotnet-docs
Report issues and find source on GitHub: https://github.com/dotnet/core
Find out what's new: https://aka.ms/dotnet-whats-new
Learn about the installed HTTPS developer cert: https://aka.ms/aspnet-core-https
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs
Write your first app: https://aka.ms/first-net-core-app
--------------------------------------------------------------------------------------
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 5.27 sec for C:\Users\IEUser\DotNetSpaFailure\DotNetSpaFailure.csproj.
  DotNetSpaFailure -> C:\Users\IEUser\DotNetSpaFailure\bin\Release\netcoreapp3.1\DotNetSpaFailure.dll
  DotNetSpaFailure -> C:\Users\IEUser\DotNetSpaFailure\bin\Release\netcoreapp3.1\DotNetSpaFailure.Views.dll
  audited 17096 packages in 32.829s
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\webpack-dev-server\node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\watchpack\node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.1 (node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.1: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\@angular\compiler-cli\node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

  found 8 vulnerabilities (3 moderate, 5 high)
    run `npm audit fix` to fix them, or `npm audit` for details

  > dotnetspafailure@0.0.0 build C:\Users\IEUser\DotNetSpaFailure\ClientApp
  > ng build "--prod"

  Browserslist: caniuse-lite is outdated. Please run next command `npm update`
  Generating ES5 bundles for differential loading...
  ES5 bundle generation complete.

  chunk {0} runtime-es2015.e8a2810b3b08d6a1b6aa.js (runtime) 1.45 kB [entry] [rendered]
  chunk {0} runtime-es5.e8a2810b3b08d6a1b6aa.js (runtime) 1.45 kB [entry] [rendered]
  chunk {1} main-es2015.fb1739147b186a90d829.js (main) 246 kB [initial] [rendered]
  chunk {1} main-es5.fb1739147b186a90d829.js (main) 282 kB [initial] [rendered]
  chunk {2} polyfills-es2015.0ef207fb7b4761464817.js (polyfills) 36.4 kB [initial] [rendered]
  chunk {3} polyfills-es5.bc6aeefaf1fbb26509d2.js (polyfills-es5) 122 kB [initial] [rendered]
  chunk {4} styles.bee5835e3fdc14721d9a.css (styles) 138 kB [initial] [rendered]
  Date: 2020-01-10T19:41:19.473Z - Hash: 4f45adf8e3b21fdee013 - Time: 145638ms
  DotNetSpaFailure -> C:\Users\IEUser\DotNetSpaFailure\bin\Release\netcoreapp3.1\publish\
```

App Error Output:
```
PS C:\Users\IEUser\DotNetSpaFailure> .\bin\Release\netcoreapp3.1\publish\DotNetSpaFailure.exe
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: http://localhost:5000
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
      Content root path: C:\Users\IEUser\DotNetSpaFailure
fail: Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware[1]
      An unhandled exception has occurred while executing the request.
System.InvalidOperationException: The SPA default page middleware could not return the default page '/index.html' because it was not found, and no other middleware handled the request.
Your application is running in Production mode, so make sure it has been published, or that you have built your SPA manually. Alternatively you may wish to switch to the Development environment.

   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__1(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_2.<Use>b__2()
   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__0(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.Routing.EndpointMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.Routing.EndpointRoutingMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware.Invoke(HttpContext context)
fail: Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware[3]
      An exception was thrown attempting to execute the error handler.
System.InvalidOperationException: The SPA default page middleware could not return the default page '/index.html' because it was not found, and no other middleware handled the request.
Your application is running in Production mode, so make sure it has been published, or that you have built your SPA manually. Alternatively you may wish to switch to the Development environment.

   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__1(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_2.<Use>b__2()
   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__0(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.Routing.EndpointMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.Routing.EndpointRoutingMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware.HandleException(HttpContext context, ExceptionDispatchInfo edi)
fail: Microsoft.AspNetCore.Server.Kestrel[13]
      Connection id "0HLSM0OO9AMHO", Request id "0HLSM0OO9AMHO:00000001": An unhandled exception was thrown by the application.
System.InvalidOperationException: The SPA default page middleware could not return the default page '/index.html' because it was not found, and no other middleware handled the request.
Your application is running in Production mode, so make sure it has been published, or that you have built your SPA manually. Alternatively you may wish to switch to the Development environment.

   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__1(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_2.<Use>b__2()
   at Microsoft.AspNetCore.SpaServices.SpaDefaultPageMiddleware.<>c__DisplayClass0_0.<Attach>b__0(HttpContext context, Func`1 next)
   at Microsoft.AspNetCore.Builder.UseExtensions.<>c__DisplayClass0_1.<Use>b__1(HttpContext context)
   at Microsoft.AspNetCore.Routing.EndpointMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.Routing.EndpointRoutingMiddleware.Invoke(HttpContext httpContext)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.StaticFiles.StaticFileMiddleware.Invoke(HttpContext context)
   at Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware.Invoke(HttpContext context)
--- End of stack trace from previous location where exception was thrown ---
   at Microsoft.AspNetCore.Diagnostics.ExceptionHandlerMiddleware.HandleException(HttpContext context, ExceptionDispatchInfo edi)
   at Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http.HttpProtocol.ProcessRequests[TContext](IHttpApplication`1 application)

```

Invoke-Webrequest Error Output:
```
PS C:\Users\IEUser> iwr -Method POST http://localhost:5000/api/thisendpointdoesntexist
iwr : The remote server returned an error: (500) Internal Server Error.
At line:1 char:1
+ iwr -Method POST http://localhost:5000/api/thisendpointdoesntexist
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (System.Net.HttpWebRequest:HttpWebRequest) [Invoke-WebRequest], WebExc
   eption
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand

```