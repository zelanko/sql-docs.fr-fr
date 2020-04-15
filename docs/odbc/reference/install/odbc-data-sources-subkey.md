---
title: ODBC Data Sources subkey (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304055"
---
# <a name="odbc-data-sources-subkey"></a>ODBC Data Sources subkey

Les valeurs `ODBC Data Sources` sous la liste sous-clé des sources de données. Le format de ces valeurs est affiché dans le tableau suivant.

| Nom | Type de données | Données |
| :--- | :-------- | :--- |
| *nom de source de données* | REG_SZ | *description du conducteur* |
| &nbsp; | &nbsp; | &nbsp; |

La valeur *de nom de source de données* est définie par le programme d’administration (qui invite habituellement l’utilisateur pour cela), et la description du *conducteur* est définie par le développeur conducteur (c’est généralement le nom de la DBMS associée au conducteur).

Supposons, par exemple, que trois sources de données aient été définies : l’inventaire, qui utilise SQL Server; La paie, qui utilise dBASE; et le personnel, qui utilise des fichiers texte formatés. Les valeurs `ODBC Data Sources` sous le sous-clé peuvent être les suivantes :

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
