![image](http://workshop.industrial-architecture.cloud/images/atEonlfPz5Unq02sGCd1Nw.png)
Comme pour le premier checkpoint, celui-ci est un point d'étape. Il a pour principal objectif de te permettre de vérifier si tu as bien assimilé les compétences vues jusqu'à présent.
Il n'y a pas de surprises, les notions abordées sont celles vues dans les semaines qui viennent de s'écouler.
C'est un exercice individuel, Mais tu as bien sûr le droit de te référer aux quêtes que tu as déjà effectuées et à la documentation (Internet).
Tu devrais être en mesure de le finir dans le temps imparti. Plus tu as des automatismes, plus tu iras vite. Mais comme dans la vraie vie, on ne connait pas tout par cœur.
Néanmoins, il ne s'agit pas d'un examen. Si tu n'as pas fini au bout de la durée impartie, ne t'inquiète pas, **tu es fortement invité à retravailler le checkpoint** par la suite afin de réussir à valider les compétences. L'essentiel est que tu comprennes et sois capable de mettre en application les notions abordées, si tu n'as pas encore la rapidité, cela viendra en t'exerçant.
Ton formateur va t'aider dans cette évaluation en examinant le travail que as fourni et en validant la quête le cas échéant.
Si tu n'as pas tout fini dans les délais, tu ajouteras simplement un commentaire `# Effectué en dehors du timing`, pour l'indiquer à ton formateur. Ça lui permettra de bien comprendre les forces et faiblesses de chacun, et de s'adapter.

# Objectifs

- Réaliser l'un des 2 exercices du challenge ou les 2 !
- Valider les compétences acquises durant ces dernières semaines de formations  

# 🤓 Contexte de ce checkpoint
Tu travailles dans le service SI de la société **SweetCakes**.
Tu dois reprendre en urgence le travail de l'un de tes collègues.

# 💻 Outils mis à disposition

Tu as 1 VM que tu trouveras [ici]().
Il faut l'importer dans VirtualBox.

Voici leurs caracteristiques :

* Serveur DC :
  * OS : **Windows Server 2019**
  * RAM : 2 Go
  * Processeurs : 2
  * Compte d'administration : **Administrateur/Azerty123!**
  * Domaine : **checkpoint.lan**
  * Rôles installés : **AD, DHCP, DNS**
  * Configuration IP : **172.16.0.250 /24**

- - -
#  Challenge

## Exercice 1 : Script Powershell
Tu trouveras des fichiers (users.ps1 & users.csv) dans le dossier **Documents** du serveur.

Voici les fonctionnalités de ce script :
* Entrée : fichier csv contenant des nouveaux utilisateurs
* Sortie : création des utilisateurs

Tu trouveras ci-dessous les remarques des utilisateurs RH qui ont commencé à utiliser ce script.
Tu dois faire fonctionner ce script correctement avec la correction de tous les points.

```alert-info
Les points à corriger sont indépendant donc tu n'est pas obligé de suivre l'ordre.
```

1. La création d'un utilisateurs nommé "`prenom nom`" est systématique et amène une erreur. C'est à corriger.
2. Le mot de passe par défaut des utilisateurs est toujours le même car il est statique dans le script. Ton collègue a prévu une fonction `Random-Password` mais elle n'est pas utilisée. Tu dois t'en servir pour avoir des mots de passe dynamiques. Il faut que ce mot de passe comporte au moins **12 caractères**.
3. Le mot de passe des utilisateurs n'est pas affiché à la fin. A la place on a `System.Security.SecureString`. Il faut qu'il apparaisse en clair.
4. Le nom de la société (`Sweetcakes`) est statique. On doit pouvoir le modifier par une variable car ce script doit pouvoir servir pour d'autres sociétés.
5. Quelques fois les utilisateurs qui ont des accents dans leur nom ou leur prénom sont mal entré dans l'AD. C'est à corriger.
6. Les utilisateurs des services **Marketing** et **Comptabilité** ne sont pas créée. Il faut voir pourquoi.
7. Les numéros de téléphone de bureau et de mobile des utilisateurs sont inversé, c'est à corrigé.
9. Le script n'est pas du tout commenté. Tu dois mettre des commentaires à chaque `###`.
10. Ton collègue a oublié de mettre le mail des utilisateurs. Tu dois ajouter cette information dans la création.
11. L'information indiquant que le compte xxx est déjà créée donne toujours le même nom. C'est à corriger.
12. L'information indiquant que le compte a été crée doit apparaître en **vert** et si le compte existe déjà cela doit apparaître en **rouge**.

## Exercice 2 : Réseaux et domaine
Tu va devoir créer une deuxième VM **Client1** avec les caractéristiques suivantes : 
* Client 
* OS : Windows 10
* Disque : 50 Go (1 partition pour le système de 35 Go et 1 partition Data de 15 Go)
* RAM : 1 Go
* Compte utilisateur : wilder/Azerty123!
* Configuration IP : DHCP
* Hostname : Change le hostname en Client1

Connecte toi sur la machine cliente et fais la rejoindre le domaine, puis réponds aux questions suivantes.

```alert-warning
Les questions se suivent, donc tu dois les faire dans l'ordre
```

#### Sur la VM **Client1** :
1. Entre le PC **Client1** et le serveur **DC**, le ping ne fonctionne pas. Pourquoi ?
Change le paramétrage des machines pour que cela soit possible.
Explique ce que tu as fait sur les 2 machines.
2. Tente de te connecter avec l'utilisateur john.doe/Azerty123! sur Client1.
3. Tente de te connecter avec l'utilisateur jane.doe/Azerty123! sur Client1.
Quel est la différence entre les deux utilisateurs ? 
4. Que dois-tu faire pour pouvoir te connecter avec le comtpe de John Doe sur le Client1 ?
Explique et fais l'action.

#### Sur la VM **DC** :
5. Configure le serveur DHCP pour adresser entre **172.16.0.10** et **172.16.0.199** 
6. Fait un enregistrement de type A pointant vers **172.16.0.254** nommé **pfsense**.
7. Fait un alias sur l'enregistrement de type A qui s'appelle **firewall** (172.16.0.254).
8. Tu vas devoir créer des GPO qui s'appliquera aux utilisateurs.
   1. Les utilisateurs n'ont pas accès à l'invite de commande et au powershell.
   2. Les utilisateurs ont un fond d'écran imposé par l'entreprise [Télécharge l'image ici](https://drive.google.com/file/d/1dekvQBWvbXaougv3t2ournK5L92od1ex/view?usp=drive_link) 
   3. Les utilisateurs du domaine peuvent se connecter sur le poste **Client1 uniquement entre 9h et 17h**.

# 🧐 Critères d'acceptation

Exercice 1 :
* Le script complètement fonctionnel sous format .ps1

Exercice 2 :
* Les explications des questions sous format markdown
