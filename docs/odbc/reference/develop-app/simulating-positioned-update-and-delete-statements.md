---
title: Simuler des mises à jour positionnées et supprimer les déclarations (fr) Microsoft Docs
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
ms.openlocfilehash: e1eb498a99180d145147e67c8955eeb7a0027024
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301990"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulation d’instructions de mise à jour et de suppression positionnées
Si la source de données ne prend pas en charge la mise à jour positionnée et supprime les instructions, le pilote peut les simuler. Par exemple, la bibliothèque de curseurs ODBC simule la mise à jour positionnée et supprime les instructions. La stratégie générale de simulation des mises à jour positionnées et de supprimer les déclarations consiste à convertir les relevés positionnés en énoncés recherchés. Ceci est fait en remplaçant la clause **WHERE CURRENT OF** par une clause **WHERE** recherchée qui identifie la ligne actuelle.  
  
 Par exemple, parce que la colonne CustID identifie de façon unique chaque ligne dans le tableau des clients, l’instruction de suppression positionnée  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 pourrait être converti en  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Le conducteur peut utiliser l’un des *identificateurs* de ligne suivants dans la clause **WHERE** :  
  
-   Colonnes dont les valeurs servent à identifier uniquement chaque rangée dans la table. Par exemple, appeler **SQLSpecialColumns** avec SQL_BEST_ROWID renvoie la colonne optimale ou l’ensemble de colonnes qui servent à cet effet.  
  
-   Pseudo-colonnes, fournies par certaines sources de données, dans le but d’identifier uniquement chaque ligne. Ceux-ci peuvent également être récupérables en appelant **SQLSpecialColumns**.  
  
-   Un index unique, s’il est disponible.  
  
-   Toutes les colonnes dans l’ensemble de résultat.  
  
 Exactement les colonnes qu’un conducteur doit utiliser dans la clause **WHERE** qu’il construit dépend du conducteur. Sur certaines sources de données, la détermination d’un identifiant de ligne peut être coûteuse. Cependant, il est plus rapide d’exécuter et garantit qu’une déclaration simulée met à jour ou supprime tout au plus une rangée. Selon les capacités du DBMS sous-jacent, l’utilisation d’un identifiant de ligne peut être coûteuse à configurer. Cependant, il est plus rapide d’exécuter et garantit qu’une déclaration simulée mettra à jour ou supprimera une seule ligne. L’option d’utiliser toutes les colonnes dans l’ensemble de résultat est généralement beaucoup plus facile à configurer. Cependant, il est plus lent à exécuter et, si les colonnes n’identifient pas uniquement une ligne, peut entraîner des lignes étant involontairement mis à jour ou supprimé, surtout lorsque la liste de sélection pour l’ensemble de résultat ne contient pas toutes les colonnes qui existent dans le tableau sous-jacent.  
  
 Selon les stratégies précédentes que prend le conducteur, une application peut choisir la stratégie qu’il souhaite que le conducteur utilise avec l’attribut SQL_ATTR_SIMULATE_CURSOR déclaration. Bien qu’il puisse sembler étrange pour une application de risquer involontairement mise à jour ou supprimer une ligne, l’application peut supprimer ce risque en s’assurant que les colonnes dans l’ensemble de résultat identifient uniquement chaque ligne dans l’ensemble de résultat. Cela permet au conducteur d’essayer de le faire.  
  
 Si le pilote choisit d’utiliser un identifiant de ligne, il intercepte la déclaration **SELECT FOR UPDATE** qui crée l’ensemble de résultats. Si les colonnes de la liste de sélection n’identifient pas efficacement une ligne, le pilote ajoute les colonnes nécessaires à la fin de la liste de sélection. Certaines sources de données ont une seule colonne qui identifie toujours de façon unique une ligne, comme la colonne ROWID dans Oracle; si une telle colonne est disponible, le conducteur l’utilise. Sinon, le conducteur appelle **SQLSpecialColumns** pour chaque tableau de la clause **FROM** pour récupérer une liste des colonnes qui identifient uniquement chaque rangée. Une restriction commune qui résulte de cette technique est que la simulation de curseur échoue s’il y a plus d’un tableau dans la clause **FROM.**  
  
 Peu importe comment le conducteur identifie les lignes, il dépouille habituellement la clause **FOR UPDATE OF** de la déclaration SELECT FOR **UPDATE** avant de l’envoyer à la source de données. La clause **FOR UPDATE OF** n’est utilisée qu’avec des mises à jour positionnées et des relevés de suppression. Les sources de données qui ne prennent pas en charge les mises à jour et les relevés positionnés ne le prennent généralement pas en charge.  
  
 Lorsque la demande soumet une mise à jour ou une déclaration de suppression positionnée pour l’exécution, le conducteur remplace la clause **WHERE CURRENT OF** par une clause **WHERE** contenant l’identifiant de la ligne. Les valeurs de ces colonnes sont récupérées à partir d’un cache maintenu par le conducteur pour chaque colonne qu’il utilise dans la clause **WHERE.** Une fois que le conducteur a remplacé la clause **WHERE,** il envoie la déclaration à la source de données pour exécution.  
  
 Supposons, par exemple, que la demande soumette l’énoncé suivant pour créer un ensemble de résultats :  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Si l’application a mis SQL_ATTR_SIMULATE_CURSOR pour demander une garantie d’unicité et si la source de données ne fournit pas une pseudo-colonne qui identifie toujours de façon unique une ligne, le conducteur appelle **SQLSpecialColumns** pour la table des clients, découvre que CustID est la clé de la table des clients et ajoute cela à la liste de sélection, et dépouille la clause **FOR UPDATE OF:**  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Si la demande n’a pas demandé de garantie d’unicité, le conducteur ne supprime que la clause **FOR UPDATE OF** :  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Supposons que l’application défile l’ensemble de résultats et soumet l’énoncé de mise à jour positionnée suivant pour l’exécution, où Cust est le nom du curseur sur l’ensemble de résultat :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Si la demande n’a pas demandé de garantie d’unicité, le conducteur remplace la clause **WHERE** et lie le paramètre CustID à la variable dans son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Si la demande n’a pas demandé de garantie d’unicité, le conducteur remplace la clause **WHERE** et lie les paramètres nom, adresse et téléphone de cette clause aux variables de son cache :  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
