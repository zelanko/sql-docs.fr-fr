---
title: Connexion à SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4f40fd6fa88b001eaa222789d6be35b83f9bf90a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948545"
---
# <a name="connecting-to-sql-server-sybasetosql"></a>Connexion à SQL Server (SybaseToSQL)
Pour migrer des bases de données Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez vous connecter à toutes les instances de la cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque vous vous connectez, SSMA récupère les métadonnées sur toutes les bases de données dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et affiche les métadonnées de base de données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. SSMA stocke des informations sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous êtes connecté à, mais ne stocke pas les mots de passe.  
  
Votre connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu'à ce que vous fermez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migrer les données.  
  
Métadonnées relatives à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas synchronisé automatiquement. Au lieu de cela, si vous souhaitez mettre à jour les métadonnées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, vous devez manuellement mettre à jour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées, comme décrit dans le « Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations requises de SQL Server  
Le compte qui est utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite des autorisations différentes selon les actions effectuées par ce compte.  
  
-   Pour convertir des objets ASE à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou pour enregistrer la syntaxe converti vers des scripts, le compte doit disposer d’autorisation pour vous connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’exigence d’autorisation minimal est l’appartenance à la **db_owner** rôle de base de données dans la base de données cible.  
  
-   Pour migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le compte doit être un membre de la **sysadmin** rôle de serveur. Cela est nécessaire pour exécuter le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] packages de migration de données de l’Agent.  
  
-   Pour exécuter le code généré par SSMA, le compte doit avoir **Execute** autorisations pour toutes les fonctions définies par l’utilisateur dans le **ssma_syb** schéma de la **sysdb** base de données. Ces fonctions fournissent des fonctionnalités équivalentes des fonctions du système ASE et sont utilisées par les objets convertis.  
  
Si le compte qui est utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est pour effectuer la migration de toutes les tâches, le compte doit être un membre de la **sysadmin** rôle de serveur.  
  
## <a name="establishing-a-sql-server-connection"></a>L’établissement d’une connexion SQL Server  
Avant de convertir des objets de base de données ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, vous devez établir une connexion à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous souhaitez migrer la base de données ASE ou les bases de données.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données où les objets et les données seront migrées. Vous pouvez personnaliser ce mappage au niveau du schéma de ASE après vous être connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [mappage de schémas Sybase ASE à des schémas de SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
> [!IMPORTANT]  
> Avant d’essayer de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution et peut accepter les connexions.  
  
**Pour vous connecter à SQL Server**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Server**.  
  
    Si vous aviez précédemment connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nom de la commande sera **reconnexion à SQL Server**.  
  
2.  Dans la boîte de dialogue de connexion, entrez ou sélectionnez le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point ( **.** ).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée sur un autre ordinateur, entrez le nom d’ordinateur suivi d’une barre oblique inverse, puis sur le nom d’instance, tels que MyServer\MyInstance.  
  
3.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter les connexions sur un port non défini par défaut, entrez le numéro de port qui est utilisé pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions dans le **port du serveur** boîte. L’instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser.  
  
4.  Dans le **base de données** , entrez le nom de la base de données cible.  
  
    Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Dans le **authentification** , sélectionnez le type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **l’authentification Windows**. Pour utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **l’authentification SQL Server** , puis indiquez le nom de connexion et mot de passe.  
  
6.  Pour une connexion sécurisée, les deux contrôles sont ajoutés, le **chiffrer la connexion** et **TrustServerCertificate** cases à cocher. Uniquement lorsque **chiffrer la connexion** est activée, le **TrustServerCertificate** case à cocher est visible. Lorsque **chiffrer la connexion** est vérifiée (true) et **TrustServerCertificate** est désactivée (false), il valide le certificat SSL SQL Server. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé sur le côté client, ainsi que sur le côté serveur.  
  
7.  Cliquer sur **Se connecter**.  
  
**Compatibilité de Version supérieure**  
  
-   Vous serez en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet de migration créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Vous serez en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet de migration créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, mais vous ne serez pas en mesure de se connecter à des versions inférieures par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Vous serez en mesure de se connecter uniquement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet créé est SQL Server 2012.  
  
-   Compatibilité de version supérieur n’est pas valide pour SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**PROJET Visual Studio TYPE VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version : 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version : 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Oui|Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Oui|Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Oui|Oui|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Oui||  
|SQL Azure||||||Oui|  
  
> [!IMPORTANT]
> Conversion des objets de base de données est effectuée selon le type de projet, mais pas conformément à la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous êtes connecté. Dans le cas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projet 2005, Conversion est effectuée conformément [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 même si vous êtes connecté à une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016)  
  
## <a name="reconnecting-to-sql-server"></a>Rétablir la connexion à SQL Server  
Votre connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu'à ce que vous fermez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous mettez à jour les métadonnées, charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et migrer les données.  
  
La procédure de reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est identique à la procédure pour établir une connexion.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées du serveur SQL  
Métadonnées relatives à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données n’est pas automatiquement mis à jour. Les métadonnées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées est un instantané des métadonnées lorsque vous avez connecté tout d’abord à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou la dernière fois que vous avez mis à jour manuellement des métadonnées. Vous pouvez mettre à jour manuellement les métadonnées pour toutes les bases de données, ou pour n’importe quel base de données unique ou un objet de base de données.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, sélectionnez la case à cocher en regard de la base de données ou le schéma que vous souhaitez mettre à jour la base de données.  
  
    Par exemple, pour mettre à jour les métadonnées pour toutes les bases de données, activez la case à côté **bases de données**.  
  
3.  Avec le bouton droit de bases de données ou la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de données**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Si vous souhaitez personnaliser le mappage entre les schémas et les bases de données ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données et des schémas, consultez [mappage Sybase ASE schémas à des schémas de SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   Si vous souhaitez personnaliser les options de configuration pour les projets, consultez [définition des Options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   Si vous souhaitez personnaliser le mappage des types de données source et cible, consultez [mappage Sybase ASE et Types de données SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Si vous n’avez pas à effectuer ces, vous pouvez convertir les définitions d’objets de base de données Sybase ASE dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définitions d’objets. Pour plus d’informations, consultez [convertir les objets de base de données Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
