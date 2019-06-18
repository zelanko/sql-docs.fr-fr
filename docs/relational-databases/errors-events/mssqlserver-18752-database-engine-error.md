---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 11fabe1ed7b54f77463e75c45e4a1a6f4e35d38d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62688011"
---
# <a name="mssqlserver18752"></a>MSSQLSERVER_18752
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|18752|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|REPL_INUSE|  
|Texte du message|Un seul Agent de lecture du journal ou une seule procédure liée au journal (sp_repldone, sp_replcmds et sp_replshowcmds) peut se connecter à une base de données à la fois. Si vous avez exécuté une procédure liée au journal, supprimez la connexion à travers laquelle fut exécutée la procédure ou exécutez sp_replflush sur cette connexion avant de démarrer l'Agent de lecture du journal ou d'exécuter toute autre procédure liée au journal.|  
  
## <a name="explanation"></a>Explication  
Un seul Agent de lecture du journal ou une seule procédure liée au journal peut se connecter à une base de données à la fois.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Assurez-vous qu'aucun autre lecteur de journal ne s'exécute pour la même base de données de publication, et qu'aucune autre connexion active n'avait auparavant exécuté sp_replcmds/sp_repltrans/sp_repldone sans exécuter sp_replflush ensuite ou se déconnecter.  
  
