# Getting Continuous Updates

If you are **an existing WUM user**, do the following to update your
products. If not, see [Getting Started with
WUM](Getting-Started_103318232.html).

In these steps, you move updates to production by extracting the updates
into a ZIP file, testing the updates, and then manually merging them to
the existing product distribution. You do not replace the existing
production setup with the WUM-updated setup.

Before you begin, do you have a proxy server/firewall? Then, grant
access to the endpoints mentioned below.

??? note "Click for more information"

    WUM gets updates by connecting to the `https://api.updates.wso2.com`
    and `https://cdn.updates.wso2.com` endpoints in the WSO2 Update service.
    If your system connects to the Update service through a proxy
    server/firewall, grant access to these endpoints.  
    Since WUM is a command-line tool, the proxy should be configured from
    your command-line as follows: 

    ```#!js
    export http_proxy=http://username:password@proxyhost:port/
    ```

If you are behind an NTLM proxy, you can use a third party tool like
**[CNTLM](http://cntlm.sourceforge.net/)** to do the NTLM proxy
authentication. See the [CNTLM
documentation](http://cntlm.sourceforge.net/) for instructions.

1.  Run the following commands to check whether there are updates
    available:

    ```#!js
    wum check-update <product>
    E.g., wum check-update wso2am-2.5.0
    ```

2.  If an update is available, run the following command to start
    updating your product:

    ``` java
    wum update <product>
    E.g., wum update wso2am-2.5.0
    ```

    Your local product repository should now contain the latest and the
    previous WUM-updated distributions. Let's extract the updates in the
    latest WUM-updated distribution to a ZIP file.

3.  Execute the following command to identify the previous WUM-updated
    pack for this product.

    ``` java
    wum list [product-name]
    E.g., wum list wso2am
    ```

4.  Execute the following command:
    ``` java
    wum diff <Latest-WUM-updated-distribution.zip> <Previous-WUM-updated-distribution.zip>
    ```

>!!! note
        **Note** that the diff ZIP is created in the location from where you
        executed the diff command.

>    Next, let's apply the WUM updates that you extracted to the ZIP file
    to the distribution pack that is currently running in your
    environment.

5.  Open the summary PDF that you get inside this ZIP file (also via
    email). It contains information about the:

    -   New configurations introduced with the update.

    -   Existing files/artifacts that are affected due to the update.

6.  If you do not have any customizations in the existing distribution,
    simply copy the changed configuration files mentioned in the ZIP to
    the corresponding directories in your product distribution.

7.  If you **have **customizations in the existing distribution, there
    might be conflicts between that and the WUM-updated distribution. 

    ![](images/icons/grey_arrow_down.png){.expand-control-image}Click to
    read how to resolve conflicts...

    A conflict happens when a customized configuration file or artifact
    has changed in the WUM updates. As the file/artifact has your
    customizations in it, it is not recommended to completely replace
    this file with the file that comes with the update.

    Given below is how to resolve conflicts manually in different types
    of files/artifacts:

    <table>
    <thead>
    <tr class="header">
    <th>File Type</th>
    <th>How to Merge the Conflicts</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Binary files</td>
    <td><div class="content-wrapper">
    <p>Copy all the binary files (.jar, .jks, .car, .war) to the relevant directories in your existing product distribution. If you have made any customizations to .car and .war files, manually merge those changes.</p>
    <div>
    <div>
    <p>Note: If there are .war files in the WUM update, be sure to delete all extracted .war files in your existing product distribution.</p>
    <p>This is because all deployed .war files get extracted at the server startup and if there are already extracted .war files by that same name, the server will not extract the .war files in the WUM update.</p>
    </div>
    </div>
    </div></td>
    </tr>
    <tr class="even">
    <td>Jaggery files</td>
    <td><p>You cannot replace the Jaggery artifacts in your existing product distribution with the WUM-updated Jaggery artifacts because your existing Jaggery artifacts may contain customizations. Here's how to merge the files:</p>
    <ol>
    <li>Check the summary PDF to identify how the Jaggery files have changed because of the WUM updates.</li>
    <li>Apply the changes to the same files in your existing product distribution.</li>
    </ol></td>
    </tr>
    <tr class="odd">
    <td>Apply the updated configuration files</td>
    <td><p>Identify the configuration updates in the summary PDF and apply them (by merging) to the relevant configuration files in the /repository/conf folder of your existing product distribution.</p>
    <p>Note: Be sure to merge the configuration files in your environment with the new files. It is not recommended to replace them.</p></td>
    </tr>
    <tr class="even">
    <td>Redundant files</td>
    <td>If there are artifacts/files that are removed by the WUM updates, remove them from your existing product distribution.</td>
    </tr>
    <tr class="odd">
    <td>Newly added files</td>
    <td>If there are newly added files listed in the PDF, create the same folder structure (if it doesn't exist) in your existing product distribution and add the file.</td>
    </tr>
    </tbody>
    </table>

8.  Do you have additional WSO2 features installed in your product
    distribution? If so,

    ![](images/icons/grey_arrow_down.png){.expand-control-image}Click to
    read on...

    Please note that WSO2 **does not** **recommend** installing new
    features to standard products. If you already have features
    installed, you need to install the same features in the new product
    distribution and apply the patches. Please contact team WSO2 as this
    needs to be handled on a case-by-case basis.

9.  Test the updated product distribution and deploy it in your
    production environment.