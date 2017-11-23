---
title: "Types de données Visual FoxPro | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b4dbb88985b114e0e2f89c4a3f57d8dae4c9210
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="visual-foxpro-field-data-types"></a>Types de données Visual FoxPro
Le tableau suivant répertorie les valeurs pour le *FieldType* argument dans l’instruction ALTER TABLE et CREATE TABLE et indique si *nFieldWidth* et *nPrecision* arguments sont requis.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*| Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Champ de caractères de largeur*n*|  
|D|-|-|Date|  
|F|N|d|Flottante champ numérique de largeur  *n*  avec *d* décimales|  
|G|-|-|Général|  
|I|-|-|Entier|  
|L|-|-|Logical|  
|M|-|-|Mémo|  
|N|N|d|Un champ numérique de largeur  *n*  avec *d* décimales|  
|T|-|-|DateTime|  
|O|-|-|Monétaire (Currency)|
