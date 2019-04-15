# ListTunnel {#concept_c33_vdw_vgb .concept}

You can call this operation to list the tunnels of a specified table.

## Request parameters {#section_wvt_xdw_vgb .section}

TableName: the name of the table that you want to list tunnels for.

## Response parameters {#section_fxx_zdw_vgb .section}

-   List<TunnelInfo\>: the list of required tunnels.
    -   TunnelId: the ID of a required tunnel.
    -   TunnelType: the type of the required tunnel. Valid values: BaseData, Stream, and BaseAndStream.
    -   TableName: the name of the table where the required tunnel is located.
    -   InstanceName: the name of the instance where the required tunnel is located.
    -   Stage: the stage where the required tunnel is located. Valid values: InitBaseDataAndStreamShard, ProcessBaseData, and ProcessStream.
    -   Expired: indicates whether data is expired. If a value of true is returned, request technical support.
-   ResponseInfo: some other fields returned in the request.

    RequestId: the GUID generated by Alibaba Cloud for the request.


## Example {#section_a3z_d2w_vgb .section}

```
private static void listTunnel(TunnelClient client, String tableName) {
    ListTunnelRequest request = new ListTunnelRequest(tableName);
    \ListTunnelResponse resp = client.listTunnel(request);
    System.out.println("RequestId: " + resp.getRequestId());
    for (TunnelInfo info : resp.getTunnelInfos()) {
        System.out.println("TunnelInfo::::::");
        System.out.println("\tTunnelName: " + info.getTunnelName());
        System.out.println("\tTunnelId: " + info.getTunnelId());
        // The type of the required tunnel. Valid values: BaseData, Stream, and BaseAndStream.
        System.out.println("\tTunnelType: " + info.getTunnelType());
        System.out.println("\tTableName: " + info.getTableName());
        System.out.println("\tInstanceName: " + info.getInstanceName());
        // The stage where the required tunnel is located. Valid values: InitBaseDataAndStreamShard, ProcessBaseData, and ProcessStream.
        System.out.println("\tStage: " + info.getStage());
        // Indicates whether data is expired. If a value of true is returned, request technical support.
        System.out.println("\tExpired: " + info.isExpired());
    }
}
```
