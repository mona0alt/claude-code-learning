# LSP Tool Prompt

## Overview

Interact with Language Server Protocol (LSP) servers for code intelligence features.

## Supported Operations

### Navigation
- **goToDefinition**: Find where a symbol is defined
- **goToImplementation**: Find implementations of an interface or abstract method
- **findReferences**: Find all references to a symbol

### Information
- **hover**: Get hover information (documentation, type info) for a symbol
- **documentSymbol**: Get all symbols (functions, classes, variables) in a document
- **workspaceSymbol**: Search for symbols across the entire workspace

### Call Hierarchy
- **prepareCallHierarchy**: Get call hierarchy item at a position
- **incomingCalls**: Find functions/methods that call the function at a position
- **outgoingCalls**: Find functions/methods called by the function at a position

## Parameters

All operations require:
- **filePath**: The file to operate on
- **line**: Line number (1-based, as shown in editors)
- **character**: Character offset (1-based, as shown in editors)

## Note

LSP servers must be configured for the file type. If no server is available, an error will be returned.
