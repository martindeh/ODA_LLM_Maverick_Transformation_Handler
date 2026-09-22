*This repository acts as a template for all of Oracle’s GitHub repositories. It contains information about the guidelines for those repositories. All files and sections contained in this template are mandatory, and a GitHub app ensures alignment with these guidelines. To get started with a new repository, replace the italic paragraphs with the respective text for your project.*

# OCI Meta Llama 4 Maverick Transformation Handler for Oracle Digital Assistant

A sample Oracle Digital Assistant (ODA) LLM Transformation Handler for invoking
OCI Generative AI Meta Llama 4 Maverick through OCI’s native Chat API.

The handler transforms ODA Common LLM Interface (CLMI) requests into OCI native
`/20231130/actions/chat` requests, and translates non-streaming and streaming
OCI responses back into CLMI.

## Features

- Supports OCI Meta Llama 4 Maverick through OCI’s native Generative AI Chat API.
- Transforms CLMI messages, output-token limits, and streaming settings.
- Supports non-streaming, streaming, and multi-turn conversations.
- Maps OCI native errors to ODA CLMI error responses.
- Includes optional payload logging for local debugging.

## Prerequisites

- Oracle Digital Assistant instance with access to custom LLM Transformation components.
- OCI tenancy and compartment authorized to use Generative AI.
- OCI request-signing authentication configured in the ODA LLM API service.
- Access to Meta Llama 4 Maverick in a supported OCI region or through a dedicated endpoint.

Do not include OCI signing keys, tokens, or other credentials in the handler source.

## Installation

1. Download or clone this repository.
2. In ODA, create an LLM Transformation component named
   `ociMaverickLLMTransformationHandler`.
3. Use the **Other → Custom** template.
4. Copy the implementation from
   [`ociMaverickLLMTransformationHandler.js`](./ociMaverickLLMTransformationHandler.js)
   into the generated handler.
5. Create an instance-level OCI LLM API service using:

   `POST https://inference.generativeai.<region>.oci.oraclecloud.com/20231130/actions/chat`

6. Configure OCI request-signing authentication and bind the API service to the
   transformation handler through a skill-level LLM service.

## Documentation

The complete implementation guide covers prerequisites, API service setup,
handler deployment, streaming, multi-turn behavior, troubleshooting, and local
debugging.


## Examples

The guide includes representative OCI native Chat request payloads and
validation steps for:

- Non-streaming responses
- Streaming responses
- Multi-turn conversations
- CLMI-to-OCI request transformation
- OCI-to-CLMI response and error transformation

## Help

For ODA configuration and product usage, consult the Oracle Digital Assistant
documentation referenced in the integration guide.

For issues with this sample implementation, open an issue in this repository
and include the ODA/OCI error message, sanitized request and response payloads,
and whether streaming is enabled.

## Contributing

*If your project has specific contribution requirements, update the CONTRIBUTING.md file to ensure those requirements are clearly explained*

This project welcomes contributions from the community. Before submitting a pull request, please [review our contribution guide](./CONTRIBUTING.md)

## Security

Please consult the [security guide](./SECURITY.md) for our responsible security vulnerability disclosure process

## License

*The correct copyright notice format for both documentation and software is*
    "Copyright (c) [year,] year Oracle and/or its affiliates."
*You must include the year the content was first released (on any platform) and the most recent year in which it was revised*

Copyright (c) 2026 Oracle and/or its affiliates.

*Replace this statement if your project is not licensed under the UPL*

Released under the Universal Permissive License v1.0 as shown at
<https://oss.oracle.com/licenses/upl/>.
