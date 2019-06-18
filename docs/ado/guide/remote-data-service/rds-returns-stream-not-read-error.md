---
title: RDS retourne &quot;Stream non lu&quot; erreur | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 598326335c32f18b5d7f5a764d387e5b5ea536f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699425"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS retourne &quot;Stream non lu&quot; erreur
« L’objet Stream est illisible, car elle est vide, ou la position actuelle est à la fin de la Stream. Pour les flux non vide, définissez la position actuelle avec la propriété Position. Pour déterminer si un Stream est vide, vérifiez la propriété de taille. »  
  
 Si vous voyez ce message d’erreur, vous pouvez essayé d’utiliser une requête paramétrable hiérarchique sur http. Services Bureau à distance ne vous permet pas d’utiliser des hiérarchies paramétrables à distance.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


