---
description: MSSQLSERVER_2570
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81a19dc1d0301fd8e098fbc45485f2318e3cd0e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482844"
---
# <a name="mssqlserver_2570"></a>MSSQLSERVER_2570
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
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
[UPDATE &#40;Transact-SQL&#41;](~/t-sql/queries/update-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](~/t-sql/data-types/data-types-transact-sql.md)  
  
