---
title: Copie les descripteurs | Documents Microsoft
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
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b452725d7a8379dcd8f27228261af8b471d96b08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="copying-descriptors"></a>Descripteurs de copie
Le **SQLCopyDesc** est appelée pour copier les champs d’un descripteur à un autre descripteur. Les champs peuvent être copiés qu’à un descripteur de l’application ou un IPD, mais pas à un IRD. Les champs peuvent être copiés à partir de n’importe quel type du descripteur. Seuls les champs qui sont définis pour les descripteurs de la source et cible sont copiés. **SQLCopyDesc** ne copie pas le champ SQL_DESC_ALLOC_TYPE, car le type d’allocation d’un descripteur ne peut pas être modifié. Champs copiés remplacement les champs existants.  
  
 Un ARD sur le handle d’une seule instruction peut servir le descripteur APD sur un autre descripteur d’instruction. Cela permet à une application de copier les lignes entre les tables sans copier les données au niveau de l’application. Pour ce faire, un descripteur de ligne qui décrit une ligne extraite d’une table est réutilisé comme un descripteur de paramètre pour un paramètre dans une instruction INSERT. Le type d’informations SQL_MAX_CONCURRENT_ACTIVITIES doit être supérieur à 1 pour cette opération réussisse.
