---
title: Fonctionnement des curseurs et des verrous | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO]
- cursors [ADO]
ms.assetid: c1b7d7e6-1707-4ce2-863f-0c6dea967df6
author: rothja
ms.author: jroth
ms.openlocfilehash: 13a175d9e98fec5795c2756e79f96304b2ab2cc6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759015"
---
# <a name="understanding-cursors-and-locks"></a>Présentation des curseurs et des verrous
Il est important de comprendre comment les curseurs fonctionnent pour vous permettre de sélectionner le type de curseur le plus efficace et le plus efficace pour les besoins d’accès aux données d’une application. Une configuration de curseur peu optimale peut rendre les opérations d’accès aux données très lentes.  
  
 De nombreuses fonctionnalités de l’objet **Recordset** ADO sont déterminées par le type et l’emplacement du curseur, ainsi que par le type de verrou.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Qu’est qu’un curseur ?](../../../ado/guide/data/what-is-a-cursor.md)  
  
-   [Types de curseurs](../../../ado/guide/data/types-of-cursors-ado.md)  
  
-   [Signification de l’emplacement du curseur](../../../ado/guide/data/the-significance-of-cursor-location.md)  
  
-   [Service de curseur Microsoft pour OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md)  
  
-   [Qu’est qu’un verrou ?](../../../ado/guide/data/what-is-a-lock.md)  
  
-   [Utilisation de CacheSize](../../../ado/guide/data/using-cachesize.md)  
  
-   [Caractéristiques des curseurs et des verrous](../../../ado/guide/data/cursor-and-lock-characteristics.md)
