---
description: Service de curseur Microsoft pour OLE DB
title: Service de curseur Microsoft pour OLE DB | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f3646ec86f76fcba2f6b82759a4784de7d463279
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452741"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Service de curseur Microsoft pour OLE DB
Lorsque vous sélectionnez un curseur côté client ou affectez à la propriété **CursorLocation** la valeur **adUseClient**, vous appelez le service de curseur Microsoft pour OLE DB. Vous pouvez également voir des références au « moteur de curseur client », qui est essentiellement la même chose dans le contexte d’ADO. Ce service complète les fonctions de prise en charge des curseurs des fournisseurs de données. Par conséquent, vous pouvez percevoir des fonctionnalités relativement uniformes de tous les fournisseurs de données.  
  
 Le service de curseur pour OLE DB rend les propriétés dynamiques disponibles et améliore le comportement de certaines méthodes. Par exemple, la propriété dynamique **optimize** permet la création d’index temporaires pour faciliter certaines opérations, telles que la méthode **Find** .  
  
 Le service de curseur permet la prise en charge de la mise à jour par lot dans tous les cas. Il simule également des types de curseurs plus efficaces, tels que des curseurs dynamiques, lorsqu’un fournisseur de données ne peut fournir que des curseurs moins performants, tels que des curseurs statiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Service de curseur Microsoft pour OLE DB (composant du service ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
