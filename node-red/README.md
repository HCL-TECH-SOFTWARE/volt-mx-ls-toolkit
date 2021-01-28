## Node-RED

The Node-RED flow in flows.json showcases the functionality of Volt MX LotusScript Toolkit. You will need:
- WebAgentFramework database, an NSF generated from the On Disk Project in the `notes` folder of this repo.
- A copy of the XPages Extension Library.
- Two agents added to the XPages Extension Library database, "UpdateContactsAndThreadsBE" and "EchoDoc", in this folder.

The Node-RED dashboard walks you through the configuration that is needed. Pay special notice to the requirement to end host URLs with a forward slash.

The Node-RED console and debug panel can be used to review any errors in using the dashboard. The most common one is configuration errors.