---
title: Sous-clés de spécification de traducteur | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093797"
---
# <a name="translator-specification-subkeys"></a>Sous-clés de spécification de convertisseur
Chaque convertisseur répertorié dans la sous-clé de convertisseurs de ODBC a une sous-clé de son propre. Cette sous-clé a le même nom que la valeur correspondante sous la sous-clé ODBC traducteurs. Les valeurs sous cette sous-clé répertorient les chemins complets du traducteur et le programme d’installation de traducteur DLL et le décompte d’utilisation. Les formats des valeurs sont comme indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Convertisseur|REG_SZ|*chemin de DLL de traduction*|  
|Installation|REG_SZ|*le programme d’installation-DLL-path*|  
|UsageCount|REG_DWORD|*nombre*|  
  
 Pour plus d’informations sur les compteurs d’utilisation, consultez [nombre d’utilisations](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Applications ne doivent pas définir le décompte d’utilisation. ODBC gère ce nombre.  
  
 Par exemple, supposons que la Page de Code Microsoft Translator a une DLL nommée Mscpxl32.dll, situés dans la même DLL, les fonctions de configuration de traducteur de traduction et que le traducteur a été installé trois fois. Les valeurs sous la sous-clé de la Page de Code Microsoft Translator peuvent être comme suit :  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
