---
title: Sous-clés de spécification de la Source de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad210f91d00f9e692c8ee20fef01a808a01501c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706467"
---
# <a name="data-source-specification-subkeys"></a>Sous-clés de spécification de source de données
Chaque source de données répertoriée dans la sous-clé de Sources de données ODBC a une sous-clé de son propre. Cette sous-clé a le même nom que la valeur correspondante sous la sous-clé de Sources de données ODBC. Les valeurs sous cette sous-clé doivent répertorier la DLL du pilote et peuvent indiquer une description de la source de données. Si le pilote prend en charge les traducteurs, les valeurs peuvent répertorier le nom d’un convertisseur de valeur par défaut, la DLL de traduction par défaut et l’option de traduction par défaut. Les valeurs peuvent également énumérer les autres informations requises par le pilote pour se connecter à la source de données. Par exemple, le pilote peut nécessiter un nom de serveur, le nom de la base de données ou le nom de schéma.  
  
 Les formats des valeurs sont comme indiqué dans le tableau suivant. Seule la valeur du pilote est requise.  
  
|Nom   |Type de données|data|  
|----------|---------------|----------|  
|Description|REG_SZ|*description*|  
|Pilote|REG_SZ|*chemin de DLL de pilote*|  
|TranslationDLL|REG_SZ|*chemin de DLL de traduction*|  
|TranslationName|REG_SZ|*nom de la traduction*|  
|TranslationOption|REG_SZ|*option de traduction*|  
|*nom de valeur opt*|*type de valeur opt*|*données de valeur opt*|  
  
 Par exemple, le pilote SQL Server nécessite le nom du serveur et un indicateur pour OEM pour la conversion ANSI et définit les valeurs de serveur et OEMTOANSI pour ceux-ci. Supposons également que la source de données d’inventaire utilise le traducteur de Page de Code Microsoft® pour la translation entre le Windows® Latin 1 (1250) et les pages de codes multilingue (850). Les valeurs sous la sous-clé de stock peuvent être comme suit :  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
