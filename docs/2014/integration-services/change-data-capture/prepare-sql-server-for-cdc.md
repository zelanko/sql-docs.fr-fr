---
title: Préparer SQL Server pour CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5f348a7f76f65c19801525967f3ded5c8b0d2d26
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58381556"
---
# <a name="prepare-sql-server-for-cdc"></a>Préparer SQL Server pour la capture de données modifiées
  Le service de capture de données modifiées Oracle requiert que toutes les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cibles contiennent la base de données MSXDBCDC. Vous créez cette base de données à l'aide de l'action Préparer SQL Server dans la console de configuration du service de capture de données modifiées. Cela crée un script spécial qui est exécuté pour créer les tables requises, les procédures stockées et autres artefacts nécessaires pour cette base de données. Cette tâche est effectuée une seule fois pour chaque instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible.  
  
 Pour plus d'informations sur la base de données MSXDBCDC, consultez Base de données MSXDBCDC.  
  
 Dans la console de configuration du service de capture de données modifiées, cliquez sur **Préparer SQL Server**. Si cette option n’est pas disponible, vérifiez que **Services de capture de données modifiées locaux** est sélectionné dans le volet gauche de la console.  
  
## <a name="options"></a>Options  
  
### <a name="server-name"></a>Nom du serveur  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Authentification  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **L’authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper le **nom d’utilisateur** et **mot de passe** pour l’utilisateur dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous vous connectez à.  
  
 Pour préparer l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la capture de données modifiées Oracle, la connexion doit avoir l'autorisation d'écriture dans la base de données MSXDBCDC. Entrez les informations d'identification pour une connexion qui a l'autorisation d'écriture dans la base de données MSXDBCDC, telle qu'un membre du rôle `sysasmin` .  
  
### <a name="options"></a>Options  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) pendant lequel le service de capture de données modifiées pour Oracle attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) pendant lequel le service Windows de capture de données modifiées Oracle attend l'exécution d'une commande avant expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: Sélectionnez **chiffrer la connexion** pour la communication entre le Service de capture de données modifiées Oracle et la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à l’aide d’une connexion chiffrée.  
  
-   **Avancé** : Tapez des propriétés de connexion supplémentaires, si nécessaire.  
  
### <a name="view-script"></a>Afficher le script  
 Cliquez sur **Afficher le script** pour afficher une version en lecture seule du script d’installation. Un administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut copier ce script dans la console de gestion SQL Server en vue de le modifier et de l'exécuter, si nécessaire. Pour plus d’informations sur le script Préparer SQL Server, consultez [Préparer SQL Server pour Oracle CDC : afficher le script](prepare-sql-server-for-oracle-cdc-view-script.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : utiliser des services de capture de données modifiées](work-with-cdc-services.md)   
 [Procédure : préparer SQL Server pour la capture de données modifiées](prepare-sql-server-for-cdc.md)  
  
  
