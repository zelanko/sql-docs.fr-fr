---
title: Propriétés dynamiques du Recordset dans XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b58a9463932e9761688fd744b972f50ad3286381
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718684"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Propriétés dynamiques du recordset dans XML
Les propriétés spécifiques au fournisseur Recordset suivantes (provenant du moteur de curseur Client) sont actuellement conservées au format XML :  
  
-   Resynchronisation de la mise à jour  
  
-   table unique  
  
-   Schéma unique  
  
-   Catalogue unique  
  
-   Resync, commande  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Modifier la forme nom  
  
-   AutoRecalc  
  
 Ces propriétés sont enregistrées dans la section de schéma en tant qu’attributs de la définition d’élément du jeu d’enregistrements en cours de persistance. Ces attributs sont définis dans l’espace de noms de schéma d’ensemble de lignes et doit avoir le préfixe « rs : ».  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
