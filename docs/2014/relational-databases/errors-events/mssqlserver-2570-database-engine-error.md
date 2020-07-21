---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb8f855a1675ef1d85c93cfc0ba38d12054d9b88
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551925"
---
# <a name="mssqlserver_2570"></a>MSSQLSERVER_2570
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2570|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Texte du message|Page P_ID, slot S_ID de l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE). La valeur COLUMN_NAME de colonne est hors limite pour le type de données "DATATYPE". Mettez la colonne à jour avec une valeur valide.|  
  
## <a name="explanation"></a>Explication  
 La valeur de colonne qui est contenue dans la colonne spécifiée se trouve en dehors de la plage des valeurs possibles pour le type de données de colonne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'erreur ne peut pas être réparée. Mettez à jour la colonne avec une valeur comprise dans la plage des valeurs pour le type de données de la colonne, puis réexécutez la commande.  Pour plus d’informations, consultez l’article [923247](https://support.microsoft.com/kb/923247) de la Base de connaissances.  
  
## <a name="see-also"></a>Voir aussi  
 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
