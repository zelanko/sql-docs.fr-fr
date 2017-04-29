---
title: "Copier des tables d’un schéma de base de données vers un autre | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4a64ef158777c4f5b5bfc091feb59a70b013973d
ms.lasthandoff: 04/11/2017

---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>Copier des tables d'un schéma de base de données vers un autre (Visual Database Tools)
Vous pouvez copier une table d'un schéma de base de données à l'autre dans la même base de données.  
  
Cette opération ajoute une référence à la table dans le deuxième schéma. La table n'est pas dupliquée dans la base de données. Par exemple, si vous copiez la table `authors` d'un schéma de base de données à un autre, les deux schémas font référence à la même table `authors` de la base de données.  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>Pour copier une table à partir d'un autre schéma de base de données  
  
1.  Vérifiez que vous êtes connecté à la base de données dont vous voulez copier une table.  
  
2.  Ouvrez les schémas de base de données source et cible, puis, dans le schéma source, sélectionnez la table que vous voulez copier vers le schéma cible.  
  
3.  Dans la barre d’outils, cliquez sur le bouton **Copier** . Cette action place la définition de la table sélectionnée dans le Presse-papiers.  
  
4.  Basculez vers le schéma cible. Ce schéma doit se trouver dans la même base de données que le schéma source.  
  
5.  Dans la barre d’outils, cliquez sur le bouton **Coller** . Le contenu du Presse-papiers apparaît au nouvel emplacement et reste affiché en surbrillance jusqu'à ce que vous cliquiez ailleurs. S'il existe des relations entre les tables sélectionnées et d'autres tables du schéma cible, les lignes de relation correspondantes sont dessinées automatiquement.  
  
Lorsque vous modifiez la table dans un des schémas, les deux schémas reflètent ces changements. De même, une fois que vous avez enregistré la table dans l'un des schémas, elle cesse d'être considérée comme « modifiée » dans les deux schémas.  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser des schémas de base de données &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Ajouter des tables à des schémas &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  

