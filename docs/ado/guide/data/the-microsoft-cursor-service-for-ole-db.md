---
title: Le Service de curseur Microsoft pour OLE DB | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e85d6f482b9d206b2ec705a8d890a4e34e5f2252
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142928"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Service de curseur Microsoft pour OLE DB
Lorsque vous sélectionnez un curseur côté client ou le **CursorLocation** propriété **adUseClient**, vous appelez le Service de curseur Microsoft pour OLE DB. Vous pouvez également voir des références à « Moteur du curseur Client », qui est essentiellement la même chose dans le contexte d’ADO. Ce service complète les fonctions de curseur-prise en charge des fournisseurs de données. Par conséquent, vous pouvez percevoir relativement uniforme des fonctionnalités à partir de tous les fournisseurs de données.  
  
 Le Service de curseur pour OLE DB rend disponibles les propriétés dynamiques et améliore le comportement de certaines méthodes. Par exemple, le **optimiser** propriété dynamique permet la création d’index temporaires afin de faciliter certaines opérations, telles que la **trouver** (méthode).  
  
 Le Service de curseur permet la prise en charge de la mise à jour du lot dans tous les cas. Elle simule également des types de curseurs plus performante, tels que les curseurs dynamiques, lorsqu’un fournisseur de données peut fournir uniquement les curseurs moins performant, tels que les curseurs statiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Service de curseur Microsoft pour OLE DB (composant du Service ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
