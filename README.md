# HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-ActiveSync-Devices-Delete

| :information_source: Information                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This repository contains the connector and configuration code only. The implementer is responsible for acquiring the connection details such as username, password, certificate, etc. You might even need to sign a contract or agreement with the supplier before implementing this connector. Please contact the client's application manager to coordinate the connector requirements. |

## Description

_HelloID-Conn-SA-Full-Exchange-On-Premises-Usermailbox-ActiveSync-Devices-Delete_ is a template designed for use with HelloID Service Automation (SA) Delegated Forms. It can be imported into HelloID and customized according to your requirements.

By using this delegated form, you can manage ActiveSync devices for user mailboxes in Exchange On-Premises. The following options are available:

1.  Search for a mailbox by entering a search term (Name, SamAccountName, Alias, or PrimarySmtpAddress)
2.  Select the target mailbox from the search results
3.  View all registered ActiveSync devices for the selected mailbox
4.  Select one or multiple devices to delete
5.  The selected devices are removed from Exchange On-Premises
6.  Audit logs are generated for all operations

## Getting started

### Requirements

- **Exchange On-Premises Environment**:<br>
  Access to an Exchange On-Premises environment is required. The connector uses PowerShell remoting to connect to Exchange servers.
- **Service Account**:<br>
  A service account with sufficient permissions to manage ActiveSync devices in Exchange On-Premises is required. The account must have the necessary rights to execute `Get-Mailbox`, `Get-MobileDevice`, and `Remove-ActiveSyncDevice` cmdlets.
- **Network Connectivity**:<br>
  The HelloID agent or server must have network connectivity to the Exchange server specified in the ConnectionUri. Ensure firewall rules allow PowerShell remoting traffic.
- **PowerShell Remoting**:<br>
  PowerShell remoting must be enabled on the Exchange server. The connector uses remote PowerShell sessions to execute Exchange cmdlets.

### Connection settings

The following user-defined variables are used by the connector.

| Setting               | Description                                                                              | Mandatory |
| --------------------- | ---------------------------------------------------------------------------------------- | --------- |
| ExchangeConnectionUri | The URI to connect to Exchange On-Premises (e.g., http://server.domain.local/PowerShell) | Yes       |
| ExchangeAdminUsername | The username of the service account with Exchange management permissions                 | Yes       |
| ExchangeAdminPassword | The password of the service account                                                      | Yes       |

## Remarks

### Authentication Method

The connector uses Default authentication for PowerShell remoting. Depending on your Exchange configuration, you may need to adjust the authentication method in the datasource and task scripts. Common alternatives include:

- **Default**: Uses the authentication method determined by the WS-Management protocol
- **Kerberos**: Requires proper Kerberos configuration and may require additional setup
- **Basic**: Requires Basic authentication to be enabled on the Exchange server

### Session Options

The connector uses secure session options with certificate validation enabled (`SkipCACheck`, `SkipCNCheck`, and `SkipRevocationCheck` set to `false`). If you encounter SSL/TLS certificate issues in your environment:

- Ensure valid SSL certificates are installed on your Exchange servers
- Alternatively, you can set these options to `true` in the datasource and task scripts, though this is not recommended for production environments

### ActiveSync Device Identity

The connector uses the `Identity.ObjectGuid` property from the `Get-MobileDevice` cmdlet results to uniquely identify devices. This ensures accurate device deletion even when multiple devices have similar friendly names.

### Wildcard Search

The mailbox search datasource supports wildcard searching across multiple fields (Name, SamAccountName, Alias, PrimarySmtpAddress). The search automatically adds wildcards around the search term for flexible matching.

## Development resources

### API endpoints

The following Exchange cmdlets are used by the connector:

| Cmdlet                  | Description                                            |
| ----------------------- | ------------------------------------------------------ |
| Get-Mailbox             | Retrieves mailbox information based on filter criteria |
| Get-MobileDevice        | Retrieves ActiveSync device information for a mailbox  |
| Remove-ActiveSyncDevice | Removes an ActiveSync device from Exchange             |

### API documentation

- [Connect to Exchange servers using remote PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-servers-using-remote-powershell)
- [Get-Mailbox cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailbox)
- [Get-MobileDevice cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mobiledevice)
- [Remove-ActiveSyncDevice cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/remove-activesyncdevice)

## Getting help

> :bulb: **Tip:**  
> _For more information on Delegated Forms, please refer to our [documentation](https://docs.helloid.com/en/service-automation/delegated-forms.html) pages_.

## HelloID docs

The official HelloID documentation can be found at: https://docs.helloid.com/
