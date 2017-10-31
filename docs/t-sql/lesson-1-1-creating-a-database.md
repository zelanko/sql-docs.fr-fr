---
title: "Création d’une base de données (didacticiel) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6628dcf0ab38db441de9bd9324e69993e5759c38
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-1-1---creating-a-database"></a>Leçon 1-1-Création d’une base de données
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
> Le mot clé GO sépare les instructions si plus d'une instruction est envoyée dans un même traitement. GO est facultatif lorsque le traitement contient uniquement une seule instruction.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Création d’une table &#40;Didacticiel&#41;](../t-sql/lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>Voir aussi  
[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
  

