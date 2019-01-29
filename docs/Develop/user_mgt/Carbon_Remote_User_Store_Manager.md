# Carbon Remote User Store Manager

Carbon Remote User Store Manager is a way of using a user store that is
already configured in a WSO2 Carbon product. 

Consider a scenario where two instances of the WSO2 Identity Server are
configured. The first instance (IS1) has a
`ReadOnlyLDAPUserStoreManager` (configured on OpenLDAP) and the second
instance (IS2) has `JDBCUserStoreManager` configured on OracleDB. To
expose the users in IS2 to IS1 through the `UserStoreManager` API, you
can call the `UserStoreManager` admin service operations. WSO2 IS has a
standard implementation which uses the admin services. The diagram below
illustrates this scenario. 

![](attachments/92523656/92523657.png)

### Configuring a carbon remote user store manager** **

To configure a carbon remote user store manager, you can follow the
following steps. 

1.  Log in to the management console of the the local server (IS1) and
    click **User Stores&gt;Add** in the **Main** menu.

2.  Fill in the following values in the form as seen below. The image
    below shows a sample configuration.
    -   **User Store Manager
        Class:  **org.wso2.carbon.identity.user.store.remote.CarbonRemoteUserstoreManger 
    -   **Domain Name:** &lt;desired\_secondary\_userstore\_name&gt;
    -   **Remote Server Username:** &lt;remote\_admin\_login&gt;
    -   **Remote Server Password:** &lt;remote\_admin\_password&gt;
    -   **Remote Server URL(s):** https://:/services

        Make sure that you insert the same credentials used to invoke
        the admin services in the remote server and the same remote
        services URL. 

        ![](attachments/92523656/92523659.png){width="519"}

3.  Update other fields as required (description is give for each
    property) and click Add.

## Attachments:

![](images/icons/bullet_blue.gif){width="8" height="8"} [image2017-3-8
12:21:17.png](attachments/92523656/92523657.png) (image/png)  
![](images/icons/bullet_blue.gif){width="8" height="8"}
[IS\_CarbonRemoteUserStoreManager.png](attachments/92523656/92523658.png)
(image/png)  
![](images/icons/bullet_blue.gif){width="8" height="8"} [Screenshot from
2016-01-14 18:15:37.png](attachments/92523656/92523659.png)
(image/png)  
![](images/icons/bullet_blue.gif){width="8" height="8"} [Screenshot from
2016-01-14 18:13:00.png](attachments/92523656/92523660.png)
(image/png)  
![](images/icons/bullet_blue.gif){width="8" height="8"}
[add.png](attachments/92523656/92523661.png) (image/png)  
![](images/icons/bullet_blue.gif){width="8" height="8"} [Untitled
drawing (2).png](attachments/92523656/92523662.png) (image/png)  
