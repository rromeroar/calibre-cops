# calibre

This contains the docker file and all necessary files to build a docker container for calibre with cops

### Preperation
Before running the container, you'll need to have the following directories predefined on the container host:
```sh
library
addbooks
```
The library directory will hold your books & database.  addbooks will be used to add books to your library on a periodic basis.  I used:
```sh
/home/books/data/library
/home/books/data/addbooks
```
for the instructions below.  Just make sure you create them prior to starting the container.
### To run the container:
```sh
docker run -d --name=primary -v /home/books/data:/data:Z -p 80:80 bcleonard/calibre-cops
```
### To list books in the library:
```sh
docker run --rm=false -ti -v /home/books/data:/data:Z bcleonard/calibre-cops /scripts/list-books.sh
```
This will list all of the books in the library in the format "ID, Author, Title"
### To remove books in the library:
```sh
docker run --rm=false -ti -v /home/books/data:/data:Z bcleonard/calibre-cops /scripts/remove-books.sh -i ID
```
### To access COPS:
```sh
http://<docker_host>/apps/
```
### Notes:

### Issues:
1) none
