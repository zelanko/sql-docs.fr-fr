---
title: Mis à jour - Advanced Analytique des documents de SQL Server | Documents Microsoft
description: Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié dans, pour avancée d’Analytique pour Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 04/28/2018
ms.openlocfilehash: bbce32579b54647e167c25d2708a80027ae0e678
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nouveaux et mis à jour récemment : Advanced Analytique pour SQL Server



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2018-02-03** &nbsp; - à - &nbsp; **2018-04-28**
- *Zone de sujet :* &nbsp; **avancées d’Analytique pour SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Installer SQL Server 2017 d’apprentissage Services (de-de base de données) sur Windows](install/sql-machine-learning-services-windows-install.md)
2. [Installer SQL Server 2017 d’apprentissage Server (autonome) sur Windows](install/sql-machine-learning-standalone-windows-install.md)
3. [Installer les composants de SQL Server machine learning à partir de la ligne de commande](install/sql-ml-component-commandline-install.md)
4. [Installer les composants sans accès à internet d’apprentissage automatique SQL Server](install/sql-ml-component-install-without-internet-access.md)
5. [Installer SQL Server 2016 R Services (de-de base de données)](install/sql-r-services-windows-install.md)
6. [Installer SQL Server 2016 R Server (autonome)](install/sql-r-standalone-windows-install.md)
7. [Définir les outils clients pour une utilisation avec SQL Server Machine Learning Python](python/setup-python-client-tools-sql.md)
8. [Utiliser le modèle de Python dans SQL pour l’apprentissage et de calcul de score](tutorials/train-score-using-python-in-tsql.md)
9. [Retour à la ligne de code Python dans une procédure stockée](tutorials/wrap-python-in-tsql-stored-procedure.md)
10. [Qu’est-ce que SQL Server Machine Learning Services ?](what-is-sql-server-machine-learning.md)
11. [Événements étendus pour la surveillance d’instructions PREDICT](xe-event-predict-tsql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Affichage R ou des packages Python installées sur SQL Server](#TitleNum_1)
2. [Installer dont l’apprentissage d’apprentissage des modèles sur SQL Server](#TitleNum_2)
3. [Configurer un client de science des données pour le développement de R sur SQL Server](#TitleNum_3)
4. [Apprentissage et R Services (de-de base de données) de l’ordinateur SQL Server](#TitleNum_4)
5. [Exécutez Python à l’aide de T-SQL](#TitleNum_5)
6. [Utiliser Python avec revoscalepy pour créer un modèle](#TitleNum_6)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-viewing-r-or-python-packages-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>1. &nbsp; [Affichage R ou des packages Python installées sur SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Mise à jour : 2018-04-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 208.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f ec6859ac91b27539dc36f21aec82c99937c0187a  (PR=5610  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f1f96a990644c0d6cfa5a1d88ccee959cab6c2b2) -->



**Python**


Cet exemple retourne la liste des dossiers inclus dans les Python `sys.path` variable. La liste inclut le répertoire actif et le chemin d’accès de la bibliothèque standard.

```
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Résultats**

```
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Pour plus d’informations sur la variable `sys.path` et la façon dont il est utilisé pour définir le chemin de recherche de l’interpréteur de modules, consultez la [documentation de Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-install-pre-trained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>2. &nbsp; [Installer dont l’apprentissage d’apprentissage des modèles sur SQL Server](r/install-pretrained-models-sql-server.md)

*Mise à jour : 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 140.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 aa03623d819750d4919feb7910b07ec1875bb509 7382228fa68b04b500a5fde73c29995e12aa20ac  (PR=5504  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



1. Lancer l’installation basée sur Windows distincte pour une [R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server) ou [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Sélectionnez les langues que vous souhaitez mettre à jour, puis sélectionnez le **Pre-trained modèles** option.

    > [!TIP]
    > Si vous avez précédemment exécuté le programme d’installation pour mettre à jour de R Server (autonome) et que vous souhaitez simplement ajouter les modèles dont l’apprentissage, laissez toutes les sélections précédentes **étant**, puis sélectionnez simplement la version antérieure de **-apprentissage des modèles** option . **Ne le faites pas** désélectionner toutes les options précédemment sélectionnées ; si vous procédez ainsi, le programme d’installation supprime les composants.

    Nous vous recommandons d’accepter les paramètres par défaut pour les emplacements du modèle.

3. Cliquez sur **Continuer**.

4. Acceptez toutes les invites, y compris les contrats de licence.

Une fois l’installation terminée, vous devez effectuer quelques étapes supplémentaires pour inscrire les modèles dont l’apprentissage.

1. Ouvrez une invite de commandes Windows **en tant qu’administrateur**.

2. Accédez au dossier d’installation d’amorçage pour R Server (autonome), qui contient également le programme d’installation de Microsoft R.

3. Exécutez `RSetup.exe` et indiquer le composant à installer, la version et le dossier contenant les fichiers de source de modèle, à l’aide de cette syntaxe :

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    Les valeurs suivantes sont prises en charge pour le paramètre de version :



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-set-up-a-data-science-client-for-r-development-on-sql-serverrset-up-a-data-science-clientmd"></a>3. &nbsp; [Configurer un client de science des données pour le développement de R sur SQL Server](r/set-up-a-data-science-client.md)

*Mise à jour : 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 39.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0583f8febcedc5dc2e14ca1a8073ca204ca37987 3d50ad8f35f2985944741a9b2211a461df2c13e4  (PR=5504  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



**Outils R**


Lorsque vous installez R avec SQL Server, vous obtenez les mêmes outils R qui sont installés avec les **base** installation de R, tels que RGui, Rterm et ainsi de suite. Par conséquent techniquement, vous devez tous les outils dont vous avez besoin pour développer et tester le code R.

Les outils R standards suivants sont inclus dans un *installation de base* de R et par conséquent, sont installés par défaut.

+ **RTerm**: un terminal de ligne de commande pour l’exécution des scripts R

+ **RGui.exe** : éditeur interactif simple pour R. Les arguments de ligne de commande sont les mêmes pour RGui.exe et RTerm.

+ **RScript** : outil en ligne de commande pour l’exécution de scripts R en mode batch.

Pour rechercher ces outils, déterminez la bibliothèque R qui a été installée lorsque vous installez SQL Server ou la fonctionnalité d’apprentissage autonome. Par exemple, dans une installation par défaut, les outils R sont situés dans ces dossiers :

+ SQL Server 2016 R Services : `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Microsoft R Server autonome : `~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ SQL Server 2017 apprentissage Services : `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Apprentissage Server (autonome) : `~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Si vous avez besoin d’aide avec les outils R, ouvrez simplement **RGui**, cliquez sur **aide**, puis sélectionnez une des options

**Microsoft R Client**


Microsoft R Client est un téléchargement gratuit qui vous permet d’accéder aux packages RevoScaleR à des fins de développement. En installant le Client de R, vous pouvez créer des solutions R qui peuvent être exécutées dans tous les contextes de calcul pris en charge, y compris analytique dans base de données de SQL Server et traitements distribués R sur Hadoop, Spark ou Linux à l’aide de la Machine Learning Server.

Si vous avez déjà installé un autre environnement de développement R, tels que RStudio, veillez à reconfigurer l’environnement pour utiliser les bibliothèques et les exécutables fournis par le Client de Microsoft R. En procédant comme vous pouvez donc utiliser toutes les fonctionnalités du package RevoScaleR, bien que les performances seront en trouvent limitées.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sql-server-machine-learning-and-r-services-in-databasersql-server-r-servicesmd"></a>4. &nbsp; [Apprentissage et R Services (de-de base de données) de l’ordinateur SQL Server](r/sql-server-r-services.md)

*Mise à jour : 2018-04-12* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3) | [suivant](#TitleNum_5))

<!-- Source markdown line 83.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b1a95a7f6d391a518762eb271e8ea7e0d684d403 7fbfabf62917e03e2bcb99d297e1c9d0f0604440  (PR=5504  ,  Filename=sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f34765240b79a44167ca2af90f97a0fdd47c41d2) -->



Choisir le meilleur langage pour la tâche. R est idéal pour effectuer des calculs statistiques qui sont difficiles à implémenter à l’aide de SQL. Pour les opérations basées sur les données, exploiter la puissance du *{inclus-contenu-passe-ici}* pour optimiser les performances. Utilisez le moteur de base de données en mémoire pour effectuer des calculs très rapides sur les colonnes.

**Étape 4 : Optimiser votre solution**


Lorsque le modèle est prêt à l’échelle sur les données d’entreprise, le chercheur de données fonctionne souvent le développeur de base de données ou SQL pour optimiser les processus tels que :

+ Ingénierie des caractéristiques
+ Intégrer les données et la transformation des données
+ Calcul de score

En règle générale, les chercheurs de données à l’aide de R ont des problèmes de performances et d’évolutivité, surtout lorsque vous utilisez le jeu de données volumineux. C’est parce que l’implémentation common runtime est monothread et peut accepter uniquement les jeux de données qui entrent dans la mémoire disponible sur l’ordinateur local. L’intégration avec les Services de SQl Server Machine Learning offre plusieurs fonctionnalités pour de meilleures performances, davantage de données :

+ **RevoScaleR**: package R ce contient des implémentations de certaines fonctions R plus populaires, repensées pour fournir un parallélisme et mise à l’échelle. Le package comprend également des fonctions qui améliorent encore davantage les performances et l’échelle en envoyant des calculs à la *{inclus-contenu-passe-ici}* ordinateur, ce qui est généralement beaucoup plus de mémoire et de puissance de calcul.

+ **revoscalepy**. Cette bibliothèque Python, disponible dans SQL Server 2017, implémente les fonctions les plus populaires dans RevoScaleR, telles que les contextes de calcul à distance et de nombreux algorithmes qui prennent en charge de traitement distribué.

**Ressources**

+ [Étude de cas de performances]
+ [R et l’optimisation de données]

**Étape 5 : Déployer et utiliser**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-run-python-using-t-sqltutorialsrun-python-using-t-sqlmd"></a>5. &nbsp; [Exécutez Python à l’aide de T-SQL](tutorials/run-python-using-t-sql.md)

*Mise à jour : 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_4) | [suivant](#TitleNum_6))

<!-- Source markdown line 306.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bde8c6476df259d225847c08224cefd02f3529d5 cad56997abe7928b588ac4a0302384c5edc1ede5  (PR=5497  ,  Filename=run-python-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



2. Notez que les valeurs d’index ne sont pas de sortie, même si vous utilisez l’index pour obtenir des valeurs spécifiques à partir de la data.frame.

    **Résultats**

    |ResultValue|
    |------|
    |0.5|
    |2|

**Valeurs de sortie en data.frame à l’aide d’un index**


Nous allons voir comment la conversion en un data.frame fonctionne avec nos deux séries qui contient les résultats d’opérations mathématiques simples. La première a un index de valeurs séquentielles générées par Python. La seconde utilise un index arbitraire de valeurs de chaîne.

1. Cet exemple obtient une valeur de la série qui utilise un index d’entiers.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

N’oubliez pas que l’index généré automatiquement commence à 0. Essayez d’utiliser une valeur hors limites index et observez le résultat.

2. Maintenant, nous allons apprendre une valeur unique à partir d’autres trame de données qui a un index de chaîne.

```
    EXECUTE sp_execute_external_script
    @language = N'Python',
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
```

**Résultats**

|ResultValue|
|------|
|0.5|

Si vous essayez d’utiliser un index numérique pour obtenir une valeur à partir de cette série, vous obtenez une erreur.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>6. &nbsp; [Utiliser Python avec revoscalepy pour créer un modèle](tutorials/use-python-revoscalepy-to-create-model.md)

*Mise à jour : 2018-04-11* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_5))

<!-- Source markdown line 22.  ms.author= heidist.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5b642b391ca571412c30c8470875d3d4d3c57246 bd83387eb8a1076a1396bbd48dca12872843aa2f  (PR=5497  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=86c4e1879c5914676b9da384ab101b50b4a63bf1) -->



Si vous avez installé une version préliminaire de SQL Server 2017, vous devez mettre à jour au moins la version RTM. Les versions ultérieures de service ont continué à développer et à améliorer les fonctionnalités de Python. Certaines fonctionnalités de ce didacticiel peut ne pas fonctionnent dans les premières versions préliminaires.

+ Cet exemple utilise un environnement Python prédéfini, nommé `PYTEST_SQL_SERVER`. L’environnement a été configuré pour qu’il contienne **revoscalepy** et d’autres bibliothèques requises.

    Si vous n’avez pas d’un environnement configuré pour s’exécuter Python, vous devez le faire séparément. En savoir plus sur la création ou de modifier des environnements Python est hors de portée pour ce didacticiel. Pour plus d’informations sur la façon de configurer un client Python qui contient les bibliothèques corrects, consultez [client de l’installation de Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter) et [Python lien outils](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools).

**Revoscalepy et contextes de calcul à distance**


Cet exemple illustre le processus de création d’un modèle de Python dans une distance _contexte de calcul_, qui vous permet de vous travaillez à partir d’un client, mais que vous choisissez un environnement distant, telles que SQL Server, Spark ou Machine Learning Server, où le les opérations sont effectuées. L’utilisation de contextes de calcul rend plus faciles à écrire du code une fois et déployez-le sur n’importe quel environnement pris en charge.

Pour exécuter le code Python dans SQL Server requiert le **revoscalepy** package. C’est un package Python spécial fourni par Microsoft, similaire à la **RevoScaleR** package pour le langage R. Le **revoscalepy** package prend en charge la création de contextes de calcul et fournit l’infrastructure pour le transfert des données et des modèles entre une station de travail locale et un serveur distant. Le **revoscalepy** de fonction qui prend en charge l’exécution de code de la base de données est [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver).







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Domaines *avec* des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (11 + 6) : &nbsp; &nbsp; **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (18 + 0) : &nbsp; &nbsp; **Analysis Services pour SQL** documents](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (218 + 14) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (14 + 0) : &nbsp; &nbsp; **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (3 + 2) : &nbsp; &nbsp; **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (3 + 3) : &nbsp; &nbsp; **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (7 + 10) : &nbsp; &nbsp; **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (0 + 2) : &nbsp; &nbsp; **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (1 + 3) : &nbsp; &nbsp; **SQL opérations Studio** documents](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveau + mis à jour (2 + 3) : &nbsp; &nbsp; **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (1 + 1) : &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (5 + 2) : &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 2) : &nbsp; &nbsp; **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)
- [Nouveau + mis à jour (1 + 1) : &nbsp; &nbsp; **Tools pour SQL** documents](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Domaines *sans* article nouveau ou mis à jour récemment

- [Nouveau + mis à jour (0 0 +) : **système de plateforme d’Analytique pour SQL** documents](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (0 0 +) : **PowerShell pour SQL** documents](../powershell/new-updated-powershell.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../samples/new-updated-samples.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)

