# Elasticsearch + Kibana on Docker

This project comes out of [`deviantony/docker-elk`](https://github.com/deviantony/docker-elk) repository template. It builds a subset of the Elastic stack on Docker, namely Elasticsearch and Kibana.

## Table of contents

1. [Usage](#usage)
2. [Network & ports](#network--ports)

## Usage

> _Read [`deviantony/docker-elk` README.md](https://github.com/deviantony/docker-elk#elastic-stack-elk-on-docker) for complete documentation on how to use this project._

1. Install dependencies:

    [https://github.com/deviantony/docker-elk#host-setup](https://github.com/deviantony/docker-elk#host-setup)

2. Clone the repository.

3. Start services:

    [https://github.com/deviantony/docker-elk#bringing-up-the-stack](https://github.com/deviantony/docker-elk#bringing-up-the-stack)

4. Configure user authentication:

    > ⚠️ **Write down generated usernames and passwords; they ARE NOT automatically stored anywhere**.

    [https://github.com/deviantony/docker-elk#setting-up-user-authentication](https://github.com/deviantony/docker-elk#setting-up-user-authentication)

5. Copy `kibana/kibana.env.dist` to `kibana/kibana.env`.

    ```shell
    cp kibana/kibana.env.dist kibana/kibana.env
    ```

6. Update URIs, usernames and passwords in `kibana/kibana.env`, if applicable.

    _Check [this link](https://github.com/deviantony/docker-elk#setting-up-user-authentication) for indications on which users to use for each specific service._

7. Restart Kibana:

    ```shell
    docker-compose restart kibana
    ```

8. Enter Kibana:

    [http://localhost:5601](http://localhost:5601)

## Network & ports

Since this setup is intended to be accessed from and access to multiple locations, most probably out of the Docker environment, all of the services are running in **host network mode**.

This implies that applications run as if running in the host machine and bind to host machine ports and IPs, which imply they must be available for the underlying services.

By default, configured ports are:

- Kibana:
  - `5601`

- Elasticsearch:
  - `9200`
  - `9300`

In case any of those ports is not available on the host machine, you will have to manually change it to an available one in the proper section of the `docker-compose.yml` file and in the specific environment files (`kibana/kibana.env`), if applicable, and restart the proper service.
