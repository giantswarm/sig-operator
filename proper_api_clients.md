# Proper API Clients

When leveraging third party tools or any kind of service, we should operate
against their APIs using proper, programmatic API client libraries. We should
not shell out against compiled binaries. This breaks a reliable API integration.
Management and error handling is always hard. There is usually no tooling to
help the development and maintenance. For instance compiler support is usually
missing and breaking APIs are only discovered by malfunctions during runtime.
