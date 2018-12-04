Mover data de un repositorio a otro desde el cliente
=================
- Primero borro el repositorio en el github, asegurandome que lo tenga clonado de manera local.

- Luego listo y tengo el .git, pero este está asociado al repositorio que borramos en el server por lo que debemos borrarlo::

	$ ls -la
	total 60
	drwxr-xr-x 5 jacevedo jacevedo  4096 dic  4 10:40 .
	drwxr-xr-x 8 jacevedo jacevedo  4096 dic  4 11:46 ..
	drwxr-xr-x 8 jacevedo jacevedo  4096 dic  4 10:45 .git
	drwxr-xr-x 2 jacevedo jacevedo  4096 dic  3 14:46 guia
	drwxr-xr-x 3 jacevedo jacevedo  4096 nov 30 16:54 imagenes
	-rw-r--r-- 1 jacevedo jacevedo 35149 nov 27 11:00 LICENSE
	-rw-r--r-- 1 jacevedo jacevedo   108 dic  3 15:42 README.md
	$ rm -rf .git

- Inicializamos el repositorio de manera local y podemos ver que se vuelve a crear el .git::

	$ git init
	Initialized empty Git repository in /home/jacevedo/Documentos/KB/Debian/.git/

	$ ls -la
	total 60
	drwxr-xr-x 5 jacevedo jacevedo  4096 dic  4 15:02 .
	drwxr-xr-x 8 jacevedo jacevedo  4096 dic  4 11:46 ..
	drwxr-xr-x 7 jacevedo jacevedo  4096 dic  4 15:02 .git
	drwxr-xr-x 2 jacevedo jacevedo  4096 dic  3 14:46 guia
	drwxr-xr-x 3 jacevedo jacevedo  4096 nov 30 16:54 imagenes
	-rw-r--r-- 1 jacevedo jacevedo 35149 nov 27 11:00 LICENSE
	-rw-r--r-- 1 jacevedo jacevedo   108 dic  3 15:42 README.md

- Luego creamos un nuevo repositorio en el server (que en este caso es git hub), y asociamos el repositorio local al creado en el servidor::

	$ git remote add origin https://github.com/jesusacev/Debian.git

- Por último subimos toda la data del reposiorio local al servidor::

	$ git add *
	$ git commit -m "debian"
	[master (root-commit) ed76f69] debian
	 Committer: jacevedo <jacevedo@scm04.consis.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

	    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

	    git commit --amend --reset-author

	 70 files changed, 971 insertions(+)
	 create mode 100644 LICENSE
	 create mode 100644 README.md
	 create mode 100644 guia/comoinstalardebian.rst
	 create mode 100644 imagenes/Instalacion_Debian_9/013.png
	 create mode 100644 imagenes/Instalacion_Debian_9/014.png
	 create mode 100644 imagenes/Instalacion_Debian_9/015.png
	 create mode 100644 imagenes/Instalacion_Debian_9/016.png
	 create mode 100644 imagenes/Instalacion_Debian_9/017.png
	 create mode 100644 imagenes/Instalacion_Debian_9/018.png
	 
	$ git push origin master
	Username for 'https://github.com': jesusacev
	Password for 'https://jesusacev@github.com': 
	Counting objects: 75, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (74/74), done.
	Writing objects: 100% (75/75), 1.13 MiB | 892.00 KiB/s, done.
	Total 75 (delta 0), reused 0 (delta 0)
	remote: 
	remote: Create a pull request for 'master' on GitHub by visiting:
	remote:      https://github.com/jesusacev/Debian/pull/new/master
	remote: 
	To https://github.com/jesusacev/Debian.git
	 * [new branch]      master -> master

- ¡Listo! Así movemos data de un repositorio a otro desde el cliente.

