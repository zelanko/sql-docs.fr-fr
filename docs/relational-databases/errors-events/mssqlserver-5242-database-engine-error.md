---
title: MSSQLSERVER_5242 | Microsoft Docs
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
helpviewer_keywords: 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38444abe57894f79cac3eed5e7b67bb70ed947d8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|5242|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une incohérence a été détectée durant une opération interne dans la base de données '%.*ls'(ID : %d), dans la page %S_PGID. Contactez le support technique. Numéro de référence %ld.|  
  
## <a name="explanation"></a>Explication  
Une incohérence structurelle s'est produite dans la page de base de données qui est référencée dans le message d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Groupes de fichiers et fichiers de base de données](~/relational-databases/databases/database-files-and-filegroups.md)  
  
