---
title: Autorisations du serveur public | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1389d712ff00438a2e6251315e8ebcc55e7fbff2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43813915"
---
# <a name="server-public-permissions"></a>Autorisations du serveur public
  Cette règle détermine si le rôle serveur public possède des autorisations de serveur. Chaque nom de connexion créé sur le serveur est un membre du rôle serveur public. Si cette condition est remplie, chaque nom de connexion sur le serveur disposera d'autorisations de serveur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 N'octroyez pas d'autorisations de serveur au rôle public du serveur.  
  
> [!IMPORTANT]  
>  Une fois que le programme d’installation se termine le **PUBLIC** rôle a `CONNECT` autorisation sur tous les points de terminaison à l’exception la **Dedicated Admin Connection**. Ce comportement est normal et ne doit normalement pas être modifié. (L’accès est contrôlé à l’aide de la `CONNECT SQL` autorisation qui est automatiquement accordée lorsque de nouvelles connexions sont créées.)  
  
### <a name="for-more-information"></a>Informations supplémentaires  
 [Sécurisation de SQL Server](../security/securing-sql-server.md)  
  
  
