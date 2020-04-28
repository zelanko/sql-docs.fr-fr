---
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
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304030"
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
