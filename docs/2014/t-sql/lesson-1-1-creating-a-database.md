---
title: Création d’une base de données (tutoriel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: f7143d762de9a2b445e0904dcd2b4619abc3e1b7
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036829"
---
# <a name="creating-a-database-tutorial"></a>Création d'une base de données (Didacticiel)
  Comme de nombreuses instructions [!INCLUDE[tsql](../includes/tsql-md.md)] , l'instruction CREATE DATABASE nécessite un paramètre obligatoire : le nom de la base de données. L'instruction CREATE DATABASE possède aussi de nombreux paramètres facultatifs, tels que l'emplacement du disque où vous souhaitez copier les fichiers de base de données. Lorsque vous exécutez l'instruction CREATE DATABASE sans les paramètres facultatifs, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise les valeurs par défaut pour un grand nombre de ces paramètres. Ce didacticiel utilise très peu de paramètres de syntaxe facultatifs.  
  
### <a name="to-create-a-database"></a>Pour créer une base de données  
  
1.  Dans une fenêtre de l'Éditeur de requête, tapez mais sans l'exécuter le code suivant :  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Utilisez le pointeur pour sélectionner les mots `CREATE DATABASE`, et appuyez sur la touche **F1**. La rubrique correspondante de la documentation en ligne de SQL Server doit s'ouvrir. Vous pouvez faire appel à cette technique pour rechercher la syntaxe finale de CREATE DATABASE et pour les autres instructions utilisées dans ce didacticiel.  
  
3.  Dans l'Éditeur de requête, appuyez sur la touche **F5** pour exécuter l'instruction et créer une base de données nommée `TestData`.  
  
 Lorsque vous créez une base de données, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] effectue une copie de la base de données **model** et remplace le nom de la copie par le nom de la base de données. Cette opération ne doit prendre que quelques secondes, sauf si vous spécifiez une taille initiale importante pour la base de données comme paramètre facultatif.  
  
> [!NOTE]  
>  Le mot clé GO sépare les instructions si plus d'une instruction est envoyée dans un même traitement. GO est facultatif lorsque le traitement contient uniquement une seule instruction.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une Table &#40;didacticiel&#41;](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
