---
title: "Autorisations du serveur public | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "meilleures pratiques [moteur de base de données]"
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Autorisations du serveur public
  Cette règle détermine si le rôle serveur public possède des autorisations de serveur. Chaque nom de connexion créé sur le serveur est un membre du rôle serveur public. Si cette condition est remplie, chaque nom de connexion sur le serveur disposera d'autorisations de serveur.  
  
## Meilleures pratiques recommandées  
 N'octroyez pas d'autorisations de serveur au rôle public du serveur.  
  
> [!IMPORTANT]  
>  Une fois l'installation terminée, le rôle **PUBLIC** dispose de l'autorisation **CONNECT** sur tous les points de terminaison, à l'exception de **Dedicated Admin Connection**. Ce comportement est normal et ne doit normalement pas être modifié. (L’accès est contrôlé par l’autorisation **CONNECT SQL** qui est automatiquement accordée lorsque de nouvelles connexions sont créées.)  
  
### Informations supplémentaires  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  