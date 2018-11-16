---
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
manager: craigg
ms.openlocfilehash: 98ac248a005b7be8c2786275f30c23c129a39887
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51511964"
---
# <a name="server-public-permissions"></a>Autorisations du serveur public
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si le rôle serveur public possède des autorisations de serveur. Chaque nom de connexion créé sur le serveur est un membre du rôle serveur public. Si cette condition est remplie, chaque nom de connexion sur le serveur disposera d'autorisations de serveur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 N'octroyez pas d'autorisations de serveur au rôle public du serveur.  
  
> [!IMPORTANT]  
>  Une fois l'installation terminée, le rôle **PUBLIC** dispose de l'autorisation **CONNECT** sur tous les points de terminaison, à l'exception de **Dedicated Admin Connection**. Ce comportement est normal et ne doit normalement pas être modifié. (L’accès est contrôlé par l’autorisation **CONNECT SQL** qui est automatiquement accordée lorsque de nouvelles connexions sont créées.)  
  
### <a name="for-more-information"></a>Informations supplémentaires  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
