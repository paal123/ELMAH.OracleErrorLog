# OracleErrorLog

[![NuGet][nuget-badge]][nuget-pkg]

An ELMAH `ErrorLog` implementation that uses an Oracle database as the storage. The `ErrorLog` supports both managed and unmanaged drivers, as well as System.Data.OracleClient.

To use the OracleErrorLog for Oracle Managed Driver, add the following in your web.config:
```xml
  <system.data>
    <DbProviderFactories>
      <remove invariant="Oracle.ManagedDataAccess.Client" />
      <add name="ODP.NET, Managed Driver" invariant="Oracle.ManagedDataAccess.Client" type="Oracle.ManagedDataAccess.Client.OracleClientFactory, Oracle.ManagedDataAccess, Version=4.122.1.0, Culture=neutral, PublicKeyToken=89b483f429c47342" />
    </DbProviderFactories>
  </system.data>
  <elmah>
    <errorLog type="Elmah.OracleErrorLog, Elmah.Oracle" connectionStringName="elmah-connection"/>
  </elmah>
  <connectionStrings>
    <add name="elmah-connection" connectionString="<your connection string>" providerName="Oracle.ManagedDataAccess.Client"/>
  </connectionStrings>
```
*NOTE:* The following providers are supported:
* Oracle.ManagedDataAccess.Client (Requires Oracle.ManagedDataAccess)
* Oracle.DataAccess.Client (Requires ODP.Net installed)
* System.Data.OracleClient (Requires Oracle client installed)

[nuget-badge]: https://img.shields.io/nuget/v/elmah.oracle.svg
[nuget-pkg]: https://www.nuget.org/packages/elmah.oracle
