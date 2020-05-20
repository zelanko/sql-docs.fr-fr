---
title: Persistance des recordsets filtrés et hiérarchiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fa3fdd55fb78f16629907c174b08aab64ceb86e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763110"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistance des recordsets filtrés et hiérarchiques
Si la propriété [Filter](../../../ado/reference/ado-api/filter-property.md) est appliquée au **jeu d’enregistrements**, seules les lignes accessibles sous le filtre sont enregistrées. Si le **jeu d’enregistrements** est hiérarchique, le **jeu d’enregistrements** enfant actuel et ses enfants sont enregistrés, y compris le **Recordset**parent. Si la méthode **Save** d’un **jeu d’enregistrements** enfant est appelée, l’enfant et tous ses enfants sont enregistrés, mais le parent n’est pas. Pour plus d’informations sur les **jeux d’enregistrements**hiérarchiques, consultez mise en [forme des données](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Certaines restrictions s’appliquent lors de l’enregistrement de **recordsets** hiérarchiques (formes de données) au format XML. Pour plus d’informations, consultez [persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
