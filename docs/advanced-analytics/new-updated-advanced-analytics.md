---
title: "Mis à jour - Advanced Analytique des documents de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié dans, pour avancée d’Analytique pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: advanced-analytics
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: r-services
ms.author: genemi
ms.workload: advanced-analytics
ms.openlocfilehash: 840e34eee090d9fba2ec25e10375a8b0c375fea4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nouveaux et mis à jour récemment : Advanced Analytique pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Zone de sujet :* &nbsp; **avancées d’Analytique pour SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Ajouter SQLRUserGroup en tant qu’un utilisateur de base de données](r/add-sqlrusergroup-to-database.md)
2. [Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R sur SQL Server](r/use-revoscaler-to-manage-r-packages.md)
3. [À l’aide de R dans la base de données SQL Azure](r/using-r-in-azure-sql-database.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Problèmes connus dans les Services de Machine Learning](#TitleNum_1)
2. [Créer un référentiel de packages local à l’aide de miniCRAN](#TitleNum_2)
3. [Déterminer quels packages R sont installés sur SQL Server](#TitleNum_3)
4. [Installer des packages R supplémentaires sur SQL Server](#TitleNum_4)
5. [L’installation de fonctionnalités sur une machine virtuelle Azure d’apprentissage automatique SQL Server](#TitleNum_5)
6. [Installer préformé d’apprentissage des modèles sur SQL Server](#TitleNum_6)
7. [Comment éviter les erreurs sur les packages R sont installés dans les bibliothèques utilisateur](#TitleNum_7)
8. [Configurer un ordinateur virtuel pour l’apprentissage sur Azure](#TitleNum_8)
9. [RevoScaleR](#TitleNum_9)
10. [Activer ou désactiver la gestion des packages R pour SQL Server](#TitleNum_10)
11. [Configurer un client de science des données pour une utilisation avec SQL Server](#TitleNum_11)
12. [Configurer SQL Server Machine Learning Services (en base de données)](#TitleNum_12)
13. [Installation sans assistance de Machine Learning Services (de-de base de données)](#TitleNum_13)
14. [Étape 3 : Explorer et visualiser les données](#TitleNum_14)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp;[Problèmes connus dans les Services de Machine Learning](known-issues-for-sql-server-machine-learning-services.md)

*Mise à jour : 2017-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 321.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00121c648c21576d5c86494137de1d4d81e2e265 c65973f6ae9253af5ecc621916ef36d7c0398789  (PR=3980  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



**L’exécution du code Python ou de problèmes liés à des packages Python**


Cette section contient des problèmes connus qui sont spécifiques à l’exécution de Python sur SQL Server, ainsi que des problèmes liés aux packages Python publiés par Microsoft, y compris [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

**Appel au modèle préformé échoue si le chemin d’accès au modèle est trop long**


Si vous installez les modèles préformés dans une installation par défaut, en fonction de votre nom de l’ordinateur et le nom de l’instance, le chemin d’accès complet obtenu dans le fichier de modèle formé peut être trop long pour Python à lire. Cette limitation sera résolue dans une version de service à venir.

Il existe plusieurs solutions possibles :

+ Lorsque vous installez les modèles préformés, choisissez un emplacement personnalisé.
+ Si possible, installez l’instance de SQL Server sous un chemin d’installation personnalisé, tel que C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilisez l’utilitaire Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) pour créer un lien réel qui mappe le fichier de modèle sur un chemin plus court.

**Impossible d’initialiser une variable varbinary provoque une erreur dans BxlServer**


Si vous exécutez le code Python à l’aide de SQL Server `sp_execute_external_script`et le code possède des variables de type varbinary (max), varchar (max) ou des types semblables de sortie, la variable doit être initialisée ou définie dans le cadre de votre script. Sinon, le composant d’échange de données, BxlServer, déclenche une erreur et s’arrête de fonctionner.

Cette limitation sera résolue dans une version de service à venir. Pour résoudre ce problème, assurez-vous que la variable est initialisée dans le script Python. N’importe quelle valeur peut être utilisé, comme dans les exemples suivants :

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-create-a-local-package-repository-using-minicranrcreate-a-local-package-repository-using-minicranmd"></a>2. &nbsp;[Créer un référentiel de package local à l’aide de miniCRAN](r/create-a-local-package-repository-using-minicran.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 43.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 44b77cb127e9ffab1777216a66f0e5be9c82f3d2 65e30f10fc36acb3ce95f60f51f3501fbc98ad08  (PR=4150  ,  Filename=create-a-local-package-repository-using-minicran.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



-   **Simplifie l’installation hors connexion**: pour installer le package à un serveur en mode hors connexion nécessite que vous téléchargez également toutes les dépendances du package, à l’aide miniCRAN plus facilement obtenir toutes les dépendances dans le format correct.

-   **Amélioration de la gestion de version**: dans un environnement multi-utilisateur, il existe de bonnes raisons d’éviter sans restriction de l’installation de plusieurs versions de package sur le serveur.

Après avoir créé le référentiel, vous pouvez le modifier en ajoutant de nouveaux packages ou de la mise à niveau la version des packages existants.

**Étape 1. Installez le package miniCRAN**


Vous commencez par créer un référentiel miniCRAN à utiliser en tant que source. Vous devez créer ce référentiel sur un ordinateur qui a accès à internet.

1.  Installer le package miniCRAN et requis **igraph** package.

```
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
```

**Étape 2. Définir une source de package : un miroir CRAN, ou un instantané MRAN**


1. Spécifiez un site miroir à utiliser lors de l’obtention de packages.

```
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
```

2.  Indiquer un dossier local dans lequel stocker les packages collectées. Vous pas besoin de nommer le dossier miniCRAN ; Cela peut être un nom plus descriptif, tel que « GeneticsPackages » ou « ClientRPackages1.0.2 ».

    Veillez à créer le dossier à l’avance. Une erreur est générée si le `local_repo` dossier n’existe pas lorsque vous exécutez le code R ultérieurement.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp;[Déterminer quels packages R sont installés sur SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 13d93acedc6e6b4615f1a244a2a1542910feb69e 9a065066398843a4bed318fa46d4982d712915a9  (PR=4150  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



+ Si le package est trouvé, le message retourné doit être quelque chose comme « Commandes exécutée avec succès. »

+ Si le package ne peut pas être situé ou chargé, vous obtenez ce type d’erreur : « une erreur de script externe s’est produite : erreur dans library("RevoScaleR") : il n’existe aucun package appelé RevoScaleR »

**Obtenir la liste des packages installés à l’aide de R**


Il existe différentes façons d’obtenir la liste des packages installés ou chargés à l’aide d’outils ou de fonctions R. De nombreux outils de développement R fournissent un explorateur d’objets ou une liste des packages installés ou chargés dans l’espace de travail R actuel.

+ À partir d’un utilitaire R local, utilisez une fonction R de base, telles que `installed.packages()`, qui est inclus dans le `utils` package. Pour obtenir une liste est correcte pour une instance, vous devez spécifier le chemin d’accès de la bibliothèque de manière explicite, ou utiliser les outils R associés à la bibliothèque de l’instance.

+ Pour vérifier si un package dans un contexte de calcul spécifique, vous pouvez utiliser les fonctions suivantes à partir du package RevoScaleR. Ces fonctions vous aider à identifier les packages dans les contextes de calcul spécifié :

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

Par exemple, exécutez le code R suivant pour obtenir la liste des packages disponibles dans le contexte de calcul de SQL Server spécifié.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```
**Voir aussi**




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-install-additional-r-packages-on-sql-serverrinstall-additional-r-packages-on-sql-servermd"></a>4. &nbsp;[Installer des packages R supplémentaires sur SQL Server](r/install-additional-r-packages-on-sql-server.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3) | [suivant](#TitleNum_5))

<!-- Source markdown line 266.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ba48f1838857d90d6692aafc48f393777ac602fa 37de2586a344a99969bcd9a20723c021db2604a4  (PR=4150  ,  Filename=install-additional-r-packages-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Cette section fournit des conseils assorties et exemple de code liées à l’installation de package de R sur SQL Server.

**<a name="packageVersion"></a>Obtenir la version de package approprié et le format**


Il existe plusieurs sources de packages R, les plus connues étant CRAN et Bioconductor. Le site officiel pour le langage R (<https://www.r-project.org/>) répertorie la plupart de ces ressources. De nombreux packages sont publiés sur GitHub, où vous pouvez obtenir le code source. Toutefois, vous pouvez ont reçu des packages R développés par une personne dans votre entreprise.

Quelle que soit la source, vous devez vous assurer que le package que vous souhaitez installer a un format binaire pour la plateforme Windows. Dans le cas contraire, le package téléchargé ne peut pas exécuter dans l’environnement SQL Server.

Avant de télécharger, vous devez également vérifier si le package est compatible avec la version de R est en cours d’exécution dans SQL Server.

**<a name="bkmk_zipPreparation"></a>Télécharger le package en tant que fichier compressé**


Pour l’installation sur un serveur sans accès à internet, téléchargez une copie du package dans le format d’un fichier compressé pour l’installation en mode hors connexion. Ne pas décompressez le package.

Par exemple, la procédure suivante décrit pour obtenir la version correcte de la [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package à partir de Bioconductor, en supposant que de l’ordinateur a accès à internet.

1.  Dans la liste d’ **archives de package** , recherchez la version **binaire Windows** .

2.  Cliquez sur le lien vers le. Fichier ZIP, puis sélectionnez **enregistrer la cible sous**.

3.  Accédez au dossier local dans lequel les packages compressés sont stockés, puis cliquez sur **enregistrer**.

Ce processus crée une copie locale du package. Vous pouvez ensuite installer le package ou copier le package compressé vers un serveur qui n’a pas accès à internet.

Pour plus d’informations sur le contenu du fichier de format zip et comment créer un package R, nous vous recommandons de ce didacticiel, vous pouvez télécharger au format PDF à partir du site du projet R : [création de Packages R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-installing-sql-server-machine-learning-features-on-an-azure-virtual-machinerinstalling-sql-server-r-services-on-an-azure-virtual-machinemd"></a>5. &nbsp;[Machine d’installation de SQL Server apprentissage des fonctionnalités sur une machine virtuelle Azure](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_4) | [suivant](#TitleNum_6))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f4d287044b8bfda2dbe77fbf65b0d9cdd8f2ff42 2a8e33de6383f5d3af52256c5dfcb60184659eb8  (PR=4150  ,  Filename=installing-sql-server-r-services-on-an-azure-virtual-machine.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



6. Si vous envisagez de vous connecter à l’instance à partir d’un client de science des données à distance, effectuez [étapes supplémentaires--#-étapes additional) selon les besoins.

**Désactiver les fonctionnalités d’apprentissage machine sur une machine virtuelle SQL Server**


Vous pouvez également activer ou désactiver la fonctionnalité sur un ordinateur virtuel de SQL Server existant à tout moment.

1. Ouvrez le panneau de l’ordinateur virtuel.
2. Cliquez sur **Paramètres**, puis sélectionnez **Configuration de SQL Server**.
3. Apporter des modifications aux fonctionnalités et s’appliquent.

**<a name="existing"></a>Ajouter R Services à un SQL Server 2016 Enterprise machine virtuelle existante**


Si vous avez créé une machine virtuelle Azure incluant SQL Server sans l’apprentissage automatique, vous pouvez ajouter la fonctionnalité en suivant ces étapes :

1. Exécutez de nouveau.. ! NCLURE-NotShown--ssNoVersion--... /.. /Includes/ssnoversion-MD.MD)] le programme d’installation et d’ajouter la fonctionnalité sur le **Configuration du serveur** page de l’Assistant.
2. Activer l’exécution de scripts externes et redémarrez le.. ! NCLURE-NotShown--ssNoVersion--... /.. instance de /Includes/ssnoversion-MD.MD)]. Pour plus d’informations, consultez [défini de SQL Server R Services--... /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Configurez l’accès aux bases de données pour les comptes de travail R, si cela est nécessaire pour l’exécution des scripts à distance.
   Pour plus d’informations, consultez [définir les SQL Server R Services--... /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Modifiez une règle de pare-feu sur la machine virtuelle Azure, si vous souhaitez autoriser l’exécution de script R à partir des clients de science des données distants. Pour plus d’informations, consultez [débloquer le pare-feu--#firewall).
4. Installez ou activez les bibliothèques réseau nécessaires. Pour plus d’informations, consultez [Ajouter réseau protocoles--#network).



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-install-pretrained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>6. &nbsp;[Installation pretrained des modèles d’apprentissage automatique sur SQL Server](r/install-pretrained-models-sql-server.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_5) | [suivant](#TitleNum_7))

<!-- Source markdown line 96.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07b51584a90568cccceea382c44155e40e09c967 db083f8536fbb2ea5886fed787872867b5de5750  (PR=4150  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    For example, to enable use of the latest version of the pretrained models for Python, in a default instance of SQL Server 2017, you would run this statement:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    On a named instance, the command would be something like this:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Pour utiliser Python pretrained modèles avec Machine Learning Server (autonome) :

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Par exemple, en supposant que d’une installation par défaut de la Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server 2017, exécutez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. Les valeurs suivantes sont prises en charge pour le paramètre de version :



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-avoiding-errors-on-r-packages-installed-in-user-librariesrpackages-installed-in-user-librariesmd"></a>7. &nbsp;[Comment éviter les erreurs sur les packages R sont installés dans les bibliothèques utilisateur](r/packages-installed-in-user-libraries.md)

*Mise à jour : 2017-10-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_6) | [suivant](#TitleNum_8))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 52cb9a53d7d9c31ee9bc6977464ebd2a18081ff3 3537aa6755c66f12c19bb3448dc9b5c8abb9cc28  (PR=3619  ,  Filename=packages-installed-in-user-libraries.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=aecf422ca2289b2a417147eb402921bb8530d969) -->



Toutefois, cela peut ne jamais fonctionne lors de l’exécution des solutions R dans SQL Server, car les packages R doivent être installés dans une bibliothèque spécifique par défaut qui est associée à l’instance.

Sinon, vous risquez d’obtenir ce type d’erreur quand vous essayez d’appeler le package :

*Erreur dans library(xxx) : il n’existe aucun package appelé 'package-name'*

Il est également une pratique de développement incorrecte pour installer les packages R requis dans une bibliothèque d’utilisateur personnalisée, tel qu’il peut entraîner des erreurs si une solution est exécutée par un autre utilisateur qui n’a pas accès à l’emplacement de la bibliothèque.

**Comment installer des packages R pour une bibliothèque accessible**


**Pour SQL Server 2016**

Utilisez la bibliothèque de package associée à l’instance. Pour plus d’informations, consultez [packages R installés avec SQL Server--installing-and-managing-r-packages.md)

**Pour SQL Server 2017**

SQL Server fournit des fonctionnalités pour vous aider à gérer plusieurs versions de package et d’autoriser les utilisateurs à des packages individuels, sans nécessiter que les utilisateurs ont accès au système de fichiers.

Pour plus d’informations sur la façon de configurer une bibliothèque de package partagé et affecter des utilisateurs aux rôles, consultez [gestion des packages R pour SQL Server--r-package-management-for-sql-server-r-services.md.)




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-provision-a-virtual-machine-for-machine-learning-on-azurerprovision-the-r-server-only-sql-server-2016-enterprise-vm-on-azuremd"></a>8. &nbsp;[Configurer une machine virtuelle pour l’apprentissage sur Azure](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

*Mise à jour : 2017-10-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_7) | [suivant](#TitleNum_9))

<!-- Source markdown line 132.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 16439b4a8f5f4218edfcd746ed20ccbc8263dabc 1b3a8a7d1ceceaa459b3fd5640da26859df8d80b  (PR=3748  ,  Filename=provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=262e3cf5df2448bb6b532c0549c3d72daefe5a96) -->



|Nom| Commentaires|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 SP1 Enterprise sur Windows|R Services d’analytique avancée intégrées.|
|BYOL SQL Server 2016 SP1 Enterprise sur Windows Server |R Services d’analytique avancée intégrées. |
|Licence gratuite : Développeur SQL Server 2016 SP1 sur Windows Server 2016 |R Services d’analytique avancée intégrées. |
| Machine virtuelle de science des données - Windows 2012|Contient les outils courants pour la science des données, y compris Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, la distribution de Python de Anaconda, édition développeur de Julia Pro et Notebook blocs-notes pour R.|
| Machine virtuelle de science des données - 2016 de Windows|Inclut SQL Server 2016 Developer Edition, avec prise en charge pour l’analytique de R dans base de données.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Machine Learning Services avec prise en charge de langage Python et R.|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Machine Learning Services avec prise en charge de langage Python et R.|
| Licence de serveur SQL libre : Développeur SQL Server 2017 sur Windows Server|Machine Learning Services avec prise en charge de langage Python et R.|
| **Autres**| *** |
| Serveur uniquement SQL Server 2017 Enterprise d’apprentissage|Similaire à l’image de SQL Server 2016 Enterprise, mais contient la version autonome du serveur de Machine Learning de cœur ScaleR et des fonctionnalités à l’Opérationnalisation optimisé pour Windows, les environnements.|
| Serveur d’apprentissage pour Windows|Contient la version autonome de Machine Learning Server, avec les fonctionnalités à l’Opérationnalisation optimisées pour les environnements Windows.|



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-revoscalerrrevoscaler-overviewmd"></a>9. &nbsp;[RevoScaleR](r/revoscaler-overview.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_8) | [suivant](#TitleNum_10))

<!-- Source markdown line 18.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 92f2dfa2e75037a932415881c55d2fd37fc6847a c6e9f17f2df82447b18beff41769ae3ebfbed562  (PR=4150  ,  Filename=revoscaler-overview.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->




RevoScaleR est un ensemble de fonctions d’apprentissage machine, fourni par Microsoft, qui prend en charge pour la science des données à grande échelle.

+ Fonctions prennent en charge l’importation de données, de transformation de données, de synthèse, de visualisation et d’analyse.

+ _À l’échelle_ signifie que les opérations peuvent être exécutées sur des jeux de données très volumineux, en parallèle et distribuées sur des systèmes de fichiers. Algorithmes peuvent opérer sur des jeux de données qui ne tiennent pas dans la mémoire, à l’aide de segmentation et REASSEMBLAGE résultats une fois les opérations terminées.

+ RevoScaleR fournit de nombreuses améliorations sur les fonctions R open source. Il existe des fonctions RevoScaleR correspondant à la plupart des fonctions R plus populaires base. Les fonctions RevoScaleR sont signalées par un **rx** ou **Rx** préfixe pour les rendre plus faciles à identifier.

+ RevoScaleR sert à une plateforme pour la science des données distribuées. Par exemple, vous pouvez utiliser les contextes de calcul RevoScaleR et les transformations avec les algorithmes de pointe dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Vous pouvez également utiliser [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) pour exécuter les fonctions de base R en parallèle.

Pour obtenir des exemples de RevoScaleR en action, consultez les blogs :

+ [Créer et déployer un modèle de prévision à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Prédictions d’un million par seconde avec le serveur de Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Conseils de taxi prédiction à l’aide de MicrosoftML](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Optimisation des performances avec rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

**Obtention de RevoScaleR**




&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-enable-or-disable-r-package-management-for-sql-serverrr-package-how-to-enable-or-disablemd"></a>10. &nbsp;[Activer ou désactiver la gestion des packages R pour SQL Server](r/r-package-how-to-enable-or-disable.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_9) | [suivant](#TitleNum_11))

<!-- Source markdown line 60.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f846cd7d601459a95e694ada41e9fc5285f3de9 83a4a84adf47670c7fd4599f889f27ec3c219708  (PR=4150  ,  Filename=r-package-how-to-enable-or-disable.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    If you do not specify a user, the current security context is used.

3. Répétez la commande pour chaque base de données où les packages doivent être installés.

4.  Pour vérifier que les nouveaux rôles ont été créés avec succès, dans SQL Server Management Studio, cliquez sur la base de données, développez **sécurité**, développez **des rôles de base de données**.

    Vous pouvez également exécuter une requête sur sys.database_principals tels que les éléments suivants :

```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,
        pr.authentication_type_desc, pe.state_desc,
        pe.permission_name, s.name + '.' + o.name AS ObjectName
    FROM sys.database_principals AS pr
    JOIN sys.database_permissions AS pe
        ON pe.grantee_principal_id = pr.principal_id
    JOIN sys.objects AS o
        ON pe.major_id = o.object_id
    JOIN sys.schemas AS s
        ON o.schema_id = s.schema_id;
```

4.  Une fois que la fonctionnalité a été activée, tout utilisateur disposant des autorisations appropriées peut utiliser le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction T-SQL pour ajouter des packages. Pour obtenir un exemple de fonctionnement, consultez [installer des packages supplémentaires sur SQL Server](r/install-additional-r-packages-on-sql-server.md).

**<a name="bkmk_disable"></a>Désactiver la gestion des packages**




&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-set-up-a-data-science-client-for-use-with-sql-serverrset-up-a-data-science-clientmd"></a>11. &nbsp;[Configurer un client de science des données pour une utilisation avec SQL Server](r/set-up-a-data-science-client.md)

*Mise à jour : 2017-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_10) | [suivant](#TitleNum_12))

<!-- Source markdown line 52.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f674f5d329211e4c7d8dc464bd70f1cdef633350 8c65fc96c04f32d1e4777870774a11f9fd2ee219  (PR=3765  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



    For setup information, see [How to install R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

    To configure RTVS to use your Microsoft R client libraries, see [About Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    Même l’édition Community gratuite inclut la charge de science des données, qui installe des modèles de projet pour R, Python et F #.

    Télécharger Visual Studio à partir de [ce site](https://www.visualstudio.com/vs/).

+ RStudio

    Si vous préférez RStudio, vous devez effectuer des étapes supplémentaires pour pouvoir utiliser les bibliothèques RevoScaleR :

    - Installer le Client Microsoft R pour obtenir les packages requis et les bibliothèques.
    - Mettre à jour votre chemin d’accès de R pour utiliser le runtime de Microsoft R.

    Pour plus d’informations, consultez [R Client - configurer votre IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

**Configurez votre interface IDE**


+ Outils R pour Visual Studio

    Consultez [ce site](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) pour obtenir des exemples montrant comment générer et déboguer R projets à l’aide des outils R pour Visual Studio.

+ Visual Studio 2017

    Si vous installez le Client Microsoft R ou R Server **avant** vous installez Visual Studio, les bibliothèques R Server sont automatiquement détectés et utilisés pour votre chemin d’accès de la bibliothèque. Si vous n’avez pas installé les bibliothèques RevoScaleR, à partir de la **outils R** menu, sélectionnez **installer le Client R**.

**Exécuter R dans SQL Server**


Cet exemple utilise Visual Studio 2017 Community Edition, avec la charge de travail de science des données installé.

1. À partir de la **fichier** menu, sélectionnez **nouveau** , puis sélectionnez **projet**.

2. -Main volet contient une liste de modèles préinstallés. Cliquez sur **R**, puis sélectionnez **projet R**. Dans le **nom** , tapez `dbtest` et cliquez sur **OK**.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>12. &nbsp;[Configurer SQL Server Machine Learning Services (de-de base de données)](r/set-up-sql-server-r-services-in-database.md)

*Mise à jour : 2017-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_11) | [suivant](#TitleNum_13))

<!-- Source markdown line 111.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4d355f6494b417dd90dce3943e7176eaece7336e 20bddb8ffd4cf3774b812a7376c70b95ccc57e92  (PR=3980  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



   + Services Moteur de base de données
   + R Services (dans la base de données)

7. Lors de l’installation est terminée, redémarrez votre ordinateur.


**<a name="bkmk2017top"></a>Installer SQL Server 2017 Machine Learning Services (de-de base de données)**


> [!div class="checklist"]
> * Installer le moteur de base de données et l’apprentissage des fonctionnalités
> * Les étapes de post-installation requises : activer l’apprentissage et redémarrer
> * Les étapes de post-installation facultatives : ajouter des règles de pare-feu, d’ajouter des utilisateurs, de modifier ou de configurer des comptes de service, configurer un client de science des données distantes.

**Prise en main**

1. Exécutez.. ! NCLURE-NotShown--ssNoVersion--... /.. programme d’installation de /Includes/ssnoversion-MD.MD)].

2. Sur le **Installation** onglet, sélectionnez **nouvelle installation SQL Server autonome ou ajouter des fonctionnalités à une installation existante**.

     ! [Installer les Services de Machine Learning (In-Database)--media/2017setup-installation-page-mlsvcs.png « Démarrer l’installation du moteur de base de données avec Machine Learning Services »)

3. Sur le **sélection des fonctionnalités** , sélectionnez les options suivantes :

    + Sélectionnez **Services moteur de base de données**. Le moteur de base de données est requise dans chaque instance qui utilise l’apprentissage.

    + Sélectionnez **(de-de base de données) de Services d’apprentissage**. Cette option installe la prise en charge pour une utilisation dans base de données de R. Une fois que vous sélectionnez cette option, vous pouvez sélectionner la langue d’apprentissage. Vous pouvez sélectionner uniquement les R, ou vous pouvez ajouter à la fois R et Python.

    ! [Fonctionnalité de machine Learning Services selection--media/2017setup-features-page-mls-rpy.png », sélectionnez ces fonctionnalités pour R Services dans-base de données »)

    Si vous ne sélectionnez pas les options de langage Python ou R, l’Assistant Installation installe uniquement l’infrastructure d’extensibilité, qui inclut SQL Server approuvée Launchpad et n’installe pas les composants spécifiques à une langue.  En règle générale, nous vous recommandons d’installer au moins une langue pour commencer. Toutefois, vous pouvez utiliser cette option si vous envisagez d’utiliser immédiatement le processus de liaison pour mettre à niveau les composants d’apprentissage automatique. Pour plus d’informations, consultez [SqlBindR de l’utiliser pour mettre à niveau une instance de R Services--use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



&nbsp;

&nbsp;

---

<a name="TitleNum_13"/>

### <a name="13-nbsp-unattended-installation-of-machine-learning-services-in-databaserunattended-installs-of-sql-server-r-servicesmd"></a>13. &nbsp;[Une installation sans assistance de Machine Learning Services (de-de base de données)](r/unattended-installs-of-sql-server-r-services.md)

*Mise à jour : 2017-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_12) | [suivant](#TitleNum_14))

<!-- Source markdown line 75.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ad203c90adff3f515b5f16472fad9753be7a421d 6925a9276bcd4a80babc7504de50400f1a5a2940  (PR=3765  ,  Filename=unattended-installs-of-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2017 Machine Services (de-de base de données) avec le langage Python ajouté.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Notez les indicateurs nécessaires pour Python dans SQL Server 2017 :

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

**Installer R et Python sur une instance nommée**


L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2017 Machine Services (de-de base de données) sur une instance nommée. Langues R et Python sont ajoutés.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

**<a name="OldInstall"></a>Installation de ligne de commande pour SQL Server 2016**


L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2016 avec le langage R ajouté.



&nbsp;

&nbsp;

---

<a name="TitleNum_14"/>

### <a name="14-nbsp-step-3-explore-and-visualize-the-datatutorialssqldev-py3-explore-and-visualize-the-datamd"></a>14. &nbsp;[Étape 3 : Explorer et visualiser les données](tutorials/sqldev-py3-explore-and-visualize-the-data.md)

*Mise à jour : 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_13))

<!-- Source markdown line 66.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 47edcfbd8da7cf1ea1ad03a05f86d3cd26014827 674a7c7d0e8290fc91970ed2aeda3b97d5165d75  (PR=4150  ,  Filename=sqldev-py3-explore-and-visualize-the-data.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    Class 4: `tip_amount` > $20

**Créer des graphiques à l’aide de Python dans T-SQL**


Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Étant donné que la visualisation est un outil puissant permettant de comprendre la distribution des données et des valeurs hors norme, Python fournit de nombreux packages de visualisation de données. Le **matplotlib** module est une des bibliothèques de visualisation les plus populaires et inclut de nombreuses fonctions pour la création d’histogrammes, nuages de points, des graphiques de zone et autres graphiques d’exploration de données.

Dans cette section, vous allez apprendre à travailler avec des graphiques à l’aide de procédures stockées. Au lieu d’ouvrir l’image sur le serveur, vous stockez l’objet Python `plot` en tant que **varbinary** données, puis écrire que dans un fichier qui peut être partagé ou affichées ailleurs.

**Créer un graphique en tant que données varbinary**


Le **revoscalepy** module inclus avec SQL Server 2017 Machine Learning Services prend en charge des fonctionnalités similaires à celles de la **RevoScaleR** package de R.  Cet exemple utilise l’équivalent de Python de `rxHistogram` pour tracer un histogramme basé sur des données d’un.. ! NCLURE-NotShown--tsql--... /.. requête /Includes/TSQL-MD.MD)].

La procédure stockée retourne une Python sérialisée `figure` objet sous forme de flux de **varbinary** données. Vous ne pouvez pas afficher directement les données binaires, mais vous pouvez utiliser du code Python à désérialiser et afficher les chiffres sur le client et puis enregistrez le fichier image sur un ordinateur client.

1. Créez la procédure stockée _SerializePlots_, si le script PowerShell s’est pas déjà fait.

    - La variable `@query` définit le texte de requête `SELECT tipped FROM nyctaxi_sample`, qui est passé au bloc de code Python comme argument à la variable d’entrée du script, `@input_data_1`.
    - Le script Python est relativement simple : **matplotlib** `figure` objets sont utilisés pour effectuer le traçage de l’histogramme et à nuages de points, et ces objets sont sérialisés puis à l’aide de la `pickle` bibliothèque.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 14) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (21 + 0) : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (5 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 0) : **Assistant Migration SQL Server (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


