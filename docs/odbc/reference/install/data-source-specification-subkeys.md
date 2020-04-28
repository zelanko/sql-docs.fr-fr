---
title: Sous-clés de spécification de source de données | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300339"
---
# <a name="data-source-specification-subkeys"></a>Sous-clés de spécification de source de données
Chaque source de données figurant dans la sous-clé de sources de données ODBC possède sa propre sous-clé. Cette sous-clé porte le même nom que la valeur correspondante dans la sous-clé de sources de données ODBC. Les valeurs sous cette sous-clé doivent répertorier la DLL du pilote et peuvent répertorier une description de la source de données. Si le pilote prend en charge les traducteurs, les valeurs peuvent répertorier le nom d’un convertisseur par défaut, la DLL de traduction par défaut et l’option de traduction par défaut. Les valeurs peuvent également répertorier d’autres informations requises par le pilote pour la connexion à la source de données. Par exemple, le pilote peut nécessiter un nom de serveur, un nom de base de données ou un nom de schéma.  
  
 Les formats des valeurs sont répertoriés dans le tableau suivant. Seule la valeur Driver est requise.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|Description|REG_SZ|*descriptive*|  
|Pilote|REG_SZ|*Driver-DLL-Path*|  
|TranslationDLL|REG_SZ|*Traducteur-DLL-chemin*|  
|TranslationName|REG_SZ|*Traducteur-nom*|  
|TranslationOption|REG_SZ|*option de traduction*|  
|*opt-Value-Name*|*opt-value-type*|*opt-value-Data*|  
  
 Supposons, par exemple, que le pilote SQL Server nécessite le nom du serveur et un indicateur pour la conversion OEM en ANSI et définit les valeurs Server et OEMTOANSI pour celles-ci. Supposons également que la source de données d’inventaire utilise le traducteur de pages de codes Microsoft® pour effectuer la conversion entre les pages de codes Windows® latin 1 (1250) et multilingue (850). Les valeurs sous la sous-clé Inventory peuvent être les suivantes :  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
