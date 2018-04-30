---
title: Notes de publication de SQL Server 2016 | Microsoft Docs
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
monikerRange: = sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d3e8962771c634f3cf606606beaac1b0604623e6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-2016-release-notes"></a>Notes de publication de SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
  Cet article décrit les limitations et les problèmes des versions SQL Server 2016, notamment les Service Packs. Pour plus d’informations sur les nouveautés, consultez [Nouveautés de SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)  Télécharger SQL Server 2016 à partir du **[Centre d’évaluation](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
- [![Machine virtuelle Azure de petite taille](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Vous avez un compte Azure ?  Cliquez **[ici](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** pour lancer une machine virtuelle avec SQL Server 2016 SP1 déjà installé.
- [![Télécharger SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Pour obtenir la dernière version de SQL Server Management Studio, consultez **[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp2"></a>SQL Server 2016 Service Pack 2 (SP2)

![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP2 inclut toutes les mises à jour cumulatives publiées après 2016 SP1, jusqu’à CU8 inclus. 

- [![Centre de téléchargement Microsoft](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?linkid=869608) [Télécharger SQL Server 2016 Service Pack 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- Pour une liste complète des mises à jour, consultez [Informations de version de SQL Server 2016 Service Pack 2](https://support.microsoft.com/en-us/help/4052908/sql-server-2016-service-pack-2-release-information)

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1)
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 inclut toutes les mises à jour cumulatives jusqu’à SQL Server 2016 RTM CU3, notamment la mise à jour de sécurité MS16-136. Elle contient un récapitulatif des solutions fournies dans les mises à jour cumulatives de SQL Server 2016 jusqu’à la dernière mise à jour cumulative - CU3 (incluse) et la mise à jour de sécurité MS16-136 publiée le 8 novembre 2016.

Les fonctionnalités suivantes sont disponibles dans les éditions Standard, Web, Express et Base de données locale de SQL Server SP1 (sauf indication contraire) :
- Always Encrypted
- Capture des changements de données (non disponible dans l’édition Express)
- columnstore
- Compression
- Masquage dynamique des données
- Audit à granularité fine
- OLTP en mémoire (non disponible dans l’édition Base de données locale)
- Plusieurs conteneurs Filestream (non disponible dans l’édition Base de données locale)
- Partitionnement
- PolyBase
- Sécurité au niveau des lignes

Le tableau suivant récapitule les principales améliorations fournies dans SQL Server 2016 SP1.

|Fonctionnalité|Description|Informations supplémentaires|
|---|---|---|
|Insertion en bloc dans des segments de mémoire avec un TABLOCK automatique sous TF 715| L’indicateur de trace 715 active le verrou de table pour les opérations de chargement en masse dans un segment de mémoire sans index non cluster.|[Migrating SAP workloads to SQL Server just got 2.5x faster](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|CREATE ou ALTER|Déployer des objets tels que des procédures stockées, des déclencheurs, des fonctions définies par l’utilisateur et des vues.|[Blog relatif au moteur de base de données SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/11/17/create-or-alter-another-great-language-enhancement-in-sql-server-2016-sp1/)|
|Prise en charge de DROP TABLE pour la réplication|Prise en charge de la DLL TABLE DROP pour la réplication afin de permettre la suppression d’articles de réplication.|[KB 3170123](https://support.microsoft.com/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactiona)|
|Signature du pilote Filestream RsFx|Le pilote Filestream RsFx est signé et certifié à l’aide du portail du tableau de bord du centre de développement du matériel Windows (portail de développement), ce qui permet d’installer le pilote Filestream RsFx SQL Server 2016 SP1 sur Windows Server 2016 et Windows 10 sans aucun problème.|[Migrating SAP workloads to SQL Server just got 2.5x faster](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|LPIM sur un compte de service SQL - identification par programmation|Permettre aux administrateurs de base de données d’identifier par programmation si le privilège LPIM (Verrouiller les pages en mémoire) est en vigueur au moment du démarrage du service.|[Developers Choice: Programmatically identify LPIM and IFI privileges in SQL Server](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-programmatically-identify-lpim-and-ifi-privileges-in-sql-server)|
|Nettoyage manuel du suivi des modifications|Une nouvelle procédure stockée nettoie à la demande la table interne de suivi des modifications.| [KB 3173157](https://support.microsoft.com/help/3173157/adds-a-stored-procedure-for-the-manual-cleanup-of-the-change-tracking)|
|Changements de Parallel INSERT..SELECT pour les tables temporaires locales|Nouvelle fonctionnalité Parallel INSERT dans les opérations INSERT..SELECT.|[SQL Server Customer Advisory Team](https://blogs.msdn.microsoft.com/sqlcat/2016/07/21/real-world-parallel-insert-what-else-you-need-to-know/)|
|Showplan XML|Diagnostics étendus incluant un avertissement d’allocation et une mémoire maximale activés pour une requête, des indicateurs de trace activés, ainsi que d’autres informations de diagnostic. | [KB 3190761](https://support.microsoft.com/help/3190761/update-to-improve-diagnostics-by-expose-data-type-of-the-parameters-fo)|
|Mémoire de classe de stockage|Améliore le traitement des transactions à l’aide de la mémoire de classe de stockage dans Windows Server 2016, ce qui permet d’accélérer les temps de validation des transactions par ordre de grandeur.|[Blog relatif au moteur de base de données SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)|
|USE HINT|Utilisez l’option de requête `OPTION(USE HINT('<option>'))` pour modifier le comportement de l’optimiseur de requête à l’aide d’indicateurs de niveau requête pris en charge. Contrairement à QUERYTRACEON, l’option USE HINT ne nécessite pas de privilèges sysadmin.|[Developers Choice: USE HINT query hints](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-use-hint-query-hints/)|
|Ajouts d’événements XEvent|Nouvelles fonctionnalités de diagnostics XEvent et Perfmon améliorent la résolution des problèmes de latence.|[Événements étendus](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)|

De plus, notez les correctifs suivants :
- En fonction des commentaires des administrateurs de base de données et de la Communauté SQL, à compter de SQL 2016 SP1, les messages de journalisation Hekaton sont réduits au minimum.
- Passez en revue les nouveaux [indicateurs de trace](https://docs.microsoft.com/en-us/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).
- Les versions complètes des exemples de bases de données WideWorldImporters fonctionnent maintenant avec les éditions Standard et Express, à compter de SQL Server 2016 SP1, et sont disponibles sur [GitHub]( https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0). Aucun changement n’est nécessaire dans l’exemple. Les sauvegardes de base de données créées dans la version finale de l’édition Entreprise avec Standard et Express SP1. 

Il peut s’avérer nécessaire de redémarrer le système après l’installation de SQL Server 2016 SP1. Nous vous recommandons de planifier et d’effectuer un redémarrage après l’installation de SQL Server 2016 SP1.

### <a name="download-pages-and-more-information"></a>Pages de téléchargement et informations supplémentaires

- [Télécharger le Service Pack 1 de Microsoft SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=54276)
- [SQL Server 2016 Service Pack 1 (SP1) Released](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)
- [Informations de version de SQL Server 2016 Service Pack 1](https://support.microsoft.com/kb/3182545)
- ![info_tip](../sql-server/media/info-tip.png) [Update Center pour SQL Server ](https://msdn.microsoft.com/library/ff803383.aspx) pour obtenir des liens et des informations sur toutes les versions prises en charge, notamment les Service Packs de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

##  <a name="bkmk_2016_ga"></a> SQL Server 2016 Release - General Availability (GA)
-   [Moteur de base de données (DG)](#bkmk_ga_instalpatch) 
-   [Stretch Database (DG)](#bkmk_ga_stretch)
-   [Magasin de requêtes (DG)](#bkmk_ga_query_store)
-   [Documentation du produit (DG)](#bkmk_ga_docs)
 
### ![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.gif) <a name="bkmk_ga_instalpatch"></a> Install Patch Requirement (GA) 
**Problème et impact sur le client :** Microsoft a identifié un problème qui affecte les fichiers binaires Microsoft VC ++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server 2016. Une mise à jour est disponible pour résoudre ce problème. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server 2016 risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server 2016, vérifiez si l’ordinateur a besoin du correctif décrit dans l’ [article 3164398 de la Base de connaissances](http://support.microsoft.com/kb/3164398). Le correctif est également inclus dans [Package de mises à jour cumulatives 1 (CU1) pour SQL Server 2016 RTM](https://www.microsoft.com/download/details.aspx?id=53338). 

**Résolution :** Utilisez une des solutions suivantes :

- Installez la [Mise à jour pour Visual C++ 2013 et de Visual C++ Redistributable Package (KB 3138367)](http://support.microsoft.com/kb/3138367). Le recours à l’article de la Base de connaissances est la méthode de résolution recommandée. Vous pouvez installer cette mise à jour avant ou après avoir installé SQL Server 2016. 

    Si SQL Server 2016 est déjà installé, exécutez les étapes suivantes dans l’ordre :

    1.  Téléchargez la version appropriée de *vcredist_\*exe*.
    1.  Arrêtez le service SQL Server pour toutes les instances du moteur de base de données.
    1.  Installez **KB 3138367**.
    1.  Redémarrez l'ordinateur.
 

 - Installez  [KB 3164398 – Mise à jour critique pour les composants requis MSVCRT de SQL Server 2016](http://support.microsoft.com/kb/3164398).  
 
    Si vous utilisez **KB 3164398**, vous pouvez l’installer en même temps que SQL Server, via Microsoft Update ou à partir du Centre de téléchargement Microsoft. 

    - **Pendant l’installation de SQL Server 2016 :** si l’ordinateur exécutant le programme d’installation de SQL Server a accès à Internet, le programme d’installation de SQL Server recherche la mise à jour pendant l’installation générale de SQL Server. Si vous acceptez la mise à jour, le programme d’installation télécharge et met à jour les fichiers binaires pendant l’installation.

    - **Microsoft Update :** la mise à jour est disponible auprès de Microsoft Update en tant que mise à jour critique de SQL Server 2016 non liée à la sécurité. Une installation via Microsoft Update après SQL Server 2016 nécessite le redémarrage du serveur à la suite de la mise à jour. 

    - **Centre de téléchargement :** enfin, la mise à jour est accessible à partir du Centre de téléchargement Microsoft. Vous pouvez télécharger le logiciel nécessaire à la mise à jour et l’installer sur les serveurs équipés de SQL Server 2016. 


### <a name="bkmk_ga_stretch"></a>Stretch Database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>Problème lié à la présence d’un caractère spécifique dans le nom d’une base de données ou d’une table

**Problème et impact sur le client :** l’activation de Stretch Database sur une base de données ou une table échoue avec une erreur. Ce problème se produit quand le nom de l’objet comprend un caractère qui est traité comme un caractère différent quand il est converti de minuscule en majuscule. Le caractère « ƒ » (créé en tapant Alt+159) est un exemple de caractère provoquant ce problème.

**Solution de contournement :** si vous voulez activer Stretch Database sur la base de données ou la table, la seule solution est de renommer l’objet et de supprimer le caractère qui pose problème.

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>Problème lié à un index qui utilise le mot clé INCLUDE

**Problème et impact sur le client :** l’activation de Stretch Database sur une table dont l’index utilise le mot clé INCLUDE pour inclure des colonnes supplémentaires dans l’index échoue avec une erreur.

**Solution de contournement :** supprimez l’index qui utilise le mot clé INCLUDE, activez Stretch Database sur la table, puis recréez l’index. Dans ce cas, veillez à suivre les pratiques et stratégies de maintenance de votre organisation pour limiter autant que possible ou éviter tout impact sur les utilisateurs de la table concernée.

### <a name="bkmk_ga_query_store"></a>Query Store

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Problème de nettoyage de données automatique sur les éditions autres que Enterprise et Developer

 **Problème et impact sur le client :** le nettoyage de données automatique échoue sur les éditions autres que Enterprise et Developer. Par voie de conséquence, dans la mesure où les données ne sont pas purgées manuellement, l’espace utilisé par le Magasin des requêtes croît au fil du temps jusqu’à atteindre la limite configurée. Si ce problème n’est pas corrigé, l’espace disque alloué pour les journaux d’erreurs se remplit également, car chaque tentative de nettoyage génère un fichier de vidage. La période d’activation du nettoyage dépend de la fréquence de la charge de travail, mais elle ne dépasse pas 15 minutes.

 **Solution de contournement :** si vous prévoyez d’utiliser le magasin de requêtes sur des éditions autres que Enterprise et Developer, vous devez désactiver explicitement les stratégies de nettoyage. Cela peut être fait à partir de SQL Server Management Studio (page Propriétés de la base de données) ou via un script Transact-SQL :

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

En outre, envisagez des options de nettoyage manuel pour empêcher le magasin de requêtes de passer en mode lecture seule. Par exemple, exécutez la requête suivante pour nettoyer périodiquement un espace de données dans son intégralité :

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

De même, exécutez les procédures stockées ci-dessous du magasin de requêtes pour nettoyer les statistiques d’exécution, des requêtes ou des plans spécifiques :

- `sp_query_store_reset_exec_stats`

- `sp_query_store_remove_plan`

- `sp_query_store_remove_query`


###  <a name="bkmk_ga_docs"></a> Documentation du produit (DG) 
 **Problème et impact sur le client :** la version téléchargeable de la documentation de SQL Server 2016 n’est pas encore disponible. Quand vous utilisez le Gestionnaire de bibliothèque d’aide pour **installer du contenu à partir d’une source en ligne**, vous voyez la documentation de SQL Server 2012 et SQL Server 2014, mais il n’existe aucune option pour la documentation de SQL Server 2016.    
    
 **Solution de contournement :** utilisez l’une des solutions de contournement suivantes :    
    
 ![Gérer les paramètres de l’aide pour SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Gérer les paramètres de l’aide pour SQL Server")    
    
-   Utilisez l’option **Choisir l’aide en ligne ou locale** , puis sélectionnez « Utiliser l’aide en ligne ».    
    
-   Utilisez l’option **Installer du contenu à partir d’une source en ligne** , puis téléchargez le contenu SQL Server 2014.    

 **Aide (F1) :** par défaut, quand vous appuyez sur F1 dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], la version en ligne de l’article d’aide F1 s’affiche dans le navigateur. Le problème vient de l’aide basée sur le navigateur même si vous avez configuré et installé l’aide locale. 

**Mise à jour de contenu :** Dans SQL Server Management Studio et Visual Studio, l’application Visionneuse d’aide peut se figer (se bloquer) pendant l’ajout de la documentation. Pour résoudre ce problème, effectuez les étapes ci-dessous. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Ouvrez le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings dans le Bloc-notes et remplacez la date dans le code ci-dessous par une date future.

     Dernière actualisation du cache = « 31/12/2017 00:00:00 »    
```

## Additional Information
+ [SQL Server 2016 installation](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [SQL Server Update Center - links and information for all supported versions](https://msdn.microsoft.com/library/ff803383.aspx)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")