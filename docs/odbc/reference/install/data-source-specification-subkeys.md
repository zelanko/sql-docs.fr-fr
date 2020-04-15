---
title: Sous-vêtements de spécifications de source de données (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 281377c307f3f3750e87bf5dc988beb7660067af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300339"
---
# <a name="data-source-specification-subkeys"></a>Sous-clés de spécification de source de données
Chaque source de données répertoriée dans le sous-clé ODBC Data Sources a une sous-clé à part entière. Ce sous-clé a le même nom que la valeur correspondante sous le sous-marin ODBC Data Sources. Les valeurs sous cette sous-clé doivent énumérer le pilote DLL et peut énumérer une description de la source de données. Si le pilote prend en charge les traducteurs, les valeurs peuvent énumérer le nom d’un traducteur par défaut, la traduction par défaut DLL et l’option de traduction par défaut. Les valeurs peuvent également énumérer les autres informations requises par le conducteur pour se connecter à la source de données. Par exemple, le pilote peut avoir besoin d’un nom de serveur, d’un nom de base de données ou d’un nom de schéma.  
  
 Les formats des valeurs sont tels qu’indiqués dans le tableau suivant. Seule la valeur du pilote est requise.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Description|REG_SZ|*Description*|  
|Pilote|REG_SZ|*conducteur-DLL-chemin*|  
|TraductionDLL|REG_SZ|*traducteur-DLL-chemin*|  
|TranslationName (en)|REG_SZ|*nom de traducteur*|  
|TraductionOption|REG_SZ|*traduction-option*|  
|*nom opt-value*|*opt-value-type*|*opt-value-data*|  
  
 Supposons, par exemple, que le pilote DE serveur SQL nécessite le nom du serveur et un drapeau pour la conversion OEM à la conversion ANSI et définit les valeurs Server et OEMTOANSI pour ceux-ci. Supposons également que la source de données Inventory utilise le traducteur de page de code Microsoft® pour traduire entre les pages de code Windows® Latin 1 (1250) et Multilingual (850). Les valeurs sous la sous-clé d’inventaire peuvent être les suivantes :  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
