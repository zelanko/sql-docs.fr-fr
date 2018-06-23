---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c9b1f477feed3215544018dc28cda840253022ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140967"
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
    
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
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Groupes de fichiers et fichiers de base de données](../databases/database-files-and-filegroups.md)  
  
  
