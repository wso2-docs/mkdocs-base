
# Using WSO2 In-Place Updates

The **WSO2 in-place updates** tool allows you to update your currently
used product by fetching updates from the server and merging all
configurations and files. The tool also gives backup and restore
capability.

Given below is how to get in-place updates to your product.
>
!!! note "Before you begin"
        -   Make sure you are already using a [WSO2
            product](https://wso2.com/platform). (Let's call this
            `<PRODUCT_HOME>`).
	-   Make sure you have an active Internet connection.
	-   Get a valid [WSO2 subscription](https://wso2.com/subscription).
	-   Do you have a proxy server/firewall? If so, grant access to the
            endpoints mentioned below.
??? note "Click to expand"
	   WUM gets updates by connecting to the `https://api.updates.wso2.com`
            and `https://cdn.updates.wso2.com` endpoints in the WSO2 Update
            service. If your system connects to the Update service through
            a proxy server/firewall, grant access to these endpoints.  
            Since WUM is a command-line tool, the proxy should be configured
            from your command-line as follows: 
            ```
            export http_proxy=http://username:password@proxyhost:port/$$
            ```            
            If you are behind an NTLM proxy, you can use a third party tool like             **[CNTLM](http://cntlm.sourceforge.net/)**  to do the NTLM proxy authentication. See the [CNTLM
            documentation](http://cntlm.sourceforge.net/) for instructions.

Let's begin.

1.  Stop the WSO2 product server if it is running.

2.  Go to the **`<PRODUCT_HOME>/bin`** directory and run the in-place
    updates tool that is appropriate to your OS:

    ``` java
    ./update_linux (On Linux)
    ./update_darwin (On OS X)

    The tool is currecntly not supported on Windows.
    ```

3.  When prompted, give the following:
    -   WSO2 subscription's user credentials.
    -   The [channel](Introduction_103318227.html#Introduction-channel) that
        you subscribed to (e.g., full or security) when getting a WSO2
        subscription.
4.  Note that the tool starts to update your product.

    ![](images/icons/grey_arrow_down.png){.expand-control-image}If the
    tool lists any conflicts, click to see how to resolve them...

    A conflict is likely to happen when a configuration file or artifact
    that you have customized has changed in the updates. If the
    file/artifact has conflicts, the tool does not attempt to merge it.
    In case you have customized .war or .car files, you need to apply
    the customizations on top of the updated .war and .car files.

    1.  Go to the locations of the files that have conflicts and note
        the following files that are created by the tool:  
        1.  The file that has your customizations (e.g., `test.jag`).
        2.  The file that was there in the previous update level, before
            updating (e.g., `test.jag.old`).
        3.  The file that is in the new update level, after updating
            (e.g., `test.jag.updated`).
        4.  The difference of the two files
            in **ii** and **iii **(e.g., `test.jag.diff`).
    2.  By looking at the three files (`.old`, `.updated`, and `.diff`),
        resolve the conflicts and save the resolved file with
        the **`.final` **extension (e.g., `test.jag.final`). 
    3.  Run the tool again with the '--continue' flag for the tool to
        merge the changes in `.final` file with the file which created
        the conflict.

        ``` java
        ./update_linux --continue (On Linux)
        ./update_darwin --continue (On OS X)
        ```

    4.  Go back to the location of the conflicting file and note that
        the tool has merged the `.final` file with the file that had
        your custom configurations and deleted all the other temporary
        files (i.e., `.old`, `.updated`, `.diff`, and `.final`)

5.  Restart the server.

6.  If you want to revert the updates and restore the previous state,
    run the following command:

    ``` java
    ./update_linux --revert (On Linux)
    ./update_darwin --revert (On OS X)
    ```

    **Tip**: To see a list of commands the tool provides, run the tool
    with the **--help** option.

You have now updated your product using the WSO2 in-place update tool.
