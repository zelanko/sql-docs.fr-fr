---
description: Simulation d’instructions de mise à jour et de suppression positionnées
title: Simulation des instructions Update et DELETE positionnées | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06f6faad1b5b6cb83616575ea8732cac98b88ed0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499812"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulation d’instructions de mise à jour et de suppression positionnées
Si la source de données ne prend pas en charge les instructions Update et DELETE positionnées, le pilote peut les simuler. Par exemple, la bibliothèque de curseurs ODBC simule les instructions Update et DELETE positionnées. La stratégie générale de simulation des instructions de mise à jour et de suppression positionnées consiste à convertir les instructions positionnées en recherches. Pour ce faire, remplacez la clause **Where Current of** par une clause **Where** recherchée qui identifie la ligne actuelle.  
  
 Par exemple, étant donné que la colonne CustID identifie de manière unique chaque ligne dans la table Customers, l’instruction DELETE positionnée  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 peut être converti en  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Le pilote peut utiliser l’un des *identificateurs de ligne* suivants dans la clause **Where** :  
  
-   Colonnes dont les valeurs servent à identifier de manière unique chaque ligne dans la table. Par exemple, l’appel de **SQLSpecialColumns** avec SQL_BEST_ROWID retourne la colonne ou l’ensemble de colonnes optimal à cet effet.  
  
-   Les pseudo-colonnes, fournies par certaines sources de données, à des fins d’identification unique de chaque ligne. Elles peuvent également être récupérées en appelant **SQLSpecialColumns**.  
  
-   Index unique, s’il est disponible.  
  
-   Toutes les colonnes du jeu de résultats.  
  
 Les colonnes précises qu’un pilote doit utiliser dans la clause **Where** qu’il construit dépend du pilote. Sur certaines sources de données, la détermination d’un identificateur de ligne peut être coûteuse. Toutefois, il est plus rapide d’exécuter et garantit qu’une instruction simulée est mise à jour ou supprimée au plus une ligne. Selon les capacités du SGBD sous-jacent, l’utilisation d’un identificateur de ligne peut être coûteuse à configurer. Toutefois, il est plus rapide de s’exécuter et garantit qu’une instruction simulée met à jour ou supprime une seule ligne. L’option d’utilisation de toutes les colonnes dans le jeu de résultats est généralement beaucoup plus facile à configurer. Toutefois, l’exécution est plus lente et, si les colonnes n’identifient pas de manière unique une ligne, peut entraîner la mise à jour ou la suppression de lignes involontairement, en particulier lorsque la liste de sélection du jeu de résultats ne contient pas toutes les colonnes qui existent dans la table sous-jacente.  
  
 Selon les stratégies précédentes prises en charge par le pilote, une application peut choisir la stratégie qu’elle souhaite que le pilote utilise avec l’attribut d’instruction SQL_ATTR_SIMULATE_CURSOR. Bien qu’il puisse paraître étrange pour une application de mettre à jour ou de supprimer involontairement une ligne, l’application peut supprimer ce risque en s’assurant que les colonnes du jeu de résultats identifient de manière unique chaque ligne dans le jeu de résultats. Cela évite au pilote d’avoir à le faire.  
  
 Si le pilote choisit d’utiliser un identificateur de ligne, il intercepte l’instruction **Select for Update** qui crée le jeu de résultats. Si les colonnes de la liste de sélection n’identifient pas efficacement une ligne, le pilote ajoute les colonnes nécessaires à la fin de la liste de sélection. Certaines sources de données ont une seule colonne qui identifie toujours de façon unique une ligne, telle que la colonne ROWID dans Oracle ; Si une colonne de ce type est disponible, le pilote utilise cette. Dans le cas contraire, le pilote appelle **SQLSpecialColumns** pour chaque table de la clause **from** pour récupérer une liste des colonnes qui identifient de manière unique chaque ligne. Une restriction courante qui résulte de cette technique est que la simulation de curseur échoue s’il existe plusieurs tables dans la clause **from** .  
  
 Quelle que soit la façon dont le pilote identifie les lignes, il supprime généralement le **pour la mise à jour de** la clause de l’instruction **Select for Update** avant de l’envoyer à la source de données. La clause **for Update of** est utilisée uniquement avec les instructions Update et DELETE positionnées. Les sources de données qui ne prennent pas en charge les instructions de mise à jour et de suppression positionnées ne la prennent généralement pas en charge.  
  
 Lorsque l’application envoie une instruction UPDATE ou DELETE positionnée pour exécution, le pilote remplace la clause **Where Current of** par une clause **Where** contenant l’identificateur de ligne. Les valeurs de ces colonnes sont extraites d’un cache conservé par le pilote pour chaque colonne utilisée dans la clause **Where** . Une fois que le pilote a remplacé la clause **Where** , il envoie l’instruction à la source de données pour exécution.  
  
 Supposons, par exemple, que l’application envoie l’instruction suivante pour créer un jeu de résultats :  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Si l’application a défini SQL_ATTR_SIMULATE_CURSOR pour demander une garantie d’unicité et que la source de données ne fournit pas de Pseudo-colonne qui identifie toujours une ligne de manière unique, le pilote appelle **SQLSpecialColumns** pour la table Customers, découvre que CustID est la clé de la table Customers et l’ajoute à la liste de sélection, et supprime le **pour la mise à jour de** la clause :  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Si l’application n’a pas demandé de garantie d’unicité, le pilote supprime uniquement les éléments **pour la mise à jour de** la clause :  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Supposons que l’application fait défiler le jeu de résultats et envoie l’instruction de mise à jour positionnée suivante pour exécution, où cust est le nom du curseur sur le jeu de résultats :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Si l’application n’a pas demandé de garantie d’unicité, le pilote remplace la clause **Where** et lie le paramètre CustID à la variable dans son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Si l’application n’a pas demandé de garantie d’unicité, le pilote remplace la clause **Where** et lie les paramètres Name, Address et Phone dans cette clause aux variables dans son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
