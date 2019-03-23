---
title: Connexion à SQL Server pour la suppression | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: acb755f8cc1e425e38714013511948f7b5b4c580
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58392937"
---
# <a name="connection-to-sql-server-for-delete"></a>Connexion à SQL Server pour la suppression
  Lorsqu’une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner**) à la base de données MSXDBCDC tente de supprimer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui a l’autorisation d’accès en écriture à la base de données MSXDBCDC, notamment le rôle de base de données **db_owner** pour supprimer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **L’authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper le **connexion** et **mot de passe** pour l’utilisateur dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous vous connectez à.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) le programme attend la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion soit établie avant de générer une erreur de délai d’attente. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) que le programme attend d’exécution de la commande SQL soit terminée avant de générer une erreur de délai d’attente. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: Sélectionnez **chiffrer la connexion** pour vous assurer que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion établie est chiffrée pour garantir la confidentialité.  
  
-   **Avancé** : Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server requises pour le service de capture de données modifiées](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
