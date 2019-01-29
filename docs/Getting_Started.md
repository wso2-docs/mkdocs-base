# Getting Started

If you are new to WSO2 updates, here is how to install WUM and update
your product for the first time:

1.  Get a valid [WSO2 support
    subscription](https://wso2.com/subscription) or subscribe to
    our [free trial](https://wso2.com/subscription/free-trial).
2.  If you have a proxy server/firewall, grant access to the
    endpoints mentioned below.

!!! info "Info"
    WUM gets updates by connecting to the `https://api.updates.wso2.com`
    and `https://cdn.updates.wso2.com` endpoints in the WSO2 Update
    service. If your system connects to the Update service through
    a proxy server/firewall, grant access to these endpoints.  
    Since WUM is a command-line tool, the proxy should be configured
    from your command-line as follows: 

    ```
    export http_proxy=http://username:password@proxyhost:port/
    ```

    If you are behind an NTLM proxy, you can use a third party tool
    like  **[CNTLM](http://cntlm.sourceforge.net/)**  to do the NTLM
    proxy authentication. See the [CNTLM
    documentation](http://cntlm.sourceforge.net/) for instructions.

3.  Download and install WUM from <https://wso2.com/wum/download/>. The
    UI guides you through the process.
4.  Execute the following command on the command-line to initialize
    WUM. 

    ``` java
    wum init
    ```

5.  When prompted, give the WSO2 support subscription's user
    credentials.

6.  Note that the following directory is created in your computer:

    -   **On Unix**: \~/.wum3
    -   **On Windows**: C:\\users\\&lt;username&gt;\\.wum3

7.  WUM updates are available only for the WSO2 product versions listed
    in <https://wso2.com/updates/wum>. Let's start by downloading a
    vanilla product distribution.

    ``` java
    //Search for an available product
    wum search <keyword>
    E.g., wum search am

    //Download the product
    wum add <product>
    E.g., wum add wso2am-2.5.0
    ```

8.  Check whether the product has any recent updates using the following
    command:

    ``` java
    wum check-update <product>
    E.g., wum check-update wso2am-2.5.0
    ```

9.  Execute the following command to start updating your product:

    ``` java
    wum update <product>
    E.g., wum update wso2am-2.5.0
    ```

10. Note that the directory path of the new distribution appears on your
    terminal. You also get an email with details.

#### What's next? [Get continuous updates](Getting-Continuous-Updates_103318234.html).

  
