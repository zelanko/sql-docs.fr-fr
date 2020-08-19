---
description: Sous-clé des pilotes ODBC
title: Sous-clé des pilotes ODBC | Microsoft Docs
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
ms.openlocfilehash: b950a352c3da69a2a8de9a89f7bbebf87e0a597a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448919"
---
# <a name="odbc-drivers-subkey"></a>Sous-clé des pilotes ODBC
Les valeurs de la sous-clé pilotes ODBC répertorient les pilotes installés. Le format de ces valeurs est indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*Description du pilote*|REG_SZ|**Installé**|  
  
 Le nom *de la description du pilote* est défini par le développeur du pilote. Il s’agit généralement du nom du SGBD associé au pilote.  
  
 Par exemple, supposons que des pilotes ont été installés pour les fichiers texte mis en forme et les SQL Server. Les valeurs sous la sous-clé pilotes ODBC peuvent être :  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
