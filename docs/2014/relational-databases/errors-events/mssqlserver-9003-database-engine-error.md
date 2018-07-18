---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 92e9b26dbf87acb6714f031f09ab7c7fafd35e28
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427888"
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9003|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_INVALID_LSN|  
|Texte du message|Le numéro d'analyse du journal % S_LSN transmis à l'analyse du journal dans la base de données '%.*ls' n'est pas valide. Cette erreur peut indiquer les données sont endommagées ou que le fichier journal (.ldf) ne correspond pas au fichier de données (.mdf). Si cette erreur s'est produite pendant la réplication, recréez la publication. Sinon, restaurez les données à partir d'une sauvegarde si le problème se traduit par une défaillance lors du démarrage.|  
  
## <a name="explanation"></a>Explication  
 Un composant a passé un numéro séquentiel dans le journal non valide au gestionnaire de fichiers journaux de la base de données. Il peut s'agir d'une réplication, d'une altération ou d'une incohérence entre le fichier de données primaires et le journal.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si cela s’est produit pendant la réplication, recréez la publication. Sinon, effectuez une restauration à partir de la sauvegarde.  
  
  
