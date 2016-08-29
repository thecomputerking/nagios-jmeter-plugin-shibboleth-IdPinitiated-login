# nagios-jmeter-plugin-shibboleth-IdPinitiated-login
A Nagios plugin written using jmeter to monitor a Shibboleth IdP using an IdP-initiated login.

This uses "nagios_jmeter_check" https://github.com/gmykhailiuta/nagios_jmeter_check to execute.

The jmx file is based on jmx work found here:
https://wiki.shibboleth.net/confluence/display/IDP30/Load+Testing+Contributed+Results

You also need some kind of java installed and jmeter binary distrobution installed here:
libexec/jmeter/apache-jmeter-2.13

This check assumes you have a Shibboleth SP active on your IdP. You can use a different SP, but you may need to adjust the jmx configuration.

Note: 
 - Following this example, you will need one jmx and one properties file per Shibboleth IdP node to monitor, See "To Do."
 - While monitoring nodes, you should also monitor the loadbalanced interface if clustered.

Instructions:
0. Edit libexec/jmeter/jmeter_plans/shibidpv3-unsolicited-login_shibidp-host.example.com.jmxand change the filename and hostname in the "IdPHost" element "Argument.value" to the FQDN of the node to be monitored, https://shibidp-host.example.com.
1. Edit libexec/jmeter/jmeter_plans/shibidpv3-unsolicited-login_shibidp-host.example.com.jmxelement "ProviderId" "Argument.value" to the entity ID of the SP being being used, entity:id:sp.idp.example.com.
2. Edit libexec/jmeter/jmeter_plans/shibidpv3-unsolicited-login_shibidp-host.example.com.jmx
element "ShibSP" "Argument.value" to the IdP SP service's FQDN, https://login.example.com.
3. Edit libexec/jmeter/jmeter_plans/shibidpv3-unsolicited-login_shibidp-host.example.com.jmx
element "j_username" "Argument.value" to your monitoring service account name, monitoring.account.
4. Edit libexec/jmeter/jmeter_plans/shibidpv3-unsolicited-login_shibidp-host.example.com.jmx
element "j_password" "Argument.value" to your monitoring service account password, secretpasswordformonitoringaccount.

To Do:
- Integrate dynamic hostname so you can use one jmx and one properties file for all IdP nodes.

