# prerequisites
- docker

# download map
docker run --rm --mount src="$(pwd)",dst=/tiles,type=bind versatiles/versatiles-frontend:latest-alpine \
 versatiles convert --bbox-border 3 --bbox "5.988,47.302,15.017,54.983" https://download.versatiles.org/osm.versatiles /tiles/germany.versatiles

# run docker
docker run --rm -p 8090:8080 --mount src="$(pwd)",dst=/tiles,type=bind,readonly versatiles/versatiles-frontend:latest-alpine \
versatiles serve -s frontend-dev.br.tar '[osm]/tiles/germany.versatiles'
