
#### Local setup using Docker (Recommended)

Using Docker to install Jekyll and Ruby dependencies is the easiest way.

You need to take the following steps to get it up and running on your local machine:

- First, install [docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/install/).
- Finally, run the following command that will pull the latest pre-built image from DockerHub and will run your website.

```bash
docker compose pull
docker compose up
```

Note that when you run it for the first time, it will download a docker image of size 400MB or so. To see the template running, open your browser and go to `http://localhost:8888`. You should see a copy of the theme's demo website.

Now, feel free to customize the theme however you like (don't forget to change the name!). After you are done, you can use the same command (`docker compose up`) to render the webpage with all you changes. Also, make sure to commit your final changes.

> To change port number, you can edit `docker-compose.yml` file.

<details><summary>(click to expand) <strong>Build your own docker image:</strong></summary>

> Note: this approach is only necessary if you would like to build an older or very custom version of al-folio.

Build and run a new docker image using:

```bash
docker compose up --build
```

> If you want to update jekyll, install new ruby packages, etc., all you have to do is build the image again using `--force-recreate` argument at the end of the previous command! It will download Ruby and Jekyll and install all Ruby packages again from scratch.

If you want to use a specific docker version, you can do so by changing `latest` tag to `your_version` in `docker-compose.yaml`. For example, you might have created your website on `v0.10.0` and you want to stick with that.

- Beta
You can also change the docker image tag to slim! It is a slimmed docker image with a size of below 100MBs (same functionality).

</details>

---
