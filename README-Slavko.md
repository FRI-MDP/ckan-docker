- Using dev versions
- Docker:
    - `docker compose -f docker-compose.dev.yml build`
    - `docker compose -f docker-compose.dev.yml up --force-recreate` - Če se baza ne vzpostavi, zaženi parkrat, saj prvič inicializacija traja dlje.

- DataPusher
    - resubmit jobs: `docker exec -i ckan /usr/bin/ckan -c /srv/app/ckan.ini datapusher resubmit`
    - build image: `docker build -f datapusher/Dockerfile.fri-mdp-git -t semantic-datapusher .`
    - build image from dev compose: `docker compose -f docker-compose.dev.yml build datapusher --no-cache`

- Default credentials:
    - ckan_admin/test1234

- HINTS:
    - remove containers after .env changes
    - login to ckan container: `docker exec -it ckan /bin/bash`
    - remove all docker compose objects: `docker-compose -f docker-compose.dev.yml down --rmi all -v --remove-orphans`