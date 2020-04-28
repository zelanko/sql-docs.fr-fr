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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5e97e643a78187b15e91833c832cd16ca435c7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304055"
---
# <a name="odbc-data-sources-subkey"></a>Sous-clé de sources de données ODBC

Les valeurs sous la `ODBC Data Sources` sous-clé répertorient les sources de données. Le format de ces valeurs est indiqué dans le tableau suivant.

| Nom | Type de données | Données |
| :--- | :-------- | :--- |
| *nom de la source de données* | REG_SZ | *Description du pilote* |
| &nbsp; | &nbsp; | &nbsp; |

La valeur de *nom de la source de données* est définie par le programme d’administration (qui invite habituellement l’utilisateur) et la *Description du pilote* est définie par le développeur du pilote (il s’agit généralement du nom du SGBD associé au pilote).

Par exemple, supposons que trois sources de données ont été définies : Inventory, qui utilise SQL Server ; La paie, qui utilise dBASE ; et le personnel, qui utilise des fichiers texte mis en forme. Les valeurs sous la `ODBC Data Sources` sous-clé peuvent être les suivantes :

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
