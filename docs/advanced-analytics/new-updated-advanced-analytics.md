---
title: Mis à jour - Advanced Analytique des documents de SQL Server | Documents Microsoft
description: Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié dans, pour avancée d’Analytique pour Microsoft SQL Server.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: advanced-analytics
ms.date: 02/03/2018
ms.openlocfilehash: fa0c25c193ea2815773ed9d08a50194d825f0a8a
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nouveaux et mis à jour récemment : Advanced Analytique pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Période des mises à jour :* &nbsp; **03-12-2017** &nbsp; au &nbsp; **03-02-2018**
- *Zone de sujet :* &nbsp; **avancées d’Analytique pour SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Installer de nouveaux packages Python sur SQL Server](python/install-additional-python-packages-on-sql-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Problèmes connus dans les Services de Machine Learning](#TitleNum_1)
2. [Conversion de code R pour l’exécution de bases de données](#TitleNum_2)
3. [Déterminer quels packages R sont installés sur SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp; [Problèmes connus dans les Services de Machine Learning](known-issues-for-sql-server-machine-learning-services.md)

*Mise à jour : 2018-02-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 163.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c6f46adcf795c43f818120b88407a3a89304cb27 c781562605f5cd77f6c43bfe5e89810cb72ceae0  (PR=4789  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=386bfb688843bac7fa4d83dc1cfef94dd19db110) -->



Pour les autres problèmes connus qui peuvent affecter des solutions R, consultez le [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) site.

**Accès refusé avertissement lors de l’exécution des scripts R sur SQL Server dans un emplacement non par défaut**


Si l’instance de SQL Server a été installé à un emplacement non définis par défaut, comme à l’extérieur de la `Program Files` dossier, l’avertissement ACCESS_DENIED est déclenché lorsque vous essayez d’exécuter des scripts qui installent un package. Par exemple :

> *NormalizePath(path.expand(path), winslash, mustWork) : chemin d’accès [2] = « ~ExternalLibraries/R/8/1 » : l’accès est refusé.*

La raison est qu’une fonction R tente de lire le chemin d’accès et échoue si le groupe d’utilisateurs intégrés **SQLRUserGroup**, n’a pas accès en lecture. L’avertissement est générée ne bloque pas l’exécution du script R en cours, mais l’avertissement peut se répéter à plusieurs reprises à chaque fois que l’utilisateur exécute tous les autres scripts.

Si vous avez installé SQL Server à l’emplacement par défaut, cette erreur ne se produit pas, car tous les utilisateurs Windows ont des autorisations de lecture sur le `Program Files` dossier.

Ce problème sera résolu dans une version de service à venir. Pour résoudre ce problème, fournissez le groupe, **SQLRUserGroup**, avec accès en lecture pour tous les dossiers parents de `ExternalLibraries`.

**Erreur de sérialisation entre les versions anciennes et nouvelles de RevoScaleR**


Lorsque vous passez d’un modèle à l’aide d’un format sérialisé à une instance distante de SQL Server, vous pouvez obtenir l’erreur :

> *Erreur dans memDecompress (données, type = décompresser) une erreur interne -3 dans memDecompress(2).*

Cette erreur est générée si vous avez enregistré le modèle à l’aide d’une version récente de la fonction de sérialisation, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), mais l’instance de SQL Server où vous désérialisez le modèle a une version antérieure des APIs RevoScaleR, à partir de SQL Serveur 2017 CU2 ou version antérieure.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-converting-r-code-for-execution-in-databaserconverting-r-code-for-use-in-sql-servermd"></a>2. &nbsp; [Conversion de code R pour l’exécution de bases de données](r/converting-r-code-for-use-in-sql-server.md)

*Mise à jour : 2018-01-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 136.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a1d156fac1af5813ef75965071686b177e2aede7 fc8beff0aa0d7ea298e493b90984875e81e9143e  (PR=4493  ,  Filename=converting-r-code-for-use-in-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f486d12078a45c87b0fcf52270b904ca7b0c7fc8) -->



**Package de votre code R dans une procédure stockée**

+ Si votre code est relativement simple, vous pouvez l’incorporer dans une fonction définie par l’utilisateur de T-SQL sans modification, comme décrit dans ces exemples :

    + [Créer une fonction R qui s’exécute dans rxExec](r/../tutorials/deepdive-create-a-simple-simulation.md)
    + [Ingénierie de fonctionnalité à l’aide de T-SQL et R](r/../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Si le code est plus complexe, utilisez le package R **sqlrutils** à convertir votre code. Ce package est conçu pour aider les utilisateurs expérimentés de R à écrire du code de procédure stockée correct.

    La première étape consiste à réécrire votre code R en tant qu’une seule fonction avec clairement des entrées et sorties.

    Ensuite, utilisez le **sqlrutils** package pour générer l’entrée et les sorties dans le format correct. Le **sqlrutils** package génère le code de procédure stockée complète pour vous et peuvent également inscrire la procédure stockée dans la base de données.

    Pour plus d’informations et d’exemples, consultez [SqlRUtils](r/../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).

**Intégrer à d’autres flux de travail**

+ Tirer parti des outils de T-SQL et les processus ETL. Effectuer une ingénierie de fonctionnalité, d’extraction de fonctionnalité et de nettoyage des données à l’avance en tant que partie du flux de travail de données.

    Lorsque vous travaillez dans un environnement de développement R dédié telles que R Tools pour Visual Studio ou RStudio, vous pouvez peut extraire des données sur votre ordinateur, analyser les données de manière itérative et ensuite écrire ou afficher les résultats.

    Toutefois, lorsque le code de R autonome est migré vers SQL Server, une grande partie de ce processus peut être simplifiée ou déléguée à d’autres outils de SQL Server.

+ Utiliser des stratégies de visualisation sécurisée, asynchrone.

    Fréquence à laquelle les utilisateurs de SQL Server ne peut pas accéder aux fichiers sur le serveur et outils clients SQL ne gèrent en général pas le périphérique d’affichage R. Si vous générez des graphiques ou autres graphiques dans le cadre de la solution, envisagez d’exportation les graphiques en tant que données binaires et de l’enregistrement dans une table ou de l’écriture.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp; [Déterminer quels packages R sont installés sur SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Mise à jour : 2018-01-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2))

<!-- Source markdown line 78.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9a065066398843a4bed318fa46d4982d712915a9 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f  (PR=4715  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=9e6a029456f4a8daddb396bc45d7874a43a47b45) -->




**Obtenir la version et l’emplacement de la bibliothèque**


L’exemple suivant obtient l’emplacement de la bibliothèque de RevoScaleR dans le contexte de calcul local et la version du package.

```
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

**Déterminer le chemin d’accès de bibliothèque utilisé par SQL Server**


Si vous avez mis à niveau les composants à l’aide de la liaison d’apprentissage automatique, le chemin d’accès à la bibliothèque R peut changer. Dans ce cas, précédentes raccourcis vers les outils R peuvent faire référence à une version antérieure. Pour être sûr de la version du chemin d’accès et le package utilisé par SQL Server, vous pouvez exécuter une commande telle que les éléments suivants :

```
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Résultats**

```
STDOUT message(s) from external script:
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Domaines *avec* des articles nouveaux ou mis à jour récemment


- [Nouveaux + Mis à jour (1 + 3) :&nbsp; **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (12 + 1) :**Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (6 + 2) :&nbsp; **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (15 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (2 + 9) :&nbsp; **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) :&nbsp; **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Domaines *sans* article nouveau ou mis à jour récemment


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveau + mis à jour (0 0 +) : **ActiveX Data Objects (ADO) pour SQL** documents](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../samples/new-updated-samples.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)


