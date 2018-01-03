---
title: "Jeux d’enregistrements hiérarchiques et filtrés persistants | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45f6f546531e506e841088bd0b73daab3e0e5360
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistance des jeux d’enregistrements hiérarchiques et filtrés
Si le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété n’est en vigueur pour le **Recordset**, seules les lignes accessibles sous le filtre sont enregistrées. Si le **Recordset** est hiérarchique, l’enfant **Recordset** et ses enfants sont enregistrés, y compris le parent **Recordset**. Si le **enregistrer** méthode d’un enfant **Recordset** est appelée, l’enfant et tous ses enfants sont enregistrés, mais le parent n’est pas. Pour plus d’informations sur hiérarchique **jeux d’enregistrements**, consultez [mise en forme des données](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Certaines restrictions s’appliquent lors de l’enregistrement hiérarchique **jeux d’enregistrements** (formes de données) au format XML. Pour plus d’informations, consultez [persistance des enregistrements au Format XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
