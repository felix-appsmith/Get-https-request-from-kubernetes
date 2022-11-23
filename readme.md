# How to get HTTP petions list from Kubernetes instance
This is a brief guide on how to generate logs of the HTTPS requests that Appsmith executes when we execute a query. This can help to debug problems with the APIs executed by users.
## Steps
All the commands executed in the steps that we show below must be executed within the shell of the pod where Appsmith is hosted.
1. Enabled Ubuntu repositories.
```bash
sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository restricted
sudo add-apt-repository multiverse 
```
2. Run the following command to update the repositories.

`sudo apt-get update`

3. Install the tcpflow package with the following command.

 `sudo apt-get install tcpflow`
 
4. We will create a folder called `NetLogs`, and we will enter it follow the following commands.

```console
mkdir NetLogs
cd NetLogs
```

5. Now we execute the https requests listener on the port that it is executed on.

`tcpflow -p -c port 443 | tee NetLogs.log`

6. This will be put in listening format and reports the movements in an `.log` file that will be saved in the `NetLogs` folder.

7. now run a query in appsmith.
8. Now we will get the results of our NetLogs with the following command.

 `cat NetLogs.log`

9. Now we will copy the resulting information and put it into a file with the `.log` extension on our local machine.
