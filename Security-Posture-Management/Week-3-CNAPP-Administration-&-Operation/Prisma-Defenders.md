
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Author                            | Modification Date       | Changes                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
|                 | 25/02/2025              | First Version Created                         |

<br>

---

Defenders enforce the policies you set in the prisma cloud console.

Specific types of assets require specific defender types to protect them to fully support for automated workflows.

## Defender types

- Container Defender (Linux and Windows)
- Host Defender (Linux and Windows)
- Orchestrator Defenders (Kubernetes)
- Serverless Defender
- App-Embedded Defender
- Tanzu Application Service Defender

## When to use each type of defender?

![alt text](https://docs.prismacloud.io/docs/en/classic/compute-admin-guide/install/deploy-defender/media_16b6cebd6af0a387fc3c96a187a471010e80aab54.png?width=650&format=webply&optimize=medium)

## Serverless Defender

Serverless Defenders offer runtime protection for AWS Lambda functions and Azure Functions . Serverless Defender must be embedded inside your functions. Deploy one Serverless Defender per function.

Serverless Defender protects serverless functions at runtime. It monitors your functions to ensure they execute as designed.

Per-function policies let you control:

- Process activity. Enables verification of launched subprocesses against policy.
- Network connections. Enables verification of inbound and outbound connections, and permits outbound connections to explicitly allowed domains.
- File system activity. Controls which parts of the file system functions can access.

### Requirements

#### AWS Lambda

- **OS**: Linux
- **Supported runtimes**:
  - C# (.NET Core) 6.0
  - Java 8, 11
  - Node.js 14.x, 16.x, 18.x
  - Python 3.6, 3.7, 3.8, 3.9
  - Ruby 2.7

> Not supported on ARM64 architecture.

## Steps to deploy Serverless defender

To secure a serverless function the steps are:

1. (Optional) If you are not using a deployment framework like SAM or Serverless Framework, download a ZIP file that contains your function source code and dependencies.
1. Embed the Serverless Defender into the function.
1. Deploy the new function or upload the updated ZIP file to the cloud provider.
1. Define a serverless protection runtime policy.
1. Define a serverless WAAS policy.

### AWS LAMBDA - Embed serverless defender into Python functions

Import the Serverless Defender module, and configure your function to start it.

Steps:

1. Open Compute Console, and go to Manage > Defenders > Defenders: Deployed > Manual deploy > Single Defender.
1. The DNS name Serverless Defender uses to connect to your Compute Console is prepopulated for you.
1. In Choose Defender type, select Serverless.
1. In Runtime, select Node.js.
1. Download the Serverless Defender package to your workstation.
1. Unzip the Serverless Defender bundle into your working directory.
1. Embed the serverless Defender into the function by importing the Prisma Cloud library and wrapping the function’s handler.
    - For asynchronous handlers:

    ```js
    // Async handler
    var twistlock = require('./twistlock');
    exports.handler = async (event, context) => {
    .
    .
    .
    };
    exports.handler = twistlock.asyncHandler(exports.handler);
    ```

    - For synchronous handlers:

    ```js
    // Non-async handler
    var twistlock = require('./twistlock');
    exports.handler = (event, context, callback) => {
    .
    .
    .
    };
    exports.handler = twistlock.handler(exports.handler);    
    ```

1. Generate the value for the TW_POLICY environment variable by specifying your function’s name and region.

    If Any is selected for region, only policies that contain * in the region label will be matched.

    Serverless Defender uses TW_POLICY to determine how to connect to Compute Console to retrieve policy and send audits.

    Copy the value generated for TW_POLICY, and set it aside.

1. AWS Lambda - Upload the protected function

    Prisma Cloud Serverless Defender includes native node.js libraries. If you are using webpack, please refer to tools such as native-addon-loader to make sure these libraries are included in the function ZIP file.

# References

- Defender Types <https://docs.prismacloud.io/en/classic/compute-admin-guide/install/deploy-defender/defender-types>
- Serverless Defender <https://docs.prismacloud.io/en/classic/compute-admin-guide/install/deploy-defender/serverless/serverless#embed-serverless-defender-into-nodejs-functions>
