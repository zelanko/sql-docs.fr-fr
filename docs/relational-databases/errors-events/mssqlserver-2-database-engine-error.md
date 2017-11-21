---
title: MSSQLSERVER_2 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a8fe9aa05a8e8f7b5c9c179ff6528e53890e6be7
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2"></a>MSSQLSERVER_2
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une erreur s'est produite lors de l'établissement d'une connexion au serveur.  Lors de la connexion à SQL Server, cet échec peut être dû au fait que les paramètres par défaut de SQL Server n'autorisent pas les connexions à distance. (fournisseur : Fournisseur de canaux nommés, erreur : 40 - Impossible d'ouvrir une connexion à SQL Server) (Fournisseur de données SqlClient .Net)|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas répondu à la demande du client parce que le serveur n’a probablement pas été démarré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Assurez-vous que le serveur a été démarré.  
  
## <a name="see-also"></a>Voir aussi  
[Gérer les services du moteur de base de données](~/database-engine/configure-windows/manage-the-database-engine-services.md)  
[Configurer des protocoles clients](~/database-engine/configure-windows/configure-client-protocols.md)  
[Protocoles réseau et bibliothèques réseau](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Configuration du réseau client](~/database-engine/configure-windows/client-network-configuration.md)  
[Configurer des protocoles clients](~/database-engine/configure-windows/configure-client-protocols.md)  
[Activer ou désactiver un protocole réseau de serveur](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

