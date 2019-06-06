---
title: Persistance des Recordsets filtrés et hiérarchiques | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cbd237580dc8c56284552e6fe2fb00e469832c5b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702045"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Persistance des recordsets filtrés et hiérarchiques
Si le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété est en vigueur pour le **Recordset**, seules les lignes accessibles sous le filtre sont enregistrés. Si le **Recordset** est hiérarchique, l’enfant actuel **Recordset** et ses enfants sont enregistrés, y compris le parent **Recordset**. Si le **enregistrer** méthode d’un enfant **Recordset** est appelée, l’enfant et tous ses enfants sont enregistrés, mais le parent n’est pas. Pour plus d’informations sur hiérarchique **Recordsets**, consultez [mise en forme des données](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Certaines limitations s’appliquent lors de l’enregistrement hiérarchique **Recordsets** (formes de données) au format XML. Pour plus d’informations, consultez [persistance des enregistrements au Format XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
