---
title: "Notes de publication de SQL Server 2016 | Microsoft Docs"
ms.date: 02/27/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 6485ef83b940ab9d04b9406e461517d5254aec7f
ms.sourcegitcommit: 1a3584a60c12521ba5b4b12a18d8cb32b1f2d555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-2016-release-notes"></a>Notes de publication de SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
Cet article décrit des limitations et des problèmes des versions SQL Server 2016. Pour plus d’informations sur les nouveautés, consultez [Nouveautés de SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

> [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)  Télécharger SQL Server 2016 à partir du **[Centre d’évaluation](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
>
> [![Machine virtuelle Azure de petite taille](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Vous avez un compte Azure ?  Cliquez **[ici](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** pour lancer une machine virtuelle avec SQL Server 2016 SP1 déjà installé.
>
> [![Télécharger SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Pour obtenir la dernière version de SQL Server Management Studio, consultez **[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1) disponible
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 permet la mise à niveau de l’ensemble des éditions et niveaux de service de SQL Server 2016 vers SQL Server 2016 SP1. En plus des correctifs présentés dans cet article, SQL Server 2016 SP1 inclut les correctifs logiciels qui étaient inclus dans les mises à jour cumulatives (CU) 1 à 3 de SQL Server 2016.

- [Page de téléchargement de SQL Server 2016 SP1](https://www.microsoft.com/download/details.aspx?id=54276)
- [SQL Server 2016 Service Pack 1 - Informations sur la version](https://support.microsoft.com/kb/3182545) Répertorie les numéros de bogue et les problèmes individuels qui ont été résolus ou modifiés dans la version SP1.
 - ![info_tip](../sql-server/media/info-tip.png) Consultez le [Centre de mise à jour SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) pour obtenir des liens et des informations sur toutes les versions prises en charge, notamment les Service Packs de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

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
     
**Mise à jour du contenu :**    
Dans SQL Server Management Studio et Visual Studio, l’application Visionneuse d’aide peut se figer (se bloquer) pendant l’ajout de la documentation. Pour résoudre ce problème, effectuez les étapes ci-dessous. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Ouvrez le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings dans le Bloc-notes et remplacez la date dans le code ci-dessous par une date future.    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
``` 

## <a name="additional-information"></a>Informations supplémentaires
+ [Installation de SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [Centre de mise à jour SQL Server - liens et informations pour toutes les versions prises en charge](https://msdn.microsoft.com/library/ff803383.aspx)


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]    

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")    
