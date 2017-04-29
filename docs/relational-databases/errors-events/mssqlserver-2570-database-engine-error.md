---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d69c6dc0336426fe5c74d5789884c16c854cfb9b
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2570|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Texte du message|Page P_ID, slot S_ID de l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE). La valeur COLUMN_NAME de colonne est hors limite pour le type de données "DATATYPE". Mettez la colonne à jour avec une valeur valide.|  
  
## <a name="explanation"></a>Explication  
La valeur de colonne qui est contenue dans la colonne spécifiée se trouve en dehors de la plage des valeurs possibles pour le type de données de colonne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
L'erreur ne peut pas être réparée. Mettez à jour la colonne avec une valeur comprise dans la plage des valeurs pour le type de données de la colonne, puis réexécutez la commande.  Pour plus d’informations, consultez l’article [923247](http://support.microsoft.com/kb/923247) de la Base de connaissances.  
  
## <a name="see-also"></a>Voir aussi  
[UPDATE &#40;Transact-SQL&#41;](~/t-sql/queries/update-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](~/t-sql/data-types/data-types-transact-sql.md)  
  

