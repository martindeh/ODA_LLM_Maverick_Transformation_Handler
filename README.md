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
- Supports OCI-native request customization in the transformation handler.

## Prerequisites

- Oracle Digital Assistant instance with access to custom LLM Transformation components.
- General familiarity with ODA skills, Visual Flow Designer, LLM Integration, and the Invoke Large Language Model component.
- OCI tenancy and compartment authorized to use Generative AI.
- OCI request-signing authentication configured in the ODA LLM API service.
- Access to Meta Llama 4 Maverick in a supported OCI region or through a dedicated endpoint.

Do not include OCI signing keys, tokens, or other credentials in the handler source.
Configure OCI request-signing authentication through the ODA LLM service configuration.

## Installation

1. Download zip of this repository.
2. Unzip the repository.
3. Unzip the `ODA_OCI_Maverick_Integration_Guide_HTML_Bundle` included with the repository.
4. Review the `ODA_OCI_Maverick_Integration_Guide.html` for detailed instructions.
5. Follow the guide to create the instance-level OCI LLM API service, custom LLM Transformation Handler, skill-level LLM service, and Invoke LLM configuration.


## Documentation

The complete ODA_OCI_Maverick_Integration_Guide.html implementation guide covers prerequisites, API service setup,
handler deployment, streaming, multi-turn behavior, troubleshooting, and local
debugging.

For Oracle Digital Assistant product documentation, see:

- [Create, Configure, and Version Skills](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/create-configure-version-skills.html)
- [Visual Flow Designer](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/visual-flow-designer.html)
- [LLM Integration](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/llm-blocks-skills.html)
- [LLM Services](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/llm-services.html)
- [LLM Transformation Handlers and CLMI](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/llm-transformation-handlers.html)
- [Invoke Large Language Model Component](https://docs.oracle.com/en/cloud/paas/digital-assistant/use-chatbot/invoke-large-language-model-component.html)

For provider documentation, see [OCI Meta Llama 4 Maverick](https://docs.oracle.com/en-us/iaas/Content/generative-ai/meta-llama-4-maverick.htm).

## Examples

The repository contains the complete handler and separate transformation methods:

- `ociMaverickLLMTransformationHandler.js` — complete, commented reference handler.
- `transformRequestPayload.js` — request transformation method.
- `transformResponsePayload.js` — response transformation method.
- `transformErrorResponsePayload.js` — error transformation method.

The guide includes representative OCI native Chat request payloads and
validation steps for:

- Non-streaming responses
- Streaming responses
- Multi-turn conversations
- CLMI-to-OCI request transformation
- OCI-to-CLMI response and error transformation

The individual method files contain the method code without the detailed comments.
When copying an individual method into the ODA-generated handler stub, review the
complete handler because the method may depend on constants or helper functions
defined elsewhere in the handler. For example, `transformRequestPayload()` uses
the `MODEL_ID` constant and the `toOciMessage()` helper defined in the complete
handler.

The complete handler also contains the detailed implementation comments and the
supporting code needed to understand the full reference implementation.

## Help

For ODA configuration and product usage, consult the Oracle Digital Assistant
documentation referenced in the integration guide.

For OCI Generative AI and Meta Llama 4 Maverick questions, consult the
[OCI Meta Llama 4 Maverick documentation](https://docs.oracle.com/en-us/iaas/Content/generative-ai/meta-llama-4-maverick.htm).

For issues with this sample implementation, open an issue in this repository
and include the ODA/OCI error message, sanitized request and response payloads,
and whether streaming is enabled.

## Contributing

*If your project has specific contribution requirements, update the CONTRIBUTING.md file to ensure those requirements are clearly explained*

This project welcomes contributions from the community. Before submitting a pull request, please [review our contribution guide](./CONTRIBUTING.md)

## Security

Please consult the [security guide](./SECURITY.md) for our responsible security vulnerability disclosure process

Do not commit OCI signing keys, tokens, credentials, or other secrets to this repository.
Review diagnostic logging before using the sample in production, particularly if
prompts or model responses may contain sensitive information.

## License

*The correct copyright notice format for both documentation and software is*
    "Copyright (c) [year,] year Oracle and/or its affiliates."
*You must include the year the content was first released (on any platform) and the most recent year in which it was revised*

Copyright (c) 2026 Oracle and/or its affiliates.

*Replace this statement if your project is not licensed under the UPL*

Released under the Universal Permissive License v1.0 as shown at
<https://oss.oracle.com/licenses/upl/>.
