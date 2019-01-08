---
title: Connexion à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85bab82173ce0caa5997774978b616340d6e5a30
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772961"
---
# <a name="connection-to-sql-server"></a>Connexion à SQL Server
  Quand une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner**) à la base de données MSXDBCDC tente de créer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui dispose d’une autorisation d’accès en écriture à la base de données MSXDBCDC (tel est notamment le cas du rôle de base de données **db_owner** ) pour créer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
### <a name="server-name"></a>Nom du serveur  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Authentification  
 Sélectionnez l'une des options suivantes :  
  
-   Authentification Windows  
  
-   **L’authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper le **connexion** et **mot de passe** pour l’utilisateur dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous vous connectez à.  
  
### <a name="options"></a>Options  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) le programme attend la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion soit établie avant de générer une erreur de délai d’attente. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) que le programme attend d’exécution de la commande SQL soit terminée avant de générer une erreur de délai d’attente. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: Sélectionnez **chiffrer la connexion** pour vous assurer que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion établie est chiffrée pour garantir la confidentialité.  
  
-   **Avancé** : Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server requises pour le service de capture de données modifiées](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
