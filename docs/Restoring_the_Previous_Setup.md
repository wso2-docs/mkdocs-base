# Restoring the Previous Setup

When there is an error in the current environment, you might want to
roll back the updates and restore the previous stable distribution. To
roll back your updates, you need to know which product distribution is
currently running in your environment and the previous distribution that
was stable. Therefore, it is recommended to keep records of your
distributions as a best practice. The previous stable distribution
should be stored in your local product repository and should be a fresh
ZIP file without any customizations. You can roll back in two ways:

### Roll back updates using automation

If you are using an automation tool such as Puppet, Ansible, or Chef,
follow the steps given below:

1.  Apply the previous stable product distribution to your configuration
    management tool. This should be a fresh ZIP without customizations.
2.  Revert the configurations specific to the updates from the
    configuration management tool. See the update summary PDF inside
    the &lt;user\_home&gt;/.wum-wso2/updates/summary-&lt;time
    stamp&gt; folder to check the configurations that were applied to
    the environment.
3.  Apply all your customizations to the product distribution. If you
    are using a deployment synchronization tool, make sure that these
    customizations are merged in the tool.
4.  Push the product distribution to your environment using the
    configuration management tool.

### Roll back updates manually

1.  Apply the configurations to the previous stable product
    distribution.
2.  Apply all your customizations to the product distribution. If you
    are using a deployment synchronization tool, make sure these
    customizations are merged in the tool.
3.  Push the product distribution to your environment.
