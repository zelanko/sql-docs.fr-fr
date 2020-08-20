---
description: Sous-clés de spécification de convertisseur
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c02317c8abe12dbc693cdf7b715b6de84e5bc631
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461291"
---
# <a name="translator-specification-subkeys"></a>Sous-clés de spécification de convertisseur
Chaque traducteur listé dans la sous-clé ODBC Translators possède sa propre sous-clé. Cette sous-clé porte le même nom que la valeur correspondante dans la sous-clé ODBC Translators. Les valeurs de cette sous-clé répertorient les chemins complets des dll de configuration du traducteur et du traducteur, ainsi que le nombre d’utilisations. Les formats des valeurs sont répertoriés dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Traducteur|REG_SZ|*Traducteur-DLL-chemin*|  
|Programme d’installation|REG_SZ|*Setup-DLL-Path*|  
|UsageCount|REG_DWORD|*count*|  
  
 Pour plus d’informations sur le nombre d’utilisations, consultez [utilisation du comptage](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC conservera ce nombre.  
  
 Par exemple, supposons que le traducteur de pages de codes Microsoft possède une DLL de traduction nommée Mscpxl32.dll, que les fonctions de configuration du traducteur se trouvent dans la même DLL et que le traducteur ait été installé trois fois. Les valeurs sous la sous-clé de traduction de page de codes Microsoft peuvent être les suivantes :  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
