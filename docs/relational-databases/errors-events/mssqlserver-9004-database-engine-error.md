---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b768a61049580db483ba51a725c585d74638d416
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9004|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_CORRUPT|  
|Texte du message|Une erreur s'est produite lors du traitement du journal de la base de données '%.*ls'.  If possible, restore from backup. Si aucune sauvegarde n'est disponible, vous devrez peut-être recréer le journal.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite lors du traitement du journal, au cours d'une annulation, d'une récupération ou d'une réplication. Cela peut indiquer une erreur détectée par le système d'exploitation ou une erreur de cohérence interne détectée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Action de l'utilisateur  
L'une des actions ci-dessous corrigera cette erreur :  
  
-   Effectuez la restauration à partir d'une sauvegarde.  
  
-   Régénérez le journal.  
  
Vérifiez également les journaux des événements et les journaux des erreurs du système qui peuvent être à l'origine du problème.  
  
