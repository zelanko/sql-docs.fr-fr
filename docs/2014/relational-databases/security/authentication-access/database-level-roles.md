---
title: Rôles au niveau de la base de données | Microsoft Docs
ms.custom: ''
ms.date: 09/22/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.database.f1
- sql12.swb.roleproperties.general.f1
- sql12.swb.roleproperties.object.f1
- SQL12.SWB.DBROLEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- db_denydatareader role
- users [SQL Server], database roles
- database-level roles [SQL Server]
- db_denydatawriter role
- roles [SQL Server], database
- principals [SQL Server], database-level
- db_backupoperator role
- credentials [SQL Server], roles
- db_accessadmin role
- schemas [SQL Server], roles
- permissions [SQL Server], roles
- database roles [SQL Server], listed
- db_datareader role
- db_ddladmin role
- db_datawriter role
- db_securityadmin role
- db_owner role
- database roles [SQL Server]
- fixed database roles [SQL Server]
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: 7f3fa5f6-6b50-43bb-9047-1544ade55e39
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3df05bddf37970ce0ff0d796bc2b5d93d309b4dc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63011720"
---
# <a name="database-level-roles"></a>Rôles au niveau de la base de données
  Pour gérer facilement les autorisations dans vos bases de données, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit plusieurs *rôles* , qui sont des principaux de sécurité regroupant d'autres principaux. Ils sont similaires aux ***groupes*** du système d'exploitation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Les autorisations des rôles au niveau de la base de données ont une portée à l'échelle de la base de données.  
  
 Il existe deux types de rôles au niveau de la base de données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: les *rôles de base de données fixes* qui sont prédéfinis dans la base de données et les *rôles de base de données flexibles* que vous pouvez créer.  
  
 Les rôles de base de données fixes sont définis au niveau de la base de données et existent dans chaque base de données. Les membres du rôle de base de données **db_owner** peuvent gérer l’appartenance aux rôles de base de données fixes. La base de données msdb comprend également des rôles de base de données fixes destinés à des usages spéciaux.  
  
 Vous pouvez ajouter tout compte de base de données, ainsi que d’autres rôles [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans des rôles au niveau de la base de données. Chaque membre d'un rôle de base de données fixe peut ajouter des connexions à ce rôle.  
  
> [!IMPORTANT]  
>  N'ajoutez pas de rôles de base de données flexibles en tant que membres de rôles fixes. Cela pourrait activer une élévation de privilèges involontaire.  
  
 Le tableau ci-dessous répertorie les rôles au niveau de la base de données fixes et leurs fonctionnalités. Ces rôles existent dans toutes les bases de données.  
  
|Nom du rôle au niveau de la base de données|Description|  
|-------------------------------|-----------------|  
|**db_owner**|Les membres du rôle de base de données fixe **db_owner** peuvent effectuer toutes les activités de configuration et de maintenance sur la base de données et peuvent également supprimer la base de données.|  
|**db_securityadmin**|Les membres du rôle de base de données fixe **db_securityadmin** peuvent modifier l'appartenance au rôle et gérer les autorisations. L'ajout de principaux à ce rôle pourrait activer une élévation de privilèges involontaire.|  
|**db_accessadmin**|Les membres du rôle de base de données fixe **db_accessadmin** peuvent ajouter ou supprimer l'accès à la base de données des connexions Windows, des groupes Windows et des connexions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|**db_backupoperator**|Les membres du rôle de base de données fixe **db_backupoperator** peuvent sauvegarder la base de données.|  
|**db_ddladmin**|Les membres du rôle de base de données fixe **db_ddladmin** peuvent exécuter n'importe quelle commande DDL (Data Definition Language) dans une base de données.|  
|**db_datawriter**|Les membres du rôle de base de données fixe **db_datawriter** peuvent ajouter, supprimer et modifier des données dans toutes les tables utilisateur.|  
|**db_datareader**|Les membres du rôle de base de données fixe **db_datareader** peuvent lire toutes les données de toutes les tables utilisateur.|  
|**db_denydatawriter**|Les membres du rôle de base de données fixe **db_denydatawriter** ne peuvent ajouter, modifier ou supprimer aucune donnée des tables utilisateur d'une base de données.|  
|**db_denydatareader**|Les membres du rôle de base de données fixe **db_denydatareader** ne peuvent lire aucune donnée des tables utilisateur d'une base de données.|  
  
## <a name="msdb-roles"></a>Rôles de msdb  
 La base de données msdb contient les rôles à usages spéciaux présentés dans le tableau ci-dessous.  
  
|Nom du rôle msdb|Description|  
|--------------------|-----------------|  
|`db_ssisadmin`<br /><br /> **db_ssisoperator**<br /><br /> **db_ssisltduser**|Les membres de ces rôles de base de données peuvent administrer et utiliser [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mises à niveau à partir d’une version antérieure peuvent contenir une version plus ancienne du rôle, nommée à l’aide de DTS (Data Transformation Services) au lieu de [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Pour plus d’informations, consultez [Rôles Integration Services &#40;Service SSIS&#41;](../../../integration-services/security/integration-services-roles-ssis-service.md).|  
|`dc_admin`<br /><br /> **dc_operator**<br /><br /> **dc_proxy**|Les membres de ces rôles de base de données peuvent administrer et utiliser le collecteur de données. Pour plus d'informations, consultez [Data Collection](../../data-collection/data-collection.md).|  
|**PolicyAdministratorRole**|Les membres du rôle de base de données **db_ PolicyAdministratorRole** peuvent effectuer toutes les activités de configuration et de maintenance sur les stratégies et conditions de la gestion basée sur une stratégie. Pour plus d’informations, consultez [Administrer des serveurs à l’aide de la Gestion basée sur des stratégies](../../policy-based-management/administer-servers-by-using-policy-based-management.md).|  
|**ServerGroupAdministratorRole**<br /><br /> **ServerGroupReaderRole**|Les membres de ces rôles de base de données peuvent administrer et utiliser des groupes de serveurs inscrits.|  
|**dbm_monitor**|Créé dans la `msdb` base de données lorsque la première base de données est inscrite dans moniteur de mise en miroir de bases de données. Le rôle **dbm_monitor** ne comporte aucun membre tant qu’un administrateur système n’affecte pas d’utilisateurs au rôle.|  
  
> [!IMPORTANT]  
>  Les membres du rôle db_ssisadmin et du rôle dc_admin peuvent être en mesure d'élever leurs privilèges à sysadmin. Cette élévation de privilège peut se produire, car ces rôles peuvent modifier les packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] et les packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] peuvent être exécutés par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide du contexte de sécurité sysadmin de l’Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour vous prémunir contre cette élévation de privilège lors de l'exécution de plans de maintenance, de jeux d'éléments de collecte de données et d'autres packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , configurez des travaux de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui exécutent des packages pour l'utilisation d'un compte proxy doté de privilèges limités ou ajoutez uniquement des membres sysadmin aux rôles db_ssisadmin et dc_admin.  
  
## <a name="working-with-database-level-roles"></a>Utilisation des rôles au niveau de la base de données  
 Le tableau ci-dessous explique les commandes, vues et fonctions permettant d'utiliser les rôles au niveau de la base de données.  
  
|Fonctionnalité|Type|Description|  
|-------------|----------|-----------------|  
|[sp_helpdbfixedrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql)|Métadonnées|Retourne une liste des rôles de base de données fixes.|  
|[sp_dbfixedrolepermission &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql)|Métadonnées|Affiche les autorisations d'un rôle de base de données fixe.|  
|[sp_helprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprole-transact-sql)|Métadonnées|Renvoie les informations concernant les rôles de la base de données active.|  
|[sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)|Métadonnées|Retourne des informations sur les membres d'un rôle dans la base de données actuelle.|  
|[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)|Métadonnées|Retourne une ligne pour chaque membre de chaque rôle de base de données.|  
|[IS_MEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-member-transact-sql)|Métadonnées|Indique si l'utilisateur actuel est membre du groupe Microsoft Windows ou du rôle de base de données Microsoft SQL Server spécifié.|  
|[CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)|Commande|Crée un rôle de base de données dans la base de données active.|  
|[ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)|Commande|Modifie le nom d'un rôle de base de données.|  
|[DROP ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-role-transact-sql)|Commande|Supprime un rôle de la base de données.|  
|[sp_addrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrole-transact-sql)|Commande|Crée un rôle de base de données dans la base de données active.|  
|[sp_droprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprole-transact-sql)|Commande|Supprime un rôle de base de données de la base de données actuelle.|  
|[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)|Commande|Ajoute un utilisateur ou un rôle de base de données, un compte de connexion ou un groupe Windows à un rôle de base de données dans la base de données active.|  
|[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)|Commande|Supprime un compte de sécurité d'un rôle SQL Server dans la base de données actuelle.|  
  
## <a name="public-database-role"></a>Rôle de base de données public  
 Chaque utilisateur de base de données appartient au rôle de base de données **public** . Lorsqu'un utilisateur ne s'est pas vu accorder ou refuser des autorisations spécifiques sur un objet sécurisable, il hérite des autorisations accordées à **public** sur cet objet.  
  
## <a name="related-content"></a>Contenu associé  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)  
  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/security-stored-procedures-transact-sql)  
  
 [Fonctions de sécurité &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)  
  
 [Sécurisation de SQL Server](../securing-sql-server.md)  
  
 [sp_helprotect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprotect-transact-sql)  
  
  
