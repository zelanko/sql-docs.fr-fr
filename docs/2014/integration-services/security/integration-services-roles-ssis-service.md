---
title: Rôles Integration Services (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5bc65a7a3ff30deb429ceeb8458ac477432a758c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422086"
---
# <a name="integration-services-roles-ssis-service"></a>Rôles Integration Services (Service SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]comprend les trois rôles fixes au niveau de la base de données, `db_ssisadmin` , **db_ssisltduser**et **db_ssisoperator**, pour contrôler l’accès aux packages. Les rôles ne peuvent être implémentés que sur les packages enregistrés `msdb` dans la base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous affectez des rôles à un package à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les attributions de rôles sont enregistrées dans la `msdb` base de données.  
  
## <a name="read-and-write-actions"></a>Actions de lecture et d'écriture  
 Le tableau suivant décrit les actions de lecture et d’écriture de Windows et des rôles fixes de niveau base de données dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Role|Action de lecture|Action d'écriture|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> ou<br /><br /> `sysadmin`|Énumérer ses packages.<br /><br /> Énumérer tous les packages.<br /><br /> Afficher ses packages.<br /><br /> Afficher tous les packages.<br /><br /> Exécuter ses packages.<br /><br /> Exécuter tous les packages.<br /><br /> Exporter ses packages.<br /><br /> Exporter tous les packages.<br /><br /> Exécuter tous les packages dans l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Importer des packages.<br /><br /> Supprimer ses packages.<br /><br /> Supprimer tous les packages.<br /><br /> Modifier les rôles de ses packages.<br /><br /> Modifier tous les rôles de package.<br /><br /> <br /><br /> Les membres ** \* \* \* importants \* ** du rôle db_ssisadmin et le rôle dc_admin peuvent être en mesure d’élever leurs privilèges à sysadmin. Cette élévation de privilège peut se produire, car ces rôles peuvent modifier les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peuvent être exécutés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du contexte de sécurité sysadmin de l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour vous prémunir contre cette élévation de privilège lors de l'exécution de plans de maintenance, de jeux d'éléments de collecte de données et d'autres packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , configurez des travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécutent des packages pour l'utilisation d'un compte proxy doté de privilèges limités ou ajoutez uniquement des membres sysadmin aux rôles db_ssisadmin et dc_admin.|  
|**db_ssisltduser**|Énumérer ses packages.<br /><br /> Énumérer tous les packages.<br /><br /> Afficher ses packages.<br /><br /> Exécuter ses packages.<br /><br /> Exporter ses packages.|Importer des packages.<br /><br /> Supprimer ses packages.<br /><br /> Modifier les rôles de ses packages.|  
|**db_ssisoperator**|Énumérer tous les packages.<br /><br /> Afficher tous les packages.<br /><br /> Exécuter tous les packages.<br /><br /> Exporter tous les packages.<br /><br /> Exécuter tous les packages dans l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|None|  
|**Administrateurs Windows**|Afficher les détails d'exécution de tous les packages en cours d'exécution.|Arrêter tous les packages en cours d'exécution.|  
  
## <a name="sysssispackages-table"></a>Table sysssispackages  
 La table **sysssispackages** dans `msdb` contient les packages qui sont enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql).  
  
 La table **sysssispackages** inclut des colonnes contenant des informations sur les rôles affectés aux packages.  
  
-   Le rôle **readerrole** spécifie le rôle qui bénéficie d'un accès en lecture au package.  
  
-   La colonne **writerrole** spécifie le rôle qui bénéficie d'un accès en écriture au package.  
  
-   La colonne **ownersid** contient l'identificateur de sécurité unique de l'utilisateur qui a créé le package. Cette colonne définit le propriétaire du package.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les autorisations de `db_ssisadmin` et **db_ssisoperator** des rôles fixes au niveau de la base de données et l’identificateur de sécurité unique de l’utilisateur qui a créé le package s’appliquent au rôle lecteur pour les packages, et les autorisations du `db_ssisadmin` rôle et l’identificateur de sécurité unique de l’utilisateur qui a créé le package s’appliquent au rôle de rédacteur. Un utilisateur doit être membre du `db_ssisadmin` rôle, **db_ssisltduser**ou **db_ssisoperator** pour avoir un accès en lecture au package. Un utilisateur doit être membre du `db_ssisadmin` rôle pour avoir un accès en écriture.  
  
## <a name="access-to-packages"></a>Accès aux packages  
 Les rôles fixes au niveau de la base de données fonctionnent conjointement avec les rôles définis par l'utilisateur. Les rôles définis par l’utilisateur sont les rôles que vous créez dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis que vous utilisez pour attribuer des autorisations aux packages. Pour accéder à un package, un utilisateur doit être membre du rôle défini par l’utilisateur et du rôle fixe pertinent de niveau base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Par exemple, si les utilisateurs sont membres du rôle **AuditUsers** défini par l’utilisateur qui est affecté à un package, ils doivent également être membres de `db_ssisadmin` , **db_ssisltduser**ou **db_ssisoperator** rôle pour avoir un accès en lecture au package.  
  
 Si vous n'affectez pas des rôles définis par l'utilisateur aux packages, les rôles de base de données fixes déterminent l'accès aux packages.  
  
 Si vous souhaitez utiliser des rôles définis par l’utilisateur, vous devez les ajouter à la `msdb` base de données avant de pouvoir les affecter à des packages. Vous pouvez créer de nouveaux rôles de base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Les rôles de niveau base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] accordent des droits sur les tables système [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de la base de données msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](le service MSSQLSERVER) doit être démarré pour que vous puissiez vous connecter au Moteur de base de données et accéder à la `msdb` base de données.  
  
 Pour affecter des rôles dans les packages, vous devez effectuer les tâches suivantes.  
  
-   **Ouvrir l'Explorateur d'objets et se connecter à Integration Services**  
  
     Avant de pouvoir affecter des rôles à des packages à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez ouvrir l'Explorateur d'objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et vous connecter à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] doit être démarré pour que vous puissiez vous connecter à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Affecter des rôles de lecture et d'écriture aux packages**  
  
     Vous pouvez affecter un rôle de lecture et d'écriture à chaque package.  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Affecter un rôle de lecture et d'écriture à un package](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Créer un rôle défini par l'utilisateur](../create-a-user-defined-role.md)  
  
-   [Se connecter à Integration Services](../connect-to-integration-services.md)  
  
  
