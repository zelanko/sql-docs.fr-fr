---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9342a460837fd6c638ea49b702cf1159b59c3aea
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429528"
---
# <a name="mssqlserver-1"></a>MSSQLSERVER_-1
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|-1|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une erreur s'est produite lors de l'établissement d'une connexion au serveur.  Lors de la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette erreur est peut être due au fait que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'autorise pas les connexions distantes selon les paramètres par défaut. (fournisseur : interfaces réseau SQL, erreur : 28 - Le serveur ne prend pas en charge le protocole demandé) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], erreur : -1).|  
  
## <a name="explanation"></a>Explication  
 Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur peut être causée par l'une des raisons suivantes :  
  
-   Le nom d'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié n'est pas valide.  
  
-   Les protocoles TCP ou de canaux nommés ne sont pas activés.  
  
-   Le pare-feu sur le serveur a refusé la connexion.  
  
-   Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (sqlbrowser) n’est pas démarré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, essayez d'effectuer l'une des opérations suivantes :  
  
-   Vérifiez l'orthographe du nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié dans la chaîne de connexion.  
  
-   Utilisez l’outil Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour faire en sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accepte les connexions distantes par l’intermédiaire des protocoles TCP ou de canaux nommés.  
  
-   Veillez à configurer le pare-feu sur l’instance de serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’ouvrir des ports pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le port [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (UDP 1434).  
  
-   Assurez-vous que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est démarré sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Protocoles réseau et bibliothèques réseau](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configuration du réseau client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Activer ou désactiver un protocole réseau de serveur](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
