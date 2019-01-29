# Troubleshooting

WUM is a simple command-line tool that you can download and use to get
the latest updates for a WSO2 product. To get started from the command
line, execute the 'wum --help' command, and the list of available
commands and its usage will be explained. If you want detailed,
step-by-step instructions on how to use WUM to get a WSO2 product
updated, see [Getting Started with WUM](Getting-Started_103318232.html).

We will now explain how to troubleshoot errors that you may encounter
while working with WUM.

WUM Message

Explanation

Possible Solution

wum: unable to connect to WSO2 Update

The WUM client cannot connect to the WSO2 Update server due to a network
failure or the server response is not successful.

Check your network connection.

If the connection is still failing, please report to WSO2 at
<https://wso2.com/contact>.

Please be sure to attach the details of the error when you report. You
can get the details by running the same command again using the '-v'
flag.

wum: update is not available in WSO2 Update: &lt;UpdateFileName&gt;

WUM is unable to get updates from the WSO2 Update service due to a
server error.

Try running the wum command again.

If the command continues to fail, please report to WSO2 at
<https://wso2.com/contact>.

Please be sure to attach the details of the error when you report. You
can get the details by running the same command again using the '-v'
flag.

  

  

  

wum: servers are busy at the moment. Please try again later.

The WSO2 Update server has reached the maximum capacity for handling
requests at the current moment.

wum: generating wum file twice. The file '&lt;FileName&gt;' has been
added by a previous update. Current update is'&lt;UpdateNumber&gt;'

WSO2 updates are cumulative, which means that once the update files
relevant to one particular update are downloaded once to your local
update repository, the same update file will not be downloaded again in
consequent updates. This error can sometimes (rarely) occur in
situations where a cumulative file is erroneously downloaded twice.

wum: invalid update file. Cannot find the update-descriptor.yaml
file'&lt;FilePath&gt;'

Some updates dispatched from the WSO2 Update server does not contain the
`update-descriptor.`yaml file. This file is stored inside the update
file that is downloaded to your local update repository.

wum: unknown form at in the update-descriptor.yamlfile'&lt;FilePath&gt;'
reason: &lt;Error Message&gt;

Some updates dispatched from the WSO2 Update server contains an
erroneous `update-descriptor.`yaml file. This file is stored inside the
update file that is downloaded to your local update repository.

wum: unable to zip directory '&lt;DirectoryPath&gt;' reason: &lt;Error
Message&gt;

When you run the 'wum update' or 'wum diff' commands, ZIP files should
be created with the relevant distribution/files inside your local
product repository. However, prior to creating the ZIP inside the
product repository, the original product distribution is copied to a
temporary directory location in order to apply the updates.

This error occurs if the product distribution (in the temporary
location) is deleted prior to generating the new ZIP file.

wum: unable to download updates reason: &lt;Error Message&gt;

WUM is unable to download the updates from the WSO2 Update server.

wum: invalid JWT string to process reason: &lt;Error Message&gt;

The JWT string is not in a valid format.

wum: cannot find the MD5 file of the specified product in WSO2 Update

WUM is unable to find the md5 sum of a file.

wum: unable to generate the update summary. reason: &lt;Error
Message&gt;

WUM is not able to generate the update summary PDF for various reasons.
When WUM generates a new product distribution ZIP file or a WUM diff ZIP
file, a summary PDF file should be generated and stored inside the ZIP
file (stored in the local product repository). The updated
distribution/ZIP will not be created without the summary ZIP.

wum: invalid update file. Update number of the update file name
'&lt;FilePath&gt;' is not equal to update number specified in
update-descriptor.yamlfile(&lt;UpdateNumber&gt;)

When WUM generates a new product distribution (ZIP file) or a ZIP file
with updates (WUM Diff), your local update repository is checked for
updates that have already been downloaded during previous updates.

This error occurs when at least one of the update files in the local
update repository is invalid, or if it has been manipulated by a user.

wum: invalid credentials  
  

The credentials you provided are not valid. If your WSO2 account was
created a short while back, the reason for the login failure may be that
your credentials are not synced in the WSO2 Update server.

Try again by providing the correct credentials. If your account was
created a short while back, you might have to wait.

If authentication is still failing, please report to WSO2 at
<https://wso2.com/contact>.

Please be sure to attach the details of the error when you report. You
can get the details by running the same command again using the ['-v'
flag](#Troubleshooting-wum_commands).

  

  

wum: you haven't initialized WUM with your WSO2 credentials

You have not initialized WUM. In order to update products, WUM should
first be initialized.

You can run the 'wum init' command to initialize WUM using your
credentials.

See the [instructions on initializing
WUM](Getting-Started_103318232.html) for more information.

wum: your session has timed out

The user session has timed out.

wum: unable to read your input reason: &lt;Error Message&gt;

The input value you provided with the wum command is invalid.

Enter a valid input for the wum command and try again.

See [Getting Started with WUM](Getting-Started_103318232.html) for
instructions on using the wum commands.

wum: file not found

You are attempting to add a product from a specific directory path to
the local product repository using the following command:

``` java
wum add --file <Path_to_product_download>/<product>.zip
```

However, the product file is not available in the directory you
specified.

Verify the directory path of the product distribution that you want to
add to the repository, and then run the command again.

See the [instructions on adding products to the product
repository](Getting-Started_103318232.html).  
  
  

wum: invalid product filename: &lt;ProductFileName&gt;

The name of the product distribution that you provided with the wum
command is wrong or it does not exist in the local product repository.

Verify the product distribution's name and run the command again.

wum: product &lt;productName-productVersion&gt; is already added

The product version that you are trying to add to your local product
repository already exists in the repository.

Try the following:

1.  First, delete the distribution from the local product repository
    using the '[wum delete](WUM-Commands-Guide_103318237.html)' command.
2.  Then, try adding the product again.

wum: your product distribution '&lt;ProductFileName&gt;' contains local
modifications. MD5 check failed.  
Please use the original product distribution.

The product distribution that you are trying to update contains local
modifications. WUM updates can only be applied to original product
distributions (ZIP files) or to original product distributions that have
been updated by WUM previously.

Try the following:

1.  First, delete the distribution with local modifications from the
    product repository using the '[wum
    delete](WUM-Commands-Guide_103318237.html)' command.
2.  [Add a new product](Getting-Started_103318232.html).
3.  [Update the new product](Getting-Continuous-Updates_103318234.html)
    you added.

wum: cannot find a matching product for '&lt;Pattern&gt;'

When executing the wum command, the pattern you used to specify the
product is wrong.

When you run the wum command, specify the product using a pattern that
matches the product name. For example, wso2esb-4.9.0, wso2esb, wso2e
etc.

  

  

wum: unable to parse the given product pattern '&lt;ProductPattern&gt;'.
reason: &lt;Error Message&gt;

wum: product '&lt;ProductName-ProductVersion&gt;' is not supported by
WSO2 Update.

wum: invalid product '&lt;ProductName-ProductVersion&gt;'

wum: you are not supposed to set a value for
'repositories.&lt;RepoName&gt;.refreshtoken'

You are using the 'wum config' command to change the refresh token of
the product repository (specified in the `config.yaml` file), which is
not allowed.

You are not allowed to change the refresh token, access token or any
other element related to the local product repository (except the
directory location).

The 'wum config' command should only be used to change the location of
the local product repository as explained here.

wum: you are not supposed to set a value for
'repositories.&lt;RepoName&gt;.accesstoken'

You are using the 'wum config' command to change the access token of the
product repository (specified in the `config.yaml` file), which is not
allowed.

  

wum: invalid repository config element '&lt;ConfigElement&gt;'

You are using the 'wum config' command to change an element in the
product repository (specified in the `config.yaml` file), which is not
allowed.

wum: invalid wumconfig element '&lt;Arguement&gt;'  
Try 'wum config --help' for more information.

You are using the 'wum config' command to change an element in the
product repository (specified in the `config.yaml` file), which is not
allowed.

wum: invalid number of arguments  
Try 'wum config --help' for more information.

The 'wum config' command can only have two valid arguments. You are
running the 'wum config' command using more than two arguments.

When you are running the 'wum config' command to change the local
product repository location, you should provide both the key and value
corresponding to the product repository (specified in the `config.yaml`
file) as shown below.

``` java
wum config local.product.repo ~/<new_directory_path>
```

-   Key: `local.product.repo`
-   Value: `~/<new_directory_path>`

wum:wumconfiguration is not available.

The WUM configuration file (`config.yaml`) stored in your local
`WUM_HOME` directory ( `~/.wum-wso2/`) is not available.

Try executing the '[wum init](WUM-Commands-Guide_103318237.html)'
command, which will create the configuration file.

wum: unable to get the absolute path of '&lt;Argument&gt;'

The path to the product distribution, which you provided with the
following command is not the absolute path:

``` java
wum add--file <Path_to_product_download>/<product>.zip
```

The relative path is not allowed with this command.

Run the command again using the absolute path to the product
distribution, instead of the relative path.

wum: you haven't added any products yet

You are attempting to execute a wum command without adding a product to
your local product repository.

Add the needed products to the local product repository by running the
'[wum add](WUM-Commands-Guide_103318237.html)' command.

wum: cannot validate the target distribution
'&lt;ProductName&gt;-&lt;ProductVersion&gt;.&lt;Timestamp&gt;'. Some
updates required are missing from the local repository, which are found
in the target distribution.

You have executed the 'wum diff' command to get the updates between two
product distributions. However, some updates, which are included in the
newer product distribution (stored in the local product repository) are
not available in the local update repository. When a WUM-updated product
distribution is created inside the local product repository, the
corresponding updates should be stored in the local update repository as
well.

This error may be because you have modified the contents of the local
update repository.

Try the following:

1.  First, delete the latest distribution from the product repository
    using the '[wum delete](WUM-Commands-Guide_103318237.html)' command.
2.  Generate a new updated distribution using the '[wum
    update](WUM-Commands-Guide_103318237.html)' command.
3.  Then, try the '[wum diff](WUM-Commands-Guide_103318237.html)'
    command again.

wum: unable to unzip file '&lt;FilePath&gt;' reason: &lt;Error
Message&gt;

You are attempting to update a product using the 'wum add' command, or
you are attempting to run the 'wum diff' command. However, the required
product ZIP files (in the local product repository) are unable to unzip
due to some corruption.

Try downloading the ZIP file again and run the 'wum update' or 'wum
diff' command.

wum: local repository path is not available.

When WUM is initialized, your local `WUM_HOME` directory
(` ~/.wum-wso2/`) is created, which contains the local update repository
and the local product repository as explained here.

This error occurs if the local product repository's path is missing in
the `config.yaml` file.

Update the product repository path in the `config.`yaml file using the
'[wum config](WUM-Commands-Guide_103318237.html)' command.

wum: unable to delete file '&lt;FilePath&gt;'. Please delete the file
manually. reason: &lt;Error Message&gt;

You have executed the 'wum delete' command, but WUM is unable to delete
the specified product file.

You can try manually deleting the product file from the local product
repository.

wum: unable to download. cannot find a matching product for
'&lt;ProductName-ProductVersion&gt;'

You have executed the 'wum add' command to download a product
distribution and to add it to the local product repository. However, the
product name you specified is not available for downloading.

Verify that the product name and version you provide is valid, and try
again.

See the instructions on adding products for more information.

wum: invalid timestamp value '%!d(string=&lt;Timestamp&gt;)'

The timestamp of the update file (stored in the local update repository)
or the product distribution file (stored in the local product
repository) has been manually changed.

Try providing a valid timestamp and running the wum command again.

wum: invalid product '&lt;ProductName-ProductVersion&gt;'. Product
version is missing

The pattern used to specify the product does not include the valid
product version. When the 'wum update' or 'wum diff' commands are
executed, the product name should include the version name.

Try providing a valid product pattern, which includes the correct
product version.

Follow the instructions in Getting Started with WUM.

wum: username or password cannot be empty

You have executed the 'wuminit' command to initialize WUM without
providing values for the username and password.

Give your credentials for the username and password, and try again.

See the instructions on initializing WUM.

wum: requires a product  
Try 'wum add --help' for more information.

You have not specified a product with the 'wum add' command. Note that
only one product can be specified at a time.

Make sure that the product name is specified when running the 'wum add'
command.

See the instructions on adding products for more information.

wum: requires only 1 product  
Try 'wum add --help' for more information.

You cannot specify more than one product with the 'wum add' command.

Make sure that only one product is specified with the 'wum add' command.

See the instructions on adding products for more information.

wum: requires only 1 product pattern  
Try 'wum check-update --help' for more information.

You cannot specify more than one product with the 'check-update'
command.

Make sure that only one product is specified with 'check-update'
command.

See the instructions on checking updates for more information.

wum: requires two updated product distributions  
Try 'wum diff --help' for more information.

You have executed the 'wum diff' command to get the updates between two
product distributions. However, you have only provided a single product
distribution.

Provide the two product distributions (with different timestamps) that
you want to compare, and try the 'wum diff' command again.

Be sure to use the product distribution names (including timestamps)
accurately.

wum: invalid update distribution names '&lt;Distibution1&gt;' -
'&lt;Distibution2&gt;'  
Try 'wum diff --help' for more information.

You have executed the 'wum diff' command to get the updates between two
product distributions. However, the provided product distribution names
are wrong.

wum: update levels cannot be the same  
Try 'wum diff --help' for more information.

You have executed the 'wum diff' command to get the updates between two
product distributions. However, you have provided the same product
distribution twice.

wum: requires only 1 product pattern  
Try 'wum list --help' for more information.

You have executed the 'wum list' command to get the list of product
distributions management by WUM. However, you have specified multiple
products.

Try the 'wum list &lt;product\_name&gt;' command with a single product
or try the 'wum list' command to get the list of all products.

See the instructions on checking the list of products managed by WUM.

You may encounter the following error messages due to permission
restrictions at OS-level.

WUM Message

Explanation

Possible Solution

wum: unable to create directory '&lt;Dir&gt;' reason: &lt;Error
Message&gt;

WUM is unable to create the specified directory in the relevant
location.

Check the permissions (OS-level) for creating folders in the relevant
locations. For example, you can enable permission to create folders in
the following locations:

-   WUM Home directory.
-   OS-specific temporary directory.

Also, check the available disc space and free some space if the
available space is insufficient.

If the error occurs even after enabling the above permissions, please
report to WSO2 at <https://wso2.com/contact>.

Please be sure to attach the details of the error when you report. You
can get the details by running the same command again using the '-v'
flag.

  
  
  
  
  
  
  
  
  

wum: unable to copy file '&lt;File&gt;' to '&lt;Path&gt;' reason:
&lt;Error Message&gt;

WUM is unable to copy the specified file to the relevant path.

wum: Failed to create directory: &lt;DirectoryPath&gt;. reason:
&lt;Error Message&gt;

WUM is unable to create the directory in the relevant location.

wum: unable to update LICENSE.txt of the product reason: &lt;Error
Message&gt;

WUM is unable to update the `LICENSE.txt` file of the product.

wum: unable to generate update log file. reason: &lt;Error Message&gt;

WUM is unable to generate the update log file (metadata file) inside the
local update repository.

wum: unable to store update summary. reason: &lt;Error Message&gt;

WUM is unable to store the update summary PDF in the local product
repository. When you execute the 'wum update' or 'wum diff' commands, an
update summary PDF file should be generated and stored inside the ZIP
file (which is the updated product ZIP, or the ZIP file created with the
WUM Diff).

wum: unable to delete the file as adviced in the update
'&lt;FilePath&gt;' reason: &lt;Error Message&gt;

When applying updates to the existing product distribution, WUM is
unable to delete files in the existing product distribution (as required
for the update).

wum: unable to load wum configuration from '&lt;FilePath&gt;'. reason:
&lt;Error Message&gt;

WUM is unable to read the `config.yaml` file in order to execute the
command.

wum: unable to create wum configuration. reason:

WUM is unable to create the `config.yaml `file in order to execute WUM.

wum: unable to calculate the MD5 of the specified file
'&lt;FilePath&gt;' reason: &lt;Error Message&gt;

WUM is unable to calculate the MD5 sum of the specified file.

wum: unable to read directory '&lt;ProductDir&gt;' reason: &lt;Error
Message&gt;

WUM is unable to read the specified directory when running the command.

wum: unable to delete the product: &lt;FilePath&gt; reason: &lt;Error
Message&gt;

WUM is unable to delete the specified file when running the command.

wum: Cannot create the temp directory wum-temp. reason: &lt;Error
Message&gt;

WUM is unable to create the temporary directory when running the
command.

wum: unable to create file '&lt;FilePath&gt;' reason: &lt;Error
Message&gt;

WUM is unable to create the file when running the command
