# blabberbot

Following is step by step explanation of the given Linux history:

1. **Update your Packages**   
   Update your existing list of packages by executing:

   ```shell
   sudo apt-get update
   ```

2. **Install Required Packages**   
   Install necessary packages which are `ca-certificates`, `curl`, and `gnupg`:

   ```shell
   sudo apt-get install ca-certificates curl gnupg
   ```

3. **Setup Docker Repository**   
   Here the Docker's official **GPG key** is added:

   ```shell
   sudo install -m 0755 -d /etc/apt/keyrings
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   sudo chmod a+r /etc/apt/keyrings/docker.gpg
   ```

   Define the repository as an APT source:

   ```shell
   echo   "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
   "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

   Update the APT package cache:

   ```shell
   sudo apt-get update
   ```

4. **Install Docker Components**   
   Now install `docker-ce`, `docker-ce-cli`, `containerd.io`, `docker-buildx-plugin`, and `docker-compose-plugin`:

   ```shell
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

5. **Test Docker Installation**   
   To verify Docker was installed correctly, try to run the hello-world container:

   ```shell
   sudo docker run hello-world
   ```

6. **Setting up the Application**   
   Navigate to the `chat` directory, or if it doesn't exist, create it:

   ```shell
   mkdir chat
   cd chat
   ```

7. **Install Git**

   If Git hasn't been installed, you can do so with:

   ```shell
   sudo apt install git
   ```

8. **Clone the Repository**   
   Clone the 'keeperchatbot' project from GitHub:

   ```shell
   git clone https://github.com/maksimu/keeperchatbot.git
   ```

9. **Navigate into the Project**   
   Change the directory to the newly cloned keeperchatbot directory:

   ```shell
   cd keeperchatbot/
   ```

10. **Setting up the Environment File**

    - Create a new file named `.env` in the same directory where your Docker Compose file is located.
    - Open the `.env` file with your preferred text editor and add the following entries to your `.env` file:
     ```shell
     LE_EMAIL=<your-email>
     CHAT_DOMAIN=<your-domain>
     ```
     Note: Replace `<your-email>` and `<your-domain>` with your actual email and domain. Do not commit `.env` file to the source control.

11. **Start the Project with Docker Compose**   
    To start the project with Docker Compose, use the following command:

    ```shell
    sudo docker compose up
    ```
