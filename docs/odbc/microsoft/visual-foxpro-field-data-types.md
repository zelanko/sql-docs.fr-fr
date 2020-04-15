---
title: Types de données visuelles sur le terrain FoxPro (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72313e0269c93bca9cb2561d89604c3c88c8567b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304800"
---
# <a name="visual-foxpro-field-data-types"></a>Types de données Visual FoxPro
Le tableau suivant énumère les valeurs de l’argument *FieldType* dans ALTER TABLE et CREATE TABLE et indique si les arguments *nFieldWidth* et *nPrecision* sont nécessaires.  
  
|*FieldType (FieldType)*|*NFieldWidth (en)*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Champ de caractère de largeur *n*|  
|D|-|-|Date|  
|F|N|d|Champ numérique flottant de largeur *n* avec des places décimales *d*|  
|G|-|-|Général|  
|I|-|-|Integer|  
|L|-|-|Logical|  
|M|-|-|Mémo|  
|N|N|d|Champ numérique de largeur *n* avec des places décimales *d*|  
|T|-|-|DateTime|  
|O|-|-|Devise|
