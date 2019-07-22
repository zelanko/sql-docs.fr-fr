---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81537ea994fa22ee9cafb2ba031677a1d5544dcd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123367"
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
  
