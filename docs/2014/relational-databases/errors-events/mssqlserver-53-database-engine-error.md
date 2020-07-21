---
title: MSSQLSERVER_53 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00838b68427e856287ede5fd066baddcb106be05
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551184"
---
# <a name="mssqlserver_53"></a>MSSQLSERVER_53
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|53|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une erreur s'est produite lors de l'établissement d'une connexion au serveur.  Lors de la connexion à SQL Server, cet échec peut être dû au fait que les paramètres par défaut de SQL Server n'autorisent pas les connexions à distance. (fournisseur : Fournisseur de canaux nommés, erreur : 40 - Impossible d’ouvrir une connexion à SQL Server) (Fournisseur de données SqlClient .Net).|  
  
## <a name="explanation"></a>Explication  
 Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur s’est peut-être produite parce que le client ne peut pas résoudre le nom du serveur ou que le nom du serveur est incorrect.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que vous avez entré le nom de serveur correct sur le client et que vous pouvez résoudre ce nom à partir du client. Pour vérifier la résolution du nom TCP/IP, vous pouvez exécuter la commande **ping** dans le système d’exploitation Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Protocoles réseau et bibliothèques réseau](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configuration du réseau client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
