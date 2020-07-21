---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab4236b47f1ab7c4824296b96d6fb25c1cf6d933
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551484"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|4064|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_UFAIL_FATAL|  
|Texte du message|La base de données utilisateur par défaut ne peut pas être ouverte. Échec de la connexion.|  
  
## <a name="explanation"></a>Explication  
 La connexion SQL Server n'a pas pu se connecter en raison d'un problème avec sa base de données par défaut. Soit la base de données n'est pas valide, soit la connexion ne dispose pas de l'autorisation CONNECT sur la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez ALTER LOGIN pour modifier la base de données par défaut de la connexion. Accordez l'autorisation CONNECT à la connexion.  
  
  
