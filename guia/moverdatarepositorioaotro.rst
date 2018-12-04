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

- Inicializamos el repositorio de manera local y podemos ver que se vuelve a crear el .init::

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

- Luego creamos un nuevo repositorio en el server, y asociamos el repositorio local al creado en el servidor::

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
	 create mode 100644 imagenes/Instalacion_Debian_9/019.png
	 create mode 100644 imagenes/Instalacion_Debian_9/020.png
	 create mode 100644 imagenes/Instalacion_Debian_9/021.png
	 create mode 100644 imagenes/Instalacion_Debian_9/022.png
	 create mode 100644 imagenes/Instalacion_Debian_9/023.png
	 create mode 100644 imagenes/Instalacion_Debian_9/024.png
	 create mode 100644 imagenes/Instalacion_Debian_9/025.png
	 create mode 100644 imagenes/Instalacion_Debian_9/026.png
	 create mode 100644 imagenes/Instalacion_Debian_9/027.png
	 create mode 100644 imagenes/Instalacion_Debian_9/028.png
	 create mode 100644 imagenes/Instalacion_Debian_9/029.png
	 create mode 100644 imagenes/Instalacion_Debian_9/030.png
	 create mode 100644 imagenes/Instalacion_Debian_9/031.png
	 create mode 100644 imagenes/Instalacion_Debian_9/032.png
	 create mode 100644 imagenes/Instalacion_Debian_9/033.png
	 create mode 100644 imagenes/Instalacion_Debian_9/034.png
	 create mode 100644 imagenes/Instalacion_Debian_9/035.png
	 create mode 100644 imagenes/Instalacion_Debian_9/036.png
	 create mode 100644 imagenes/Instalacion_Debian_9/037.png
	 create mode 100644 imagenes/Instalacion_Debian_9/038.png
	 create mode 100644 imagenes/Instalacion_Debian_9/039.png
	 create mode 100644 imagenes/Instalacion_Debian_9/040.png
	 create mode 100644 imagenes/Instalacion_Debian_9/041.png
	 create mode 100644 imagenes/Instalacion_Debian_9/042.png
	 create mode 100644 imagenes/Instalacion_Debian_9/043.png
	 create mode 100644 imagenes/Instalacion_Debian_9/044.png
	 create mode 100644 imagenes/Instalacion_Debian_9/045.png
	 create mode 100644 imagenes/Instalacion_Debian_9/046.png
	 create mode 100644 imagenes/Instalacion_Debian_9/047.png
	 create mode 100644 imagenes/Instalacion_Debian_9/048.png
	 create mode 100644 imagenes/Instalacion_Debian_9/049.png
	 create mode 100644 imagenes/Instalacion_Debian_9/050.png
	 create mode 100644 imagenes/Instalacion_Debian_9/051.png
	 create mode 100644 imagenes/Instalacion_Debian_9/052.png
	 create mode 100644 imagenes/Instalacion_Debian_9/053.png
	 create mode 100644 imagenes/Instalacion_Debian_9/054.png
	 create mode 100644 imagenes/Instalacion_Debian_9/055.png
	 create mode 100644 imagenes/Instalacion_Debian_9/056.png
	 create mode 100644 imagenes/Instalacion_Debian_9/057.png
	 create mode 100644 imagenes/Instalacion_Debian_9/058.png
	 create mode 100644 imagenes/Instalacion_Debian_9/059.png
	 create mode 100644 imagenes/Instalacion_Debian_9/060.png
	 create mode 100644 imagenes/Instalacion_Debian_9/061.png
	 create mode 100644 imagenes/Instalacion_Debian_9/062.png
	 create mode 100644 imagenes/Instalacion_Debian_9/063.png
	 create mode 100644 imagenes/Instalacion_Debian_9/064.png
	 create mode 100644 imagenes/Instalacion_Debian_9/065.png
	 create mode 100644 imagenes/Instalacion_Debian_9/066.png
	 create mode 100644 imagenes/Instalacion_Debian_9/067.png
	 create mode 100644 imagenes/Instalacion_Debian_9/068.png
	 create mode 100644 imagenes/Instalacion_Debian_9/070.png
	 create mode 100644 imagenes/Instalacion_Debian_9/071.png
	 create mode 100644 imagenes/Instalacion_Debian_9/072.png
	 create mode 100644 imagenes/Instalacion_Debian_9/073.png
	 create mode 100644 imagenes/Instalacion_Debian_9/074.png
	 create mode 100644 imagenes/Instalacion_Debian_9/075.png
	 create mode 100644 imagenes/Instalacion_Debian_9/076.png
	 create mode 100644 imagenes/Instalacion_Debian_9/077.png
	 create mode 100644 imagenes/Instalacion_Debian_9/078.png
	 create mode 100644 imagenes/Instalacion_Debian_9/079.png
	 create mode 100644 imagenes/Instalacion_Debian_9/080.png

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

