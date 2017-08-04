---
title: "Connexion à SQL Server pour la suppression | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9be0eb89c1d19068e8cb97e94654d5dc177c0a86
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connection-to-sql-server-for-delete"></a>Connexion à SQL Server pour la suppression
  Lorsqu’une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner** ) à la base de données MSXDBCDC tente de supprimer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui a l’autorisation d’accès en écriture à la base de données MSXDBCDC, notamment le rôle de base de données **db_owner** pour supprimer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper **l’identifiant** et le **mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: tapez le délai d’attente du programme (en secondes) avant qu’il génère une erreur d’expiration du délai de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: tapez le délai d’attente du programme (en secondes) avant qu’il génère une erreur d’expiration du délai d’exécution d’une commande SQL. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: sélectionnez **Chiffrer la connexion** pour garantir que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] établie est chiffrée et assurer ainsi la protection des données.  
  
-   **Avancé**: cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion SQL Server des autorisations requises pour le Service de capture de données modifiées](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
