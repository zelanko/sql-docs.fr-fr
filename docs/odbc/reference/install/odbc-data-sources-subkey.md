---
title: Sous-clé des sources de données ODBC | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d6d54d1fc7c7742bf94e91d7370f356e28b5624
ms.sourcegitcommit: 816ff47eeab157c66e0f75f18897a63dc8033502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71207686"
---
# <a name="odbc-data-sources-subkey"></a>Sous-clé de sources de données ODBC

Les valeurs sous la `ODBC Data Sources` sous-clé répertorient les sources de données. Le format de ces valeurs est indiqué dans le tableau suivant.

| Nom | Type de données | Données |
| :--- | :-------- | :--- |
| *data-source-name* | REG_SZ | *driver-description* |
| &nbsp; | &nbsp; | &nbsp; |

La valeur de *nom de la source de données* est définie par le programme d’administration (qui invite habituellement l’utilisateur) et la *Description du pilote* est définie par le développeur du pilote (il s’agit généralement du nom du SGBD associé au pilote).

Par exemple, supposons que trois sources de données ont été définies : Inventory, qui utilise SQL Server ; La paie, qui utilise dBASE ; et le personnel, qui utilise des fichiers texte mis en forme. Les valeurs sous la `ODBC Data Sources` sous-clé peuvent être les suivantes :

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
