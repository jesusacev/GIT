Como instalar un servidor GIT
=====================================

Server
+++++++++

- Lo primero que debemos hacer es instalar el paquete git::

	# yum install git

- Luego creamos un directorio en /opt que será la estructura a donde guardaremos los repositorios::

	# mkdir /opt/repos

- Creamos el usuario de servicio para GIT::

	# useradd usergit

- Le asignamos el password al usuario de servicio::

	# passwd usergit

- Luego asignamos que el usuario de servicio y su grupo, sean propietarios del directorio creado (si solocas punto despues del usuario, te colocara el grupo al que este pertenece)::

	# chown -R usergit. /opt/repos/

- Verificamos el usuario y grupo propietario del directorio (con el parámetro -d le decimos que no entra al directorio, sino que me de exactamente la permisologia de esa ruta)::

	# ls -ld /opt/repos/
	drwxr-xr-x. 2 usergit usergit 6 dic  4 09:59 /opt/repos/

- Nos desplazamos hacia la ruta del directorio y nos suicheamos al usuario de servicio::

	# cd /opt/repos/
	# su usergit

- En este caso creamos 2 repositorios. Es importante colocarle la extensión .git ya que es un estandar::

	$ mkdir Training.git Cursos.git

- Nos movemos hacia uno de los repo creados y listamos sus archivos ocultos::

	$ cd Training.git/
	$ ls -la
	total 0
	drwxrwxr-x. 2 usergit usergit  6 dic  4 10:08 .
	drwxr-xr-x. 4 usergit usergit 44 dic  4 10:08 ..

- Como podemos ver solo estan los archivos del directorio actual y del anterior, por lo que debemos inicializar el repositorio con el siguiente comando::

	$ git --bare init
	Initialized empty Git repository in /opt/repos/Training.git/

- Si volvemos a listar se habrá creado esta estructura::

	$ ls
	branches  config  description  HEAD  hooks  info  objects  refs

- Hacemos el mismo procedimiento con el otro repositorio::

	$ cd ..
	$ cd Cursos.git/
	$ git --bare init
	Initialized empty Git repository in /opt/repos/Cursos.git/
	$ ls -la
	total 12
	drwxrwxr-x. 7 usergit usergit 119 dic  4 10:12 .
	drwxr-xr-x. 4 usergit usergit  44 dic  4 10:08 ..
	drwxrwxr-x. 2 usergit usergit   6 dic  4 10:12 branches
	-rw-rw-r--. 1 usergit usergit  66 dic  4 10:12 config
	-rw-rw-r--. 1 usergit usergit  73 dic  4 10:12 description
	-rw-rw-r--. 1 usergit usergit  23 dic  4 10:12 HEAD
	drwxrwxr-x. 2 usergit usergit 242 dic  4 10:12 hooks
	drwxrwxr-x. 2 usergit usergit  21 dic  4 10:12 info
	drwxrwxr-x. 4 usergit usergit  30 dic  4 10:12 objects
	drwxrwxr-x. 4 usergit usergit  31 dic  4 10:12 refs

- ¡LISTO! ya los repositorios Training.git y Cursos.git estan listos para ser utilizados.


Cliente
++++++++

- Luego nos vamos a una máquina cliente y clonamos uno de los reposirorios de manera local, conectandonos con el usuario de servicio::

	$ git clone usergit@192.168.0.188:/opt/repos/Cursos.git
	Cloning into 'Cursos'...
	usergit@192.168.0.188's password: 
	warning: You appear to have cloned an empty repository.

- Ingresamos al repositorio y listamos su contenido::

	$ cd Cursos/
	jacevedo@scm04:/tmp/Cursos$ ls -la
	total 20
	drwxr-xr-x  3 jacevedo jacevedo  4096 dic  4 10:16 .
	drwxrwxrwt 25 root     root     12288 dic  4 10:17 ..
	drwxr-xr-x  7 jacevedo jacevedo  4096 dic  4 10:17 .git

- Consultamos hacia donde esta apuntando nuestro repositorio local en el server::

	$ git remote -v
	origin	usergit@192.168.0.188:/opt/repos/Cursos.git (fetch)
	origin	usergit@192.168.0.188:/opt/repos/Cursos.git (push)

- Luego creamos un archivo dentro del repositorio local y lo subimos al server::

	$ touch prueba
	$ git add *
	$ git commit -m "prueba"
	master (root-commit) c0c89de] prueba
	 Committer: jacevedo <jacevedo@scm04.consis.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

	    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

	    git commit --amend --reset-author

	 1 file changed, 1 insertion(+)
	 create mode 100644 prueba

	$ git push
	usergit@192.168.0.188's password: 
	Permission denied, please try again.
	usergit@192.168.0.188's password: 
	Counting objects: 3, done.
	Writing objects: 100% (3/3), 232 bytes | 0 bytes/s, done.
	Total 3 (delta 0), reused 0 (delta 0)
	To 192.168.0.188:/opt/repos/Cursos.git
	 * [new branch]      master -> master

- Finalmente este archivo ya puede ser visto por cualquier otro cliente que uitilice el server GIT.


	







	

	



	

