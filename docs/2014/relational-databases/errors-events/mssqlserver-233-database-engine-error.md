---
title: MSSQLSERVER_233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fbe1fbc9aee04353ee4b5628ec1bddb7fc860a33
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553404"
---
# <a name="mssqlserver_233"></a>MSSQLSERVER_233
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|233|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une connexion a été établie avec le serveur, mais une erreur s’est ensuite produite pendant le processus de connexion. (fournisseur : Fournisseur de mémoire partagée, erreur : 0 - Il n’y a pas de processus à l’autre extrémité du canal.) (Microsoft SQL Server, erreur : 233)|  
  
## <a name="explanation"></a>Explication  
 Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur s'est peut-être produite parce que le serveur n'est pas configuré pour accepter des connexions distantes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez l'outil Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'accepter des connexions distantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Protocoles réseau et bibliothèques réseau](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configuration du réseau client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
