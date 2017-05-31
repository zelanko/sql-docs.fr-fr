---
title: "Compléter des extraits de code Transact-SQL | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3cdeaf7c4fa9a002b25f0732f446d8e813234164
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="complete-transact-sql-snippets"></a>Compléter des extraits de code Transact-SQL
  Une fois un extrait de code [!INCLUDE[tsql](../../includes/tsql-md.md)] inséré dans un script, vous modifiez le contenu de l'extrait de code pour générer une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] complète.  
  
## <a name="completing-snippets"></a>Compléter des extraits de code  
 Lorsque vous ajoutez un extrait de code [!INCLUDE[tsql](../../includes/tsql-md.md)] à votre script, l'instruction de l'extrait de code insérée présente un ou plusieurs points de remplacement, mis en surbrillance. Si vous placez le pointeur de votre souris sur un point de remplacement, une info-bulle apparaît avec une description de l'élément syntaxique que vous pouvez spécifier. L’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] reconnaît l’extrait de code comme un élément distinct du script environnant jusqu’à ce que vous fermiez le fichier source. Les points de remplacement restent actifs jusqu'à la fermeture du fichier source.  
  
 Vous pouvez également ajouter des éléments syntaxiques supplémentaires au code du modèle inséré par un extrait de code. Par exemple, le modèle d'extrait de code Create Table génère deux définitions de colonne ; vous devez ajouter des définitions de colonne supplémentaires pour créer une table avec plus de deux colonnes.  
  
#### <a name="completing-the-snippet-statement"></a>Compléter l'instruction de l'extrait de code  
  
1.  Utilisez la touche TABULATION pour passer d'un point de remplacement au suivant. Utilisez SHIFT+TAB pour revenir au point de remplacement précédent.  
  
2.  Cliquez sur CTRL+SPACE pour appeler IntelliSense.  
  
3.  Sélectionnez un élément dans la liste ou tapez le code de remplacement de votre choix.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer des extraits de code Transact-SQL](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [Insérer des extraits de code d'entourage (surround-with) Transact-SQL](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
