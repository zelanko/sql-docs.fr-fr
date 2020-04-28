---
title: Types de données de champ Visual FoxPro | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304800"
---
# <a name="visual-foxpro-field-data-types"></a>Types de données Visual FoxPro
Le tableau suivant répertorie les valeurs de l’argument *FieldType* dans ALTER table et Create table et indique si les arguments *nFieldWidth* et *nPrecision* sont obligatoires.  
  
|*Argument*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Champ de caractères de largeur *n*|  
|D|-|-|Date|  
|F|N|d|Champ numérique flottant de la largeur *n* avec des décimales *d*|  
|G|-|-|Général|  
|I|-|-|Integer|  
|L|-|-|Logical|  
|M|-|-|Mémo|  
|N|N|d|Champ numérique de largeur *n* avec des décimales *d*|  
|T|-|-|DateTime|  
|O|-|-|Devise|
