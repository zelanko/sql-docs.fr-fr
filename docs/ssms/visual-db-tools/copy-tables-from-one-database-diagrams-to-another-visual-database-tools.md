---
title: Copier des tables d’un diagramme de base de données vers un autre | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 794a484546d1ab40ae5da167a5d0eff64436f211
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67686124"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>Copier des tables d’un diagramme de base de données vers un autre (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
[Utiliser des diagrammes de base de données &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Ajouter des tables à des schémas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
