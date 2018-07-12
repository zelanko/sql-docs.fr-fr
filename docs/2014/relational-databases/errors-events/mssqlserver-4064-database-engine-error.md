---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d4f94fb3dccadaba54528d195c03c81ed1d9c63
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432408"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
    
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
  
  
