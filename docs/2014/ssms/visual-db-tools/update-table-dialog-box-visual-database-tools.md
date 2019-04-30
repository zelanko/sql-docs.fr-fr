---
title: Mettre à jour une table, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8c5575f73ff75ef9276bab52571e8670f28e0be
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63204683"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Mettre à jour une table, boîte de dialogue (Visual Database Tools)
  Cette boîte de dialogue permet de spécifier la table à mettre à jour.  
  
 Elle apparaît si plusieurs tables sont affichées dans le volet Schéma lorsque vous modifiez le type d'une requête pour en faire une requête Update.  
  
 Sélectionnez la table à mettre à jour, puis choisissez **OK**.  
  
> [!NOTE]  
>  Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au diagramme à l’aide du Concepteur de tables ou du Concepteur de diagrammes de base de données, celui-ci tente d’abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des requêtes Update &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
