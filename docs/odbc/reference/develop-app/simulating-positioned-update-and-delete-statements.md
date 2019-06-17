---
title: Simulation positionné instructions Update et Delete | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- row identifiers [ODBC]
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d98d40ae24c68f90a304edb0293febfe76fac2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445891"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulation d’instructions de mise à jour et de suppression positionnées
Si la source de données ne pas prendre en charge la mise à jour positionnée et supprimer des instructions, le pilote peut simuler ces. Par exemple, la bibliothèque de curseurs ODBC simule la mise à jour positionnée et supprimer des instructions. La stratégie générale pour simuler une mise à jour positionnée instructions et suppression consiste à convertir les instructions positionnées à ceux recherchés. Cela est effectué en remplaçant le **WHERE CURRENT OF** clause avec une recherche **où** clause qui identifie la ligne actuelle.  
  
 Par exemple, étant donné que la colonne CustID identifie de façon unique chaque ligne dans la table Customers, la positionnées instruction delete  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 peut être converti en  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Le pilote peut utiliser une de ces *d’identificateurs de lignes* dans le **où** clause :  
  
-   Colonnes dont les valeurs servent à identifier de façon unique chaque ligne dans la table. Par exemple, l’appel **SQLSpecialColumns** avec SQL_BEST_ROWID retourne la colonne ou jeu optimal de colonnes qui correspondent à cet effet.  
  
-   Pseudo-colonnes, fournis par certaines sources de données, à des fins d’identifiant de manière unique chaque ligne. Il ne peuvent également être récupérés en appelant **SQLSpecialColumns**.  
  
-   Un index unique, si elle est disponible.  
  
-   Toutes les colonnes du jeu de résultats.  
  
 Exactement quelles colonnes un pilote doit utiliser dans le **où** clause il construit dépend du pilote. Sur certaines données sources, de déterminer un identificateur de ligne peuvent être coûteuses. Toutefois, il est plus rapide d’exécuter et garantit qu’une instruction simulée met à jour ou supprime une ligne au plus. Selon les capacités du SGBD sous-jacent, à l’aide d’un identificateur de ligne peut être coûteux à configurer. Toutefois, il est plus rapide d’exécuter et garantit qu’une instruction simulée sera mise à jour ou supprimer qu’une seule ligne. La possibilité d’utiliser toutes les colonnes du jeu de résultats est généralement beaucoup plus facile à configurer. Toutefois, il est plus lent à exécuter et, si les colonnes n’identifient pas une ligne, peut entraîner des lignes ne soient involontairement mis à jour ou supprimées, en particulier lorsque la liste de sélection pour le résultat de la valeur ne contient-elle pas toutes les colonnes qui existent dans la table sous-jacente.  
  
 En fonction de laquelle des stratégies précédentes le pilote prend en charge, une application peut choisir quelle stratégie qu’il veut le pilote à utiliser avec l’attribut d’instruction SQL_ATTR_SIMULATE_CURSOR. Bien qu’il peut sembler étrange pour une application à courir le risque involontairement la mise à jour ou suppression d’une ligne, l’application peut supprimer ce risque en veillant à ce que les colonnes du jeu de résultats identifient de manière unique chaque ligne du jeu de résultats. Cela permet d’économiser le pilote l’effort d’avoir à le faire.  
  
 Si le pilote choisit d’utiliser un identificateur de ligne, il intercepte la **SELECT FOR UPDATE** instruction qui crée le jeu de résultats. Si les colonnes dans la liste select n’identifient pas efficacement une ligne, le pilote ajoute les colonnes nécessaires à la fin de la liste de sélection. Certaines sources de données ont une colonne unique qui identifie le toujours une ligne, telles que la colonne ROWID dans Oracle. Si une telle colonne est disponible, le pilote utilise ceci. Sinon, le pilote appelle **SQLSpecialColumns** pour chaque table dans le **FROM** clause pour récupérer une liste des colonnes qui identifient de façon unique chaque ligne. Une restriction du common qui résulte de cette technique est que la simulation de curseur échoue s’il existe plusieurs tables dans le **FROM** clause.  
  
 Quelle que soit la façon dont le pilote identifie les lignes, il supprime généralement la **FOR UPDATE OF** clause désactivé le **SELECT FOR UPDATE** instruction avant de les envoyer à la source de données. Le **pour mettre à jour de** clause est utilisée uniquement avec positionné mise à jour et supprimer des instructions. Sources de données ne prenant pas en charge positionné mise à jour et instructions delete généralement ne pas en charge.  
  
 Lorsque l’application envoie une mise à jour positionnée ou une instruction delete pour l’exécution, le pilote remplace le **WHERE CURRENT OF** clause avec un **où** clause contenant l’identificateur de ligne. Les valeurs de ces colonnes sont récupérées à partir d’un cache géré par le pilote pour chaque colonne, il utilise dans les **où** clause. Une fois que le pilote a remplacé le **où** clause, il envoie l’instruction à la source de données pour l’exécution.  
  
 Par exemple, supposons que l’application soumet l’instruction suivante pour créer un jeu de résultats :  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Si l’application a la valeur SQL_ATTR_SIMULATE_CURSOR pour demander une garantie d’unicité et si la source de données ne fournit pas une pseudo-colonne qui identifie le toujours une ligne, le pilote appelle **SQLSpecialColumns** pour le Table Customers, découvre que CustID est la clé à la table Customers et il ajoute à la liste de sélection et supprime la **FOR UPDATE OF** clause :  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Si l’application n’a pas demandé une garantie d’unicité, le pilote supprime uniquement le **FOR UPDATE OF** clause :  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Supposons que l’application fait défile le jeu de résultats et soumet l’instruction de mise à jour positionnée suivante pour l’exécution, où le client est le nom du curseur sur le jeu de résultats :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Si l’application n’a pas demandé une garantie d’unicité, le pilote remplace le **où** clause et lie le paramètre CustID à la variable dans son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Si l’application n’a pas demandé une garantie d’unicité, le pilote remplace le **où** clause et lie les paramètres de nom, adresse et téléphone dans cette clause pour les variables dans son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
