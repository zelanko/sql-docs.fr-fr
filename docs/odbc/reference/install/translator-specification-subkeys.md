---
title: Sous-clés de la spécification du traducteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec94f3e02b720617e8f7369b12a916c2bbbe7b16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093797"
---
# <a name="translator-specification-subkeys"></a>Sous-clés de spécification de convertisseur
Chaque traducteur listé dans la sous-clé ODBC Translators possède sa propre sous-clé. Cette sous-clé porte le même nom que la valeur correspondante dans la sous-clé ODBC Translators. Les valeurs de cette sous-clé répertorient les chemins complets des dll de configuration du traducteur et du traducteur, ainsi que le nombre d’utilisations. Les formats des valeurs sont répertoriés dans le tableau suivant.  
  
|Name|Type de données|Données|  
|----------|---------------|----------|  
|Traducteur|REG_SZ|*Traducteur-DLL-chemin*|  
|Installation|REG_SZ|*Setup-DLL-Path*|  
|UsageCount|REG_DWORD|*saut*|  
  
 Pour plus d’informations sur le nombre d’utilisations, consultez [utilisation du comptage](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC conservera ce nombre.  
  
 Par exemple, supposons que le traducteur de pages de codes Microsoft possède une DLL de traduction nommée mscpxl32. dll, que les fonctions de configuration du traducteur se trouvent dans la même DLL et que le traducteur ait été installé trois fois. Les valeurs sous la sous-clé de traduction de page de codes Microsoft peuvent être les suivantes :  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
