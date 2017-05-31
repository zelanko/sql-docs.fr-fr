---
title: "Mettre à jour une table, boîte de dialogue (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e0abd8866fecfd845e56cd1ea26eabfc87b1e3b5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="update-table-dialog-box-visual-database-tools"></a>Mettre à jour une table, boîte de dialogue (Visual Database Tools)
Cette boîte de dialogue permet de spécifier la table à mettre à jour.  
  
Elle apparaît si plusieurs tables sont affichées dans le volet Schéma lorsque vous modifiez le type d'une requête pour en faire une requête Update.  
  
Sélectionnez la table à mettre à jour, puis choisissez **OK**.  
  
> [!NOTE]  
> Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l’aide de l’instruction Transact-SQL [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au schéma à l'aide du Concepteur de tables ou du Concepteur de schémas de base de données, celui-ci tente d'abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="see-also"></a>Voir aussi  
[Créer des requêtes Update (Visual Database Tools)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  

