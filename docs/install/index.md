# Installing Actual

Unlike most web apps, you’ll need to install Actual on a computer to get the full benefit out of it. While you could use Actual without running a server, we strongly recommend a server to ensure that your budget is saved and can be synced across multiple browsers and devices.

While running a server can be a complicated endeavour, we’ve tried to make it fairly easy to set up and hands-off to maintain. Choose one of the following options to get started:

- If you’re not comfortable with the command line and are willing to pay a small amount of money to have your version of Actual hosted on the cloud for you, we recommend [PikaPods](pikapods.md).
- If you’re willing to run a few commands in the terminal:
  - [Fly.io](fly.md) offers free cloud hosting.
  - You could [directly install Actual locally](local.md) on macOS, Windows, or Linux if you don’t want to use a tool like Docker. (This method is the best option if you want to contribute to Actual!)
  - If you want to use Docker, we have instructions for [using our provided Docker containers](docker.md).

Once you’ve set up your server, you can [configure it](../config/index.md) to change a few of the ways it works.

If you're coming from the original, managed Actual subscription service, you may want to [migrate your data](../migration/index.md).

## Additional Installation Options

In addition to our officially supported options listed above, some community members have written guides for using other platforms or tools:

:::caution

Content contained on external links is not managed or maintained by the Actual Budget team, if you run into issues with instructions on a third party site, please contact the author in the first instance or ask in discord where a member of the community may be able to help.

:::

- [Synology NAS](https://mariushosting.com/how-to-install-actual-on-your-synology-nas/)
- [Home Assistant](https://github.com/sztupy/hassio-actualbudget/blob/main/README.md)
- **Proxmox**
1. Download CT Template
   >"Debian-**-turnkey-nodejs".
   
2. Create Container
   >"Create CT".
   > * **Name:** Actual
   > * **Password:** Your Password for container
   > * **Template:** Debian-**-turnkey-nodejs
   > * **Disk Size:** 8GB
   > * **CPU:** 2 Cores
   > * **Memory:** 1024Mb
   
3. Start the Container, and navigate to the Console. Run through the guided setup & accept reboot at the end.

4. Once rebooted, login as root and use the password created.

*Steps as followed from [Local Installation section](docs/install/local)*

5. Install Yarn 
   ```js
   npm install --global yarn
   ```
   
7. Clone the Actual Server from Git
   ```bash
   git clone https://github.com/actualbudget/actual-server.git
   ```
   
9. Navigate to the directory cloned
   ```bash
   cd actual-server
   ```

10. Install all the dependencies
    ```bash
    yarn install
    ```

> [!IMPORTANT]
> 10. Create a SSL Certificate 
> ```bash
> openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout selfhost.key -out selfhost.crt
> ```
> 
> 11. Create a Config file to use the certificate created
> ```bash
> Nano config.json
> ```
> 
> 12. Inside Nano config file created, note the location of the certificate. Save and then exit nano.
>    ```json
>    {
>      "https": {
>        "key": "selfhost.key",
>        "cert": "selfhost.crt"
>      }
>    }
>    ```

13. Start the server with
    ```js
    yarn start
    ```

14. Open a new tab in your browser and enter the IP address on port:5006 
> [!TIP]
> Get the IP address in the console before starting the server, if you don't know it.
> ```bash
> ifconfig
> ```
