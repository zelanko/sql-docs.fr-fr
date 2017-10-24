---
title: "Qu’est un verrou ? | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f4975dd903c6d012976f9288b9758e1acab52f1f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="what-is-a-lock"></a>Qu’est un verrou ?
Le verrouillage est le processus par lequel un SGBD limite l’accès à une ligne dans un environnement multi-utilisateur. Lorsqu’une ligne ou une colonne est verrouillée en mode exclusif, les autres utilisateurs ne sont pas autorisés à accéder aux données verrouillées jusqu'à ce que le verrou est libéré. Cela garantit que deux utilisateurs ne peuvent pas mettre à jour simultanément la même colonne dans une ligne.  
  
 Les verrous peuvent être très coûteuses du point de vue de la ressource et doivent être utilisés uniquement si nécessaire pour conserver l’intégrité des données. Dans une base de données où des centaines, voire des milliers d’utilisateurs essaie d’accéder à un enregistrement de chaque seconde, comme une base de données connectés à Internet, donc baisse des performances dans votre application.  
  
 Vous pouvez contrôler la façon dont la source de données et la bibliothèque de curseurs ADO gérer l’accès concurrentiel en choisissant l’option de verrouillage appropriée.  
  
 Définir le **LockType** propriété avant d’ouvrir un **Recordset** pour spécifier le type de verrouillage que le fournisseur doit utiliser pour l’ouvrir. Lire la propriété pour retourner le type de verrouillage en cours d’utilisation sur open **Recordset** objet.  
  
 Les fournisseurs ne peuvent pas en charge tous les types de verrous. Si un fournisseur ne peut pas prendre en charge demandé **LockType** définition, il remplacera un autre type de verrouillage. Pour déterminer les fonctionnalités de verrouillage disponibles dans un **Recordset** de l’objet, utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) méthode avec **adUpdate** et **adUpdateBatch**.  
  
 Le **adLockPessimistic** paramètre n’est pas pris en charge si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) est définie sur **adUseClient.** Si une valeur non prise en charge est définie, aucune erreur se produira ; prise en charge la plus proche **LockType** sera utilisé à la place.  
  
 Le **LockType** propriété est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de verrous](../../../ado/guide/data/types-of-locks.md)

