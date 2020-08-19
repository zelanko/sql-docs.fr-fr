---
description: Curseurs dynamiques dans ODBC
title: Curseurs dynamiques ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19ae15a211329e07fdab13a5b6ff40e210e97cb5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429191"
---
# <a name="odbc-dynamic-cursors"></a>Curseurs dynamiques dans ODBC
Un curseur dynamique est simplement : dynamique. Il peut détecter toute modification apportée à l’appartenance, à l’ordre et aux valeurs du jeu de résultats après l’ouverture du curseur. Par exemple, supposez qu’un curseur dynamique extrait deux lignes et qu’une autre application met ensuite à jour l’une de ces lignes et supprime l’autre. Si le curseur dynamique tente ensuite de récupérer ces lignes, il ne trouvera pas la ligne supprimée, mais renverra les nouvelles valeurs de la ligne mise à jour.  
  
 Les curseurs dynamiques détectent toutes les mises à jour, suppressions et insertions, les unes avec les autres et celles effectuées par d’autres. (Ceci est soumis au niveau d’isolation de la transaction, tel qu’il est défini par l’attribut de connexion SQL_ATTR_TXN_ISOLATION.) Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR reflète ces modifications et peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED et SQL_ROW_ADDED. Elle ne peut pas retourner SQL_ROW_DELETED, car un curseur dynamique ne retourne pas de lignes supprimées en dehors de l’ensemble de lignes et ne reconnaît donc plus l’existence de la ligne supprimée dans le jeu de résultats ou son élément correspondant dans le tableau d’état de ligne. SQL_ROW_ADDED est retourné uniquement lorsqu’une ligne est mise à jour par un appel à **SQLSetPos**, et non lorsqu’elle est mise à jour par un autre curseur.  
  
 L’une des façons d’implémenter des curseurs dynamiques dans la base de données consiste à créer un index sélectif qui définit l’appartenance et l’ordre du jeu de résultats. Étant donné que l’index est mis à jour lorsque d’autres utilisateurs apportent des modifications, un curseur basé sur ce type d’index est sensible à toutes les modifications. Une sélection supplémentaire dans le jeu de résultats défini par cet index est possible en traitant le long de l’index.  
  
 Les curseurs dynamiques peuvent être simulés en exigeant que le jeu de résultats soit classé par une clé unique. Avec une telle restriction, les extractions sont effectuées en exécutant une instruction **Select** chaque fois que le curseur extrait des lignes. Par exemple, supposons que le jeu de résultats est défini par l’instruction suivante :  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Pour extraire l’ensemble de lignes suivant dans ce jeu de résultats, le curseur simulé définit les paramètres de l’instruction **Select** suivante sur les valeurs de la dernière ligne de l’ensemble de lignes actif, puis l’exécute :  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Cette instruction crée un deuxième jeu de résultats, le premier ensemble de lignes qui est l’ensemble de lignes suivant dans le jeu de résultats d’origine. dans ce cas, il s’agit de l’ensemble de lignes de la table Customers. Le curseur retourne cet ensemble de lignes à l’application.  
  
 Il est intéressant de noter qu’un curseur dynamique implémenté de cette manière crée en fait de nombreux jeux de résultats, ce qui lui permet de détecter les modifications apportées au jeu de résultats d’origine. L’application n’apprend jamais l’existence de ces jeux de résultats auxiliaires. Il apparaît simplement comme si le curseur est en mesure de détecter les modifications apportées au jeu de résultats d’origine.
