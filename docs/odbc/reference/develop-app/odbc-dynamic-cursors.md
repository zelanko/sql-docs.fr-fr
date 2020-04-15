---
title: Cursors dynamiques de l’ODBC (fr) Microsoft Docs
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
ms.openlocfilehash: f94b83ef1458cd9f8368d1bea3a39682bd80b1a2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302321"
---
# <a name="odbc-dynamic-cursors"></a>Curseurs dynamiques dans ODBC
Un curseur dynamique est juste que: dynamique. Il peut détecter les modifications apportées à l’adhésion, à l’ordre et aux valeurs du résultat fixé après l’ouverture du curseur. Par exemple, supposez qu’un curseur dynamique extrait deux lignes et qu’une autre application met ensuite à jour l’une de ces lignes et supprime l’autre. Si le curseur dynamique tente alors de réfélériser ces lignes, il ne trouvera pas la ligne supprimée, mais retournera les nouvelles valeurs pour la ligne mise à jour.  
  
 Les curseurs dynamiques détectent toutes les mises à jour, les suppressions et les inserts, les leurs et ceux fabriqués par d’autres. (Cela est soumis au niveau d’isolement de la transaction, tel que défini par l’attribut de connexion SQL_ATTR_TXN_ISOLATION.) Le tableau d’état de la ligne spécifié par l’attribut de l’instruction SQL_ATTR_ROW_STATUS_PTR reflète ces modifications et peut contenir des SQL_ROW_SUCCESS, des SQL_ROW_SUCCESS_WITH_INFO, des SQL_ROW_ERROR, des SQL_ROW_UPDATED et des SQL_ROW_ADDED. Il ne peut pas retourner SQL_ROW_DELETED parce qu’un curseur dynamique ne retourne pas les lignes supprimées à l’extérieur de la ligne et ne reconnaît donc plus l’existence de la ligne supprimée dans l’ensemble de résultat ou son élément correspondant dans le tableau d’état de la ligne. SQL_ROW_ADDED n’est retourné que lorsqu’une ligne est mise à jour par un appel à **SQLSetPos**, pas lorsqu’elle est mise à jour par un autre curseur.  
  
 Une façon de mettre en œuvre des curseurs dynamiques dans la base de données est de créer un indice sélectif qui définit les membres et la commande de l’ensemble de résultats. Étant donné que l’indice est mis à jour lorsque d’autres effectuent des modifications, un curseur basé sur un tel indice est sensible à tous les changements. Une sélection supplémentaire dans le résultat défini par cet indice est possible en traitant le long de l’indice.  
  
 Les curseurs dynamiques peuvent être simulés en exigeant que le résultat soit commandé par une clé unique. Avec une telle restriction, les allers chercher sont faits en exécutant une déclaration **SELECT** chaque fois que le curseur récupère des rangées. Supposons, par exemple, que l’ensemble de résultats soit défini par cette affirmation :  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Pour aller chercher le jeu de ligne suivant dans cet ensemble de résultats, le curseur simulé définit les paramètres de l’énoncé **SELECT** suivant aux valeurs de la dernière rangée de l’ensemble actuel, puis l’exécute :  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Cette déclaration crée un deuxième ensemble de résultats, dont le premier jeu de ligne est le jeu de ligne suivant dans l’ensemble de résultats d’origine - dans ce cas, l’ensemble de lignes dans le tableau des clients. Le curseur renvoie ce jeu de ligne à l’application.  
  
 Il est intéressant de noter qu’un curseur dynamique mis en œuvre de cette manière crée en fait de nombreux ensembles de résultats, ce qui lui permet de détecter les changements à l’ensemble de résultats d’origine. L’application n’apprend jamais de l’existence de ces ensembles de résultats auxiliaires; il apparaît simplement comme si le curseur est capable de détecter les changements à l’ensemble de résultat d’origine.
