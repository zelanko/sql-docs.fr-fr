---
title: ODBC Drivers Subkey - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304030"
---
# <a name="odbc-drivers-subkey"></a>Sous-clé des pilotes ODBC
Les valeurs sous la sous-liste ODBC Drivers sont les pilotes installés. Le format de ces valeurs est affiché dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*description du conducteur*|REG_SZ|**Installé**|  
  
 Le nom *de description du conducteur* est défini par le développeur du conducteur. C’est généralement le nom du DBMS associé au conducteur.  
  
 Supposons, par exemple, que les conducteurs aient été installés pour des fichiers texte formatés et SQL Server. Les valeurs sous le sous-clé ODBC Drivers pourraient être les :  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
