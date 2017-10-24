---
title: "Propriétés dynamiques du jeu d’enregistrements au format XML | Documents Microsoft"
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
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62d9b59fc1145e09f89bbe69b8d7b6e561798e70
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-dynamic-properties-in-xml"></a>Propriétés dynamiques du jeu d’enregistrements au format XML
Actuellement, les propriétés spécifiques au fournisseur de Recordset suivantes (à partir du moteur de curseur Client) sont conservées au format XML :  
  
-   Resynchronisation de la mise à jour  
  
-   Table unique  
  
-   Schéma unique  
  
-   Catalogue unique  
  
-   Resynchronisation des commandes  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Modifier la forme nom  
  
-   AutoRecalc  
  
 Ces propriétés sont enregistrées dans la section de schéma en tant qu’attributs de la définition d’élément du jeu d’enregistrements persistant. Ces attributs sont définis dans l’espace de noms de schéma d’ensemble de lignes et doit avoir le préfixe « rs : ».  
  
## <a name="see-also"></a>Voir aussi  
 [Maintien d’enregistrements au Format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)

