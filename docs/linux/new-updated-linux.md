---
title: "Mise à jour - SQL Server sur Linux docs | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour Microsoft SQL Server sur Linux."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: sql-linux,UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: 
ms.date: 02/03/2018
ms.openlocfilehash: 827399587a8147c59caf6bf31bf8b10f10c83211
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nouveau et récemment mis à jour : SQL Server sur Linux docs



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-12-03** &nbsp; - à - &nbsp; **2018-02-03**
- *Zone de sujet :* &nbsp; **Microsoft SQL Server sur Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Configurer les sous-réseaux de plusieurs groupes de disponibilité AlwaysOn et les instances de cluster de basculement](sql-server-linux-configure-multiple-subnet.md)
2. [Créer et configurer un groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-create-availability-group.md)
3. [Déployer un cluster STIMULATEUR pour SQL Server sur Linux](sql-server-linux-deploy-pacemaker-cluster.md)
4. [SQL Server sur Linux Forum aux Questions (FAQ)](sql-server-linux-faq.md)
5. [Principes fondamentaux de disponibilité de SQL Server pour les déploiements de Linux](sql-server-linux-ha-basics.md)
6. [Configurer un conteneur de SQL Server dans Kubernetes pour la haute disponibilité](tutorial-sql-server-containers-kubernetes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Toujours sur les groupes de disponibilité sur Linux](#TitleNum_1)
2. [Extraire, transformer et charger des données sur Linux avec SSIS](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-always-on-availability-groups-on-linuxsql-server-linux-availability-group-overviewmd"></a>1. &nbsp;[Toujours sur les groupes de disponibilité sur Linux](sql-server-linux-availability-group-overview.md)

*Mise à jour : 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 85.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 85685bc8ad3528aa26ca3f2bba7b0112808ad6f9 51aff6e55104c8f775d2b4f4461e44f689a9ee6b  (PR=4768  ,  Filename=sql-server-linux-availability-group-overview.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



Le basculement automatique d’un groupe de disponibilité est possible lorsque les conditions suivantes sont remplies :

-   Le serveur principal et le réplica secondaire sont définies sur le déplacement des données synchrone.
-   La base de données secondaire a un état de synchronisation (sans synchronisation), ce qui signifie que les deux sont sur le même point de données.
-   Le type de cluster est défini en mode externe. Le basculement automatique n’est pas possible avec un type de cluster None.
-   Le `sequence_number` le réplica secondaire qui deviendra le réplica principal a le numéro de séquence plus élevé : en d’autres termes, le réplica secondaire `sequence_number` correspond à celui du réplica principal d’origine.

Si ces conditions sont réunies et que le serveur qui héberge le réplica principal échoue, le groupe de disponibilité changent de propriété vers un réplica synchrone. Le comportement de réplicas synchrones (de laquelle il peut y avoir trois total : un serveur principal et deux réplicas secondaires) peuvent également être gérées par `required_synchronized_secondaries_to_commit`. Cela fonctionne avec les groupes de disponibilité de Windows et Linux, mais il est configuré complètement différemment. Sur Linux, la valeur est configurée automatiquement par le cluster sur la ressource de groupe de disponibilité lui-même.

Quorum et le réplica de configuration uniquement


Nouveau dans 2017 du serveur SQL à partir de CU1 est également un réplica de configuration. STIMULATEUR étant différent de celui d’un cluster WSFC, en particulier lorsqu’il s’agit de quorum et en demandant STONITH, seulement une configuration de deux nœuds ne fonctionnera pas lorsqu’il s’agit d’un groupe de disponibilité. Pour une instance de cluster, les mécanismes de quorum fournis par STIMULATEUR peuvent être précis, car tous les arbitrage de basculement FCI se produit au niveau du cluster. Pour un groupe de disponibilité, arbitrage sous Linux se produit dans SQL Server, où sont stockées toutes les métadonnées. Il s’agit là le réplica de configuration entre en jeu.

Sans quoi, un troisième nœud et au moins un réplica synchronisé est requis. Cela ne fonctionne pas pour SQL Server Standard, car il ne peut comporter deux réplicas qui participent à un groupe de disponibilité. Le réplica de configuration stocke la configuration du groupe de disponibilité dans la base de données master, identique à celui des autres réplicas dans la configuration du groupe de disponibilité. Le réplica de configuration n’a pas de bases de données utilisateur participant dans le groupe de disponibilité. Les données de configuration sont envoyées de façon synchrone à partir du principal. Ces données de configuration sont ensuite utilisées pendant les basculements, qu’ils soient automatique ou manuelle.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-extract-transform-and-load-data-on-linux-with-ssissql-server-linux-migrate-ssismd"></a>2. &nbsp;[Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

*Mise à jour : 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1))

<!-- Source markdown line 50.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9bba002ae3955ebb8376c7c85b7ec1ac8c706073 1533a8e0bfe553e5404de79129119b3f93185ee9  (PR=4768  ,  Filename=sql-server-linux-migrate-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Spécifiez le `/de[crypt]` option pour entrer le mot de passe interactivement, comme indiqué dans l’exemple suivant :

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de

    Enter decryption password:
    ```

3.  Spécifiez le `/de` permet de fournir le mot de passe sur la ligne de commande, comme indiqué dans l’exemple suivant. Cette méthode n’est pas recommandée, car elle stocke le mot de passe de déchiffrement avec la commande dans l’historique des commandes.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test

    Warning: Using /De[crypt] <password> may store decryption password in command history.

    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

Conception de packages


**Se connecter aux sources de données ODBC**. SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS permet les connexions ODBC sur Linux. Cette fonctionnalité a été testée avec les pilotes ODBC MySQL sur le serveur SQL Server, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Zones de sujet qui *faire* ont nouveaux ou récemment mis à jour articles


- [Nouveau + mis à jour (1 + 3) :&nbsp; **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **système de plateforme d’Analytique pour SQL** documents](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (12 + 1) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (6 + 2) :&nbsp; **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (15 + 0) : **PowerShell pour SQL** documents](../powershell/new-updated-powershell.md)
- [Nouveau + mis à jour (2 + 9) :&nbsp; **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **SQL opérations Studio** documents](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 2) :&nbsp; **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Zones de font l’objet *pas* ont tous nouveaux ou récemment mis à jour articles


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveau + mis à jour (0 0 +) : **ActiveX Data Objects (ADO) pour SQL** documents](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)


