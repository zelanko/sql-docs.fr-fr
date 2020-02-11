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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 217058bf328677bf375d346ae7201c6eb81efa4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087956"
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
|M|-|-|Champs|  
|N|N|d|Champ numérique de largeur *n* avec des décimales *d*|  
|T|-|-|DateTime|  
|O|-|-|Devise|
