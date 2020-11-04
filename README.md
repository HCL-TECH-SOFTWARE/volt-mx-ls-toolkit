## Volt MX LotusScript Toolkit

This repository contains an NSF which comprises a LotusScript toolkit (i.e. set of LotusScript libraries) providing a framework for integrating with Volt MX. There are multiple script libraries because error line numbers are changed if there is more than one class in each script library. 

### Script Libraries
The script libraries are:

- **OpenLogFunctions**: part of Julian Robichaux's excellent [OpenLog](https://openntf.org/main.nsf/project.xsp?r=project/OpenLog) application. The library is included to enable LotusScript compilation.
- **NotesHttpConstants**: contains constants used within the other script libraries.
- **FluentNotesJson**: contains wrappers for NotesJson classes, providing fluent methods to allow e.g. `.appendElementFluent("World", "Hello").appendArray("names").appendElementFluent("John Doe").appendElementFluent("Jane Doe")`.
- **NotesHttpRequestHelper**: helper class for receiving and processing HTTP calls to Domino agents.
- **NotesHttpJsonRequestHelper**: helper class for receiving and processing HTTP calls to Domino agents *which receive and return JSON*.
- **FoundryHttpHelper**: helper class for receiving and processing HTTP calls to Domino agents which receive and return JSON according to the Volt MX schema.

The Volt MX schema expected is:
```json
{
    "unid": "36EBDFD11D4381F280258600003ED607",
    "dbPath": "extlib/xpagesext.nsf",
    "payload": {
        "FirstName": "Adrian",
        "TestVal": "20",
        "TestBoolean": false
    },
    "returnFields": [
        "FirstName",
        "LastName",
        "City",
        "State",
        "Email"
    ]
}
```

- **unid** allows you to define a document on which to act.
- **dbPath** allows you to specify that the document should be retrieved from a database other than the one containing this code.
- **payload** is a set of fields and values to apply to the document.
- **returnItems** is a set of fields to return.

### Sample Agents
There are two sample agents that can be called from Postman or Node-RED, TestAgent and TestFoundryAgent.

- **TestAgent** demonstrates methods for extracting content from header and query parameters, as well as the payload. It also demonstrates the fluent methods for building the response. There are also method calls for building error responses.
- **TestVoltMXAgent** demonstrates using the FoundryHttpHelper for the minimum calls for validating this is a call from the web, validating the existence of the document to act upon, updating all fields based on the payload, saving it and returning the requested fields.

### Async Agent Processing

**RunAgentAsync** is an agent endpoint that's designed to allow you to run agents asynchronously from the web. The process creates a process document based on the payload, which should comprise:

- **dbPath**: the database path containing the agent to trigger.
- **agentName**: the name of the agent to trigger. This doesn't have to include parentheses if the agent is set to run on agent list selection.
- **callbackUrl**: the URL to call on completion of the agent.
- **method**: the HTTP method to use for the callback, e.g. "POST".
- **unid**: the UNID of the document to act upon.
- **payload**: a set of fields and values to apply to the document.

The **ProcessAsyncRequests** agent picks up any documents at "Pending" status and triggers the relevant agent. Your agent should use the values in the document and send an HTTP request back to the callback URL.