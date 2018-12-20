Manejo de ramas en GIT
============

- Primero procedemos a clonar un repositorio ya creado en GIT::


	$ git clone https://github.com/jesusacev/acsele.git
	Cloning into 'acsele'...
	warning: You appear to have cloned an empty repository.


- Nos mostrará un warning que estamos clonando un repositorio vacío. Luego accedemos al repositorio y listamos sus ramas locales, pero como está nuevo, no nos mostrará nada ya que tiene por defecto la rama master::


	$ cd acsele/
	$ git branch
	$


- Listamos las ramas remotas e igualmente no nos mostrará nada::


	$ git branch -r
	$


- Esto nos evidencia que estamos trabajando en la rama master, por lo que procedemos a crear un directorio y un archivo en dicha rama::


	$ mkdir a
	$ touch a/archivo1.txt


- Luego subimos la modificación al servidor GIT, especificando la rama master::


	$ git add *
	$ git commit -m "primer cambio"
	[master (root-commit) 6a6a61c] primer cambio
	 Committer: jacevedo <jacevedo@scm04.consis.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

	    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

	    git commit --amend --reset-author

	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 a/archivo1.txt

	$ git push origin master
	Username for 'https://github.com': jesusacev
	Password for 'https://jesusacev@github.com': 
	Counting objects: 4, done.
	Writing objects: 100% (4/4), 254 bytes | 0 bytes/s, done.
	Total 4 (delta 0), reused 0 (delta 0)
	To https://github.com/jesusacev/acsele.git
	 * [new branch]      master -> master


- Si listamos nuevamente las ramas, esta vez si nos indica que es la master, y no lo da por sobre entendido::


	$ git branch
	* master


- Igualmente las ramas remotas::


	$ git branch -r
  	origin/master


- Si hacemos un git log nos mostrará el historial de modificaciones subidas al servidor GIT, que en este caso es una sola::


	$ git log
	commit 6a6a61c2afb7696f14bee5d0806a3640f4c4b881
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:13:36 2018 -0400

	    primer cambio


- Luego hacemos la prueba creando otro archivo, lo subimos al GIT y posteriormente volvemos a verificar el git log de la rama master::


	$ touch a/archivo2.txt
	$ git add *
	$ git commit -m "segundo cambio"
	[master e52c70a] segundo cambio
	 Committer: jacevedo <jacevedo@scm04.consis.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

	    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

	    git commit --amend --reset-author

	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 a/archivo2.txt

	$ git push origin master
	Username for 'https://github.com': jesusacev
	Password for 'https://jesusacev@github.com': 
	Counting objects: 3, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (2/2), done.
	Writing objects: 100% (3/3), 282 bytes | 0 bytes/s, done.
	Total 3 (delta 0), reused 0 (delta 0)
	To https://github.com/jesusacev/acsele.git
	   6a6a61c..e52c70a  master -> master


- Realizamos el git log nuevamente y nos mostrará las 2 modificaciones::


	$ git log
	commit e52c70a2492fafa79fc82543d0be851d8216e229
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:16:24 2018 -0400

	    segundo cambio

	commit 6a6a61c2afb7696f14bee5d0806a3640f4c4b881
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:13:36 2018 -0400

	    primer cambio


- Ahora procedemos a crear una rama nueva::

	$ git branch jesus


- Luego listamos las ramas y aparecerá la nueva, pero seguimos suicheados a la rama master::


	 git branch
	  jesus
	* master


- Seguidamente nos suicheamos a la nueva rama creada::


	$ git checkout jesus
	Switched to branch 'jesus
	$ git branch
	* jesus
	  master


- Esta rama tendrá todas las modificaciones de la rama a donde la creamos, en este caso la rama master::


	$ ls a/
	archivo1.txt  archivo2.txt


- Luego creamos un nuevo directorio con un nuevo archivo en esta rama::


	$ mkdir b
	$ touch b/archivo1.txt
	$ ls
	a  b


- Y subimos los cambios al servidor GIT especificandole la nueva rama::


	$ git add *
	
	$ git commit -m "primer commit en rama de jesus"
	[jesus 2c4df67] primer commit en rama de jesus
	 Committer: jacevedo <jacevedo@scm04.consis.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

	    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

	    git commit --amend --reset-author

	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 b/archivo1.txt

	$ git push origin jesus
	Username for 'https://github.com': jesusacev
	Password for 'https://jesusacev@github.com': 
	Counting objects: 3, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (2/2), done.
	Writing objects: 100% (3/3), 310 bytes | 0 bytes/s, done.
	Total 3 (delta 0), reused 0 (delta 0)
	remote: 
	remote: Create a pull request for 'jesus' on GitHub by visiting:
	remote:      https://github.com/jesusacev/acsele/pull/new/jesus
	remote: 
	To https://github.com/jesusacev/acsele.git
	 * [new branch]      jesus -> jesus

	
- Cuando hacemos el git log, podemos ver las 2 modificaciones que nos trajimos de la rama master y la última realizada en la rama jesus::


	$ git log
	commit 2c4df67ab2f18b7973189cd6c25329bb29fa0733
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:24:44 2018 -0400

	    primer commit en rama de jesus

	commit e52c70a2492fafa79fc82543d0be851d8216e229
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:16:24 2018 -0400

	    segundo cambio

	commit 6a6a61c2afb7696f14bee5d0806a3640f4c4b881
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:13:36 2018 -0400

	    primer cambio


- Pero ahora haremos una prueba cambiandonos nuevamente a la rama master a ver que nos muestra::

	$ git checkout master
	Switched to branch 'master'
	Your branch is up-to-date with 'origin/master'.

	$ git branch
	  jesus
	* master


- Y el git log nos muestra las 2 modificaciones de la rama master pero no la realizada en la rama jesus::


	$ git log
	commit e52c70a2492fafa79fc82543d0be851d8216e229
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:16:24 2018 -0400

	    segundo cambio

	commit 6a6a61c2afb7696f14bee5d0806a3640f4c4b881
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:13:36 2018 -0400

	    primer cambio


- Esto evidencia que los cambios entre ramas son totalmente independientes.


- Sí queremos que los cambios de una rama sean llevados a otra rama, debemos ejecutar el comando merge, parados en la rama a donde queremos que se realiza la réplica::

	$ git branch
	  jesus
        * master

	$ git merge jesus
	Updating e52c70a..2c4df67
	Fast-forward
	 b/archivo1.txt | 0
	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 b/archivo1.txt


- Y sí hacemos un git log en la rama master nuevamente, veremos la modificación que habíamos realizado en la rama jesus::

	$ git log
	commit 2c4df67ab2f18b7973189cd6c25329bb29fa0733
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:24:44 2018 -0400

	    primer commit en rama de jesus

	commit e52c70a2492fafa79fc82543d0be851d8216e229
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:16:24 2018 -0400

	    segundo cambio

	commit 6a6a61c2afb7696f14bee5d0806a3640f4c4b881
	Author: jacevedo <jacevedo@scm04.consis.local>
	Date:   Wed Dec 19 11:13:36 2018 -0400

	    primer cambio


- Sí listamos veremos el directorio b, que lo habíamos creado en la rama jesus y no en la rama master, pero que lo trajimos a la rama master con el comando merge::

	$ ls
	a  b


- Cabe destacar que toda rama que se esta creando por primera vez, tendrá todo el contenido presente en la rama a donde estamos parados cuando se crea.


