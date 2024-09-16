<h1>Initial Steps</h1>

You will need Kali virtualised (I used VirtualBox) and an account on https://www.elastic.co

Once Kali in running, navigate over to Elastic and click the drop down menu on top-left to "Add Integrations"

Select "Elastic Defend" and install it, it will then prompt you to install Elastic Agent on your host which is your Kali instance in this case

Copy the CLI command and paste it into Kali

![Installing Kali](https://github.com/user-attachments/assets/856c14fb-7b59-47e0-90d6-d7de821af74e)

Let the command run and type in your password to Kali when prompted

<h2>Generating Traffic</h2>

Generate some traffic to the SIEM with nmap scanning ``` nmap -A -p- localhost```
![finding open ports nmap](https://github.com/user-attachments/assets/d4b49c31-afe8-4082-a137-248f5d30a160)

Navigate to top left of Elastic and using the drop-down menu, go to "Logs"

If you filter by using ```process.args:"nmap"```, you can see the command used from the Kali instance.


<h3>Using Kibana to create a dashboard display</h3>
Using dropdown menu on top left, naviagate to "Dashboard"

Then select "create dashboard" and "create visulisation", we can set our horizontal as @timestamp and vertical as Count.

After saving, there will be a visualisation on the screen to visualise logs based on our horizontal and vertical axis we've assigned.
![Using Kibana to build dashboard](https://github.com/user-attachments/assets/f75784b4-391a-40eb-8509-4232fd0a26d6)


<h4>Creating a custom alert</h4>

From the drop-down menu in the top left, we can Create new rule through "Manage rules" and "Create new rule"

We can select "Custom Query" and ```event.action:"nmap_scan"```
You can also select which platform the alerts are passed through.
![Nmap Detect Rule](https://github.com/user-attachments/assets/e8f3b687-bd39-49f9-a3ea-66441ad23471)

We can also create an alert based off failed login attempts through the same method, but instead using ```event.action :"user_login" and event.outcome: "failure"```



![faled login rule](https://github.com/user-attachments/assets/e3f98b42-9854-4aef-bf5e-0f26ca5460ff)
