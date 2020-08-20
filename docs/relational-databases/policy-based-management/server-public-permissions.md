---
description: Autorisations du serveur public
title: Autorisations du serveur public | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4abf2fd4068f19befd2896a27b9b214fee95dec0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482551"
---
# <a name="server-public-permissions"></a>Autorisations du serveur public
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle détermine si le rôle serveur public possède des autorisations de serveur. Chaque nom de connexion créé sur le serveur est un membre du rôle serveur public. Si cette condition est remplie, chaque nom de connexion sur le serveur disposera d'autorisations de serveur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 N'octroyez pas d'autorisations de serveur au rôle public du serveur.  
  
> [!IMPORTANT]  
>  Une fois l'installation terminée, le rôle **PUBLIC** dispose de l'autorisation **CONNECT** sur tous les points de terminaison, à l'exception de **Dedicated Admin Connection**. Ce comportement est normal et ne doit normalement pas être modifié. (L’accès est contrôlé par l’autorisation **CONNECT SQL** qui est automatiquement accordée lorsque de nouvelles connexions sont créées.)  
  
### <a name="for-more-information"></a>Informations supplémentaires  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
