# de-landscape

https://github.com/cncf/landscape2

``` bash
sudo podman pull public.ecr.aws/g6m3a0y9/landscape2:latest
mkdir data
chmod a+w data
sudo podman run --rm -v `pwd`/data:/home/landscape2/data --name landscape -it public.ecr.aws/g6m3a0y9/landscape2:latest "bash"
# ^^^ will launch container and put you at a bash shell inside
landscape2 new --output-dir data
cd data
landscape2 build --data-file data.yml --settings-file settings.yml --guide-file guide.yml --logos-path logos --output-dir build
# ^^^ will build the site, based on default settings and data in the data/*.yaml files
exit
# ^^^ will exit the container
cd data/build
python3 -m http.server
# ^^^ will run a web server that serves the static site for testing
```
