We welcome contributions, but request that you follow these guidelines.

- [Style Guide](#style-guide)

### Style Guide
#### WebAgentFramework NSF
**DO NOT USE BINARY DXL EXPORT FROM DOMINO DESIGNER**
To check your setting:
1. Go to Preferences in Domino Designer (the relevant category does not show for Notes Client).
2. Go to Domino Designer > Source Control.
3. Ensure **_no_** check in "Use Binary DXL dfor source control operations". If you need this checked, manually copy code out of the database rather than synchronising to an On Disk Project.

For Agents and Script Libraries, ensure the Apache header is added to the Options section. 

If you are editing a design element for the first time, add your name to the copyright header.

Add comments to any Subs or Functions. Comments are not required for Property blocks.

Clean up LotusScript source code before submitting. Unfortunately there is not a formatter to enable this.
- Ensure code is indented with tabs to the right level.
- Use proper case for keywords (e.g. `If`, not `if`).
- Use proper case for in-built LotusScript methods (e.g. `ReplaceItemValue()`, not `replaceitemvalue()`). This aids translation to other languages.
- Wrap `if` statements in parentheses, as is expected by e.g. Java or JavaScript.

#### Testing

A Node-RED flow and dashboard is available for testing. This allows customisation for a specific server / database / authentication. Test should be run and updated for new functionality.

### Issues

Issues should be raised in the project on GitHub. Maintainers will not be proactively monitoring other forums. Check there is not already an issue raised. Remember the issue may have been closed as not to be fixed.

Please structure your issue report to make it as easy as possible to reproduce and diagnose. If possible, investigate and debug the source code to identify the location of the issue, including line numbers for the relevant script library (right-click in the gutter on the LotusScript editor to enable line numbers). A standalone tester agent will help reproduce issues.

At a minimum provide information about the server version, fix packs and hot fixes applied. 

An informative and well-structured issue report will increase the chances of a timely fix.

### Feature Requests

Feature requests can be raised in the project on GitHub. But they should aim to be as generic as possible.

### Pull Requests

Pull requests are encouraged. The project team will help those new to open source. Pull requests should only include contributions for a single feature request. They may contain multiple bug fixes, if they are small and related.

All contributors need to sign an [OpenNTF Contributor License Agreement](https://openntf.org/main.nsf/page.xsp?name=Get_Involved&subName=Project_Contributor) (ICLA or CCLA). The link gives details of how to complete the CLA. Also update the AUTHORS file. As part of the Pull Request review process, a committer will check to make sure a CLA has been signed.