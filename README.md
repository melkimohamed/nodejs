# Intégration contenue (CI) avec Jenkins et Github
## Task 1 : création projet NodeJs/Angular sur Github

Cloner le projet nodejs/Angular sur votre machine et le pousser sur votre propre compte github

Aller sur git et cloner ce projet
https://github.com/melkimohamed/nodejs
Commande :git clone  https://github.com/votrelogin/nodejs
Aller sur votre compte git et créer une nouvelle reposotery « nodejs»
Supprimer le dossier .git de dossier télecharger : git rm –rf .git
Exucuter les commandes suivant pour metre le projet sur votre propre github
 git init
Git add .
git commit –m "push project todolist"
git remote add origin https://github.com/melkimohamed/nodejs.git
git push origin master

Maintenant vous avez le projet todolist sur votre propre compte github.
## Task 2- Instalation  Jenkins
1.	Sous ubuntu
wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins

##Commandes Jenkins
Démarrer Jenkins
systemctl satart jenkins
Stoper le service
systemctl stop jenkins
Voir le statut de service
systemctl status jenkins
Redamarer jenkins
systemctl restart jenkins

## Task 3 : Premier pas avec  jenkins	
Connecter à localhost :8080
Pour récuperer le mot de passe par defaut excuter la commande :
cat /var/jenkins_home/secrets/initialAdminPassword
Presentation de tableau de board

## Task 4: Mon premier project Jenkins

1.	Connectez-vous sur jenkins
2.	Cliquez sur New item et  et choisissez  Freestyle project
3.	Dans le tab  Source code Manegement  cochez git et inserer l’url de votre projet
4.	Dans le tab  Build Triggers, cocher Build periodically ensuite inserer H/05 * * * *
5.	Dans le tab  build  selectionner excute shell et inserer npm install
6.	Lancement de primier job
	Dans le sidebar: cliquer sur build Now ou sur l’icon de build sur le projet
	Allez sur workspace pour vore votre nouveau projet télecharger  avec l’ajout d’un nouveau dossier « node_modules »
7.	Builder votre projet
	Cliquer sur configurer  et dans le tab  build ajouter un nouveau commande shell et inserer 
	Npm start
8.	Cliquer sur build Now, si le build se termine avec succès, allez sur localhost:3000 pour voir votre projet

## Task 5 Création de webhook avec git 
1.	Creation de webhook
	- Sur votre projet github: aller sur setting > Webhooks & services > Add Webhook 
	- Dans le champs: Playload url inserer votre url localhost:8080/github-webhook/
	- Cocher Just the push event.
2.	Configuration de  build triggers
	Aller sur jenkins et modifier le projet: dans le tab « build triggers » cocher GitHub hook trigger for GITScm polling
3.	Creation de votre premier commit
	Sur votre projet git en local essayer de modifier quelque chose dans le code example  la traduction  de deux fichier 
	\public\app\components\item\item.component.html
	\public\app\components\list\list.html
	Apres modification  executer les commandes git suivantes :
	git status
	git add .
	git commit –m “my new commit”
	git push origin master
	Allez sur jenkins et vous observez un nouveau build se lanse automatiquement pour builder le projet
	Aller ensuite sur votreadresse:3000 pour voir le nouveau build de nouveau





