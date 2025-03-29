# ed-discohook

A Python program that listens to [edstem](https://edstem.org/) websockets for new threads and publish events to [Discord](https://discord.com/) via [webhooks](https://discord.com/developers/docs/resources/webhook).
This project mainly makes use of [edspy](https://github.com/bachtran02/edspy), a Python wrapper for edstem API which I also maintain. This repository has been modified to anonymize all posts. 

## Setup
1. Request an Ubunutu VM [here](https://vcm.duke.edu/apps/index).
2. Once the VM is provisioned, select your VM from the [managaement console](https://vcm.duke.edu/).
3. Uncheck "Automatic power downs?" This will ensure the webhook is continuously running.
4. Write down the hostname, admin user, and admin password.
5. In a terminal of your choice, run `ssh <ADMIN_USER>@<hostname>`. When prompted, enter the admin password. 
6. In the TA Discord, create an Ed feed channel and create a webhook. Read more about Discord wehooks [here](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks).
7. Find the course id by navigating to the Ed page and looking at the URL. The URL will look like this: `https://edstem.org/us/courses/<COURSE_ID>/discussion`
8. In your Ubunutu VM, clone the repo.
9. In `main.py`, configure the `COURSE_IDS` map using the course id(s) you found in step 7. If you don't like editing files through the command line, you can also clone the repository to your local machine, edit the files, push the changes, and then pull them down in the VM. 
10. Create an .env file using [this template](https://github.com/ece350TA/ed-discohook/blob/main/.env.example) and enter your Ed API token, which can be created [here](https://edstem.org/us/settings/api-tokens).
11. In `.env` file, also enter Discord webhook URLs of the channel you want to send the payload to. The key **must** match the values in the `COURSE_IDS` map in step 9.
12. Run `docker compose build` to build the project and then `docker compose up` to start running it.
