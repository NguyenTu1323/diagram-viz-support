# System Architecture Diagram

This diagram shows a typical API request flow with caching and authentication.

```mermaid
graph TB
    Start([User Request]) --> Gateway[API Gateway]
    Gateway --> Auth{Authentication<br/>Valid?}

    Auth -->|Invalid| Error[Return 401<br/>Unauthorized]
    Auth -->|Valid| Router[Route Handler]

    Router --> Cache{Check<br/>Cache}
    Cache -->|Hit| Return[Return Cached<br/>Response]
    Cache -->|Miss| Service[Business Logic<br/>Service]

    Service --> DB[(Database)]
    DB --> Service
    Service --> UpdateCache[Update Cache]
    UpdateCache --> Return

    Return --> Response([Send Response<br/>to Client])
    Error --> Response

    style Start fill:#e1f5e1
    style Response fill:#e1f5e1
    style Auth fill:#fff4e1
    style Cache fill:#fff4e1
    style Error fill:#ffe1e1
    style DB fill:#e1e5ff
```

## How to View

1. **In VS Code**: Open this file and click the preview button (top-right icon) or use `Cmd+Shift+V`
2. **Export**: Use Mermaid CLI or copy to [mermaid.live](https://mermaid.live) for PNG/SVG export
