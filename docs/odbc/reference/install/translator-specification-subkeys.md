---
title: Subkeys de spécifications de traducteurs (fr) Microsoft Docs
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
ms.openlocfilehash: ad21943c5313edcb09aba88d45ea21132aa9757f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296039"
---
# <a name="translator-specification-subkeys"></a>Sous-clés de spécification de convertisseur
Chaque traducteur répertorié dans le sous-clé ODBC Translators a une sous-clé à part entière. Ce sous-clé a le même nom que la valeur correspondante sous le sous-clé ODBC Translators. Les valeurs sous cette sous-clé répertorient les chemins complets des DLL de configuration de traducteur et de traducteur et le nombre d’utilisation. Les formats des valeurs sont tels qu’indiqués dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Convertisseur|REG_SZ|*traducteur-DLL-chemin*|  
|Programme d’installation|REG_SZ|*configuration-DLL-chemin*|  
|UtilisationCompte|REG_DWORD|*count*|  
  
 Pour plus d’informations sur les comptes d’utilisation, voir [Compter l’utilisation](../../../odbc/reference/install/usage-counting.md) plus tôt dans cette section.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC maintiendra ce décompte.  
  
 Supposons, par exemple, que le traducteur de page de code Microsoft a une traduction DLL nommée Mscpxl32.dll, que les fonctions de configuration du traducteur sont dans la même DLL, et que le traducteur a été installé trois fois. Les valeurs sous la sous-clé Microsoft Code Page Translator peuvent être les suivantes :  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
