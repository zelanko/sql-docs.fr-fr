---
title: MSSQLSERVER_4064 | Microsoft Docs
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
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8908c1075c0df7cb60d5e8b79c9d9067c03876ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|4064|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_UFAIL_FATAL|  
|Texte du message|Impossible d'ouvrir la base de données par défaut de l'utilisateur. Échec de la connexion.|  
  
## <a name="explanation"></a>Explication  
La connexion SQL Server n'a pas pu se connecter en raison d'un problème avec sa base de données par défaut. Soit la base de données n'est pas valide, soit la connexion ne dispose pas de l'autorisation CONNECT sur la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Utilisez ALTER LOGIN pour modifier la base de données par défaut de la connexion. Accordez l'autorisation CONNECT à la connexion.  
  
