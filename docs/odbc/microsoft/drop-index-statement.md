---
title: L’instruction DROP INDEX | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aef4e44ff71a000345dff42a01d5e5e75a13bdd1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="drop-index-statement"></a>Instruction DROP INDEX
Lorsque le pilote Microsoft Access, dBASE ou Paradox est utilisé, la syntaxe de l’instruction DROP INDEX est « DROP INDEX a à b » où « a » est, le nom de l’index et « b » est le nom de la table (pas les INDEX DROP *-nom de l’index*).  
  
 Lorsque le pilote Paradox est utilisé, l’instruction DROP INDEX supprime les fichiers d’index secondaire de Corel.  
  
 L’instruction DROP INDEX n’est pas prise en charge pour les pilotes Microsoft Excel ou texte.
