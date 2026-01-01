# Speckit Command Flow

Below is a Mermaid diagram that illustrates the flow of Speckit commands:

```mermaid
graph TD
    A[Start] --> B[Initialize Speckit]
    B --> C[Create a New Spec]
    C --> D[Edit Spec File]
    D --> E[Validate Spec]
    E --> F{Validation Successful?}
    F -->|Yes| G[Commit Changes]
    F -->|No| H[Fix Errors]
    H --> D
    G --> I[Push to Remote Repository]
    I --> J[End]
```

This diagram provides a high-level overview of the typical workflow when using Speckit commands. For more details, refer to the [Speckit Documentation](https://github.com/schalkje/devman/blob/main/speckit/speckit.md).