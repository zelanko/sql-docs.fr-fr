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
ms.openlocfilehash: a058a2d0c5a808f29807744c6ba01f658bebc120
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924444"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Propriétés dynamiques du recordset dans XML
Les propriétés suivantes spécifiques au fournisseur de l’ensemble d’enregistrements (à partir du moteur de curseur client) sont actuellement conservées au format XML :  
  
-   Mettre à jour la resynchronisation  
  
-   table unique  
  
-   Schéma unique  
  
-   Catalogue unique  
  
-   Commande Resync  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Reformer le nom  
  
-   AutoRecalc  
  
 Ces propriétés sont enregistrées dans la section du schéma en tant qu’attributs de la définition de l’élément pour le recordset à conserver. Ces attributs sont définis dans l’espace de noms du schéma de l’ensemble de lignes et doivent avoir le préfixe « rs : ».  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
