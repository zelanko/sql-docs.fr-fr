---
title: Copier des Tables à partir de diagrammes d’une base de données vers un autre (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d1b0d70a5d8121963d424f25eef517af7cde4ba7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62720075"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>Copier des tables d’un diagramme de base de données vers un autre (Visual Database Tools)
  Vous pouvez copier une table d’un diagramme de base de données à l’autre dans la même base de données.  
  
 Cette opération ajoute une référence à la table dans le deuxième diagramme. La table n'est pas dupliquée dans la base de données. Par exemple, si vous copiez la table `authors` d’un diagramme de base de données à un autre, les deux diagrammes font référence à la même table `authors` de la base de données.  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>Pour copier une table à partir d’un autre diagramme de base de données  
  
1.  Vérifiez que vous êtes connecté à la base de données dont vous voulez copier une table.  
  
2.  Ouvrez les diagrammes de base de données source et cible, puis, dans le diagramme source, sélectionnez la table que vous voulez copier vers le diagramme cible.  
  
3.  Dans la barre d’outils, cliquez sur le bouton **Copier** . Cette action place la définition de la table sélectionnée dans le Presse-papiers.  
  
4.  Basculez vers le schéma cible. Ce schéma doit se trouver dans la même base de données que le schéma source.  
  
5.  Dans la barre d’outils, cliquez sur le bouton **Coller** . Le contenu du Presse-papiers apparaît au nouvel emplacement et reste affiché en surbrillance jusqu'à ce que vous cliquiez ailleurs. S'il existe des relations entre les tables sélectionnées et d'autres tables du schéma cible, les lignes de relation correspondantes sont dessinées automatiquement.  
  
 Lorsque vous modifiez la table dans un des schémas, les deux schémas reflètent ces changements. De même, une fois que vous avez enregistré la table dans l'un des schémas, elle cesse d'être considérée comme « modifiée » dans les deux schémas.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des schémas de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Ajouter des tables à des schémas &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md)  
  
  
