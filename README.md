# Data-diff testing

A uni project dedicated to software testing.\
The goal is to conduct a testing cycle on chosen product - for that purpose, our group, called the Brazilian Lift of Death, selected a tool called [data-diff](https://github.com/datafold/data-diff).

## Environment setup

The tests will be conducted on local environments (more on that in upcoming documentation) with all the secondary services, possibly with auxilary testing tools, containerised.

### Architecture
The graphics below describe the composed container architecture. 

![Git gud.](./container_architecture_light.png)

Presto and Trino (Younger brother of trino, stemming from the same project) are query engines, balancing the load between different databases (registered via .properties files in ```catalog``` folders). Postgres is a standard OLTP row-oriented database, Clichouse is a columnar OLAP solution, as well as Vertica (Community Edition), which is really not as easy to get known with as open source projects but at least I found [the documentation](https://docs.vertica.com/23.4.x/en/).

How to use the presto CLI directly on the docker image: [Link](https://prestodb.io/docs/current/installation/deploy-docker.html#installing-and-running-the-presto-docker-container)\
How to do the above, but from your local machine connecting to the docker? [Like that](https://prestodb.io/docs/current/installation/cli.html)\
Example of presto usage connested to a clichouse instance? [Got you](https://prestodb.io/docs/current/connector/clickhouse.html?highlight=clickhouse#querying-clickhouse)\
How to do the same with trino? [I'm glad you askn'](https://trino.io/docs/current/client/cli.html).

### Running docker compose
One has to install docker along with docker-compose on their machine (with accordance to the possesed OS). Then it's just a matter of running the command ```docker compose up```.

### Running presto

    docker exec -it presto-container ./bin/presto 