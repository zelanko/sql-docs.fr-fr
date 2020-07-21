---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ccfdf4f2409fa4a91e5b287b45c25918e41d1aa
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552994"
---
# <a name="mssqlserver_-2"></a>MSSQLSERVER_-2
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|-2|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Délai expiré.  Période de délai d'attente écoulée avant l'achèvement de l'opération, ou le serveur ne répond pas. (Microsoft SQL Server, erreur : -2)|   
  
## <a name="explanation"></a>Explication  
 Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur s'est peut-être produite parce que le pare-feu sur le serveur a refusé la connexion. 
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que vous avez configuré le pare-feu sur l’instance de serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accepter les connexions.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le pare-feu Windows pour autoriser l’accès SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)   
 [Configurer un pare-feu Windows pour l’accès Moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Protocoles réseau et bibliothèques réseau](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configuration du réseau client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
