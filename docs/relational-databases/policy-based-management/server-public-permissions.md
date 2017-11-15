---
title: "Autorisations du serveur public | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5c9c5606ffe070cd72648e256f059d6375455dd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="server-public-permissions"></a>Autorisations du serveur public
  Cette règle détermine si le rôle serveur public possède des autorisations de serveur. Chaque nom de connexion créé sur le serveur est un membre du rôle serveur public. Si cette condition est remplie, chaque nom de connexion sur le serveur disposera d'autorisations de serveur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 N'octroyez pas d'autorisations de serveur au rôle public du serveur.  
  
> [!IMPORTANT]  
>  Une fois l'installation terminée, le rôle **PUBLIC** dispose de l'autorisation **CONNECT** sur tous les points de terminaison, à l'exception de **Dedicated Admin Connection**. Ce comportement est normal et ne doit normalement pas être modifié. (L’accès est contrôlé par l’autorisation **CONNECT SQL** qui est automatiquement accordée lorsque de nouvelles connexions sont créées.)  
  
### <a name="for-more-information"></a>Informations supplémentaires  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
