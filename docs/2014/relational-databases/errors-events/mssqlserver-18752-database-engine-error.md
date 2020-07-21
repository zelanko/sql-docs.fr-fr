---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cafa08486680ff2f9318188446cd1117488553f2
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552214"
---
# <a name="mssqlserver_18752"></a>MSSQLSERVER_18752
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|18752|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|REPL_INUSE|  
|Texte du message|Un seul Agent de lecture du journal ou une seule procédure liée au journal (sp_repldone, sp_replcmds et sp_replshowcmds) peut se connecter à une base de données à la fois. Si vous avez exécuté une procédure liée au journal, supprimez la connexion à travers laquelle fut exécutée la procédure ou exécutez sp_replflush sur cette connexion avant de démarrer l'Agent de lecture du journal ou d'exécuter toute autre procédure liée au journal.|  
  
## <a name="explanation"></a>Explication  
 Un seul Agent de lecture du journal ou une seule procédure liée au journal peut se connecter à une base de données à la fois.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous qu'aucun autre lecteur de journal ne s'exécute pour la même base de données de publication, et qu'aucune autre connexion active n'avait auparavant exécuté sp_replcmds/sp_repltrans/sp_repldone sans exécuter sp_replflush ensuite ou se déconnecter.  
  
  
