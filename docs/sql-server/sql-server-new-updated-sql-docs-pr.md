---
title: "Mise à jour - documentation de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 7fba3b05943b93c0a2c0e76c2d0d5f2696a48d1c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/25/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Nouveau et récemment mis à jour : documentation de SQL Server



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-05-01** &nbsp; - à - &nbsp; **2017-05-23**
- *Zone de sujet :* &nbsp; **SQL Server**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1. &nbsp;[Notes de mise à jour de SQL Server 2017](sql-server-2017-release-notes.md)

*Updated: 2017-05-17* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 28.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 84e7a2a49f2893d49380db1ad75695d9a4fd59b2 27a145ad30c10fd667f926d2e092b88c0ba586c5 -->



**SQL Server CTP 2017 2.1 (mai 2017)**

**Documentation (préliminaire CTP 2.1)**

- **Impact sur le problème et le client :** Documentation pour [ ! INCLUDE [ssSQLv14_md--... /Includes/sssqlv14-MD.MD)] est limité et le contenu est inclus dans le [ ! INCLUDE [ssSQL15_md--... ensemble de documentation /Includes/sssql15-MD.MD)].  Le contenu des articles spécifiques à [ ! INCLUDE [ssSQLv14_md--... /Includes/sssqlv14-MD.MD)] est notée avec **s’applique à**. 
- **Impact sur le problème et le client :** aucun contenu hors connexion n’est disponible pour [ ! INCLUDE [ssSQLv14_md--... /Includes/sssqlv14-MD.MD)].

**SQL Server Reporting Services (CTP 2.1)**


- **Impact sur le problème et le client :** si vous disposez de SQL Server Reporting Services et Power BI serveur de rapports sur le même ordinateur et désinstaller un d’eux, vous ne serez n’est plus en mesure de se connecter au serveur de rapports avec le Gestionnaire de Configuration de Report Server restants.
- **Solution de contournement** pour contourner ce problème, vous devez effectuer les opérations suivantes après la désinstallation d’un des serveurs.

    1. Lancez une invite de commandes en mode administrateur.
    2. Accédez au répertoire où est installé le serveur de rapports restants.

        *Emplacement par défaut pour le serveur de rapports Power BI : serveur de rapports de C:\Program Files\Microsoft Power BI*

        *Emplacement par défaut pour SQL Server Reporting Services : C:\Program Files\Microsoft SQL Server Reporting Services*

    3. Puis accédez au dossier suivant. Il s’agit de *SSRS* ou *PBIRS* selon ce qui est restant.
    4. Accédez au dossier WMI.
    5. Exécutez la commande suivante :

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        Vous pouvez ignorer l’erreur suivante, si elle s’affiche.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

**TSqlLanguageService.msi (CTP 2.1)**


- **Impact sur le problème et le client :** après l’installation sur un ordinateur qui possède une version 2016 de *TSqlLanguageService.msi* (via le programme d’installation de SQL ou installé en tant que composant redistribuable autonome) les versions v13.* (SQL 2016) de *Microsoft.SqlServer.Management.SqlParser.dll* et *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* sont supprimés. Toutes les applications qui ont une dépendance sur les versions de 2016 de ces assemblys puis cesse de fonctionner, ce qui donne une erreur similaire à : *erreur : Impossible de charger le fichier ou l’assembly ' Microsoft.SqlServer.Management.SqlParser, Version = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91' ou une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.*




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-what39s-new-in-sql-server-2017what-s-new-in-sql-server-2017md"></a>2. &nbsp;[Quel &#39; s de SQL Server 2017](what-s-new-in-sql-server-2017.md)

*Updated: 2017-05-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 31.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b3e965f62414af06d42f88497958a4bca67befce 82ad09ae9a917f26db3e2210b5cf89585e0e4c4e -->



**Nouveautés de SQL Server CTP 2017 2.1 (mai 2017)**

** Moteur de base de données SQL Server **

- Un nouveau DMF [sys.dm_db_log_stats--... / relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), est introduit pour exposer les attributs au niveau de synthèses et des informations sur les fichiers journaux des transactions ; permet de surveiller l’intégrité du journal des transactions.  
- Cette version CTP contient des correctifs de bogues et améliorations des performances pour le moteur de base de données.
- Pour une liste détaillée des 2017 améliorations CTP dans les précédentes versions CTP, consultez [Nouveautés de SQL Server 2017 (moteur de base de données)--... / database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

**SQL Server Reporting Services (SSRS)**

- SQL Server Reporting Services n’est plus disponible pour installer via le programme d’installation de SQL Server à partir de CTP 2.1.
- Commentaires sont maintenant disponibles pour les rapports. Commentaires permettent d’ajouter une perspective à ce qui est dans un rapport et de collaborer avec d’autres personnes de votre organisation. Vous pouvez également inclure des pièces jointes avec votre commentaire.
- Pour SSRS plus informations sur les nouveautés, y compris les détails des versions précédentes, consultez [Nouveautés dans Reporting Services--... / reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Pour plus d’informations sur le serveur de rapports Power BI, consultez [prise en main avec un serveur de rapports Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

**Apprentissage des Services de l’ordinateur SQL Server**

- Il n’y a aucune nouvelle fonctionnalité de Machine Learning Services dans cette version CTP.
- Pour les Services de formation Machine plus informations sur les nouveautés, y compris les informations à partir de précédentes versions CTP, consultez [Nouveautés dans SQL Server Machine Learning Services--... / advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

**SQL Server Analysis Services (SSAS)**

- Cette version CTP ne contient pas de nouvelles fonctionnalités SSAS.  
- Pour plus d’informations sur les améliorations et correctifs de bogues dans cette version, consultez [Nouveautés dans SQL Server 2017 Analysis Services--... / analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section précédente.

1. [Notes de mise à jour de SQL Server 2017](#TitleNum_1)
2. [Quel &#39; s de SQL Server 2017](#TitleNum_2)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Articles de frères

Cette section répertorie les articles très similaires pour les articles récemment mis à jour dans d’autres zones de sujet, dans le même référentiel GitHub.


&nbsp;

[Microsoft /**sql-docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) référentiel sur GitHub.com :

- [Récemment mis à jour : **Microsoft SQL Server et les bases de données relationnelles** documents](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Récemment mis à jour : **Microsoft SQL Server** documents](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Récemment mis à jour : **Transact-SQL dans SQL Server** documents](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



