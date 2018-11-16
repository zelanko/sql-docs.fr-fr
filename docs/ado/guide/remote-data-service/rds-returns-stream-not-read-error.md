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
manager: craigg
ms.openlocfilehash: 65067452553f3a0c44259e12b294bc795baa9d12
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559956"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS retourne &quot;Stream non lu&quot; erreur
« L’objet Stream est illisible, car elle est vide, ou la position actuelle est à la fin de la Stream. Pour les flux non vide, définissez la position actuelle avec la propriété Position. Pour déterminer si un Stream est vide, vérifiez la propriété de taille. »  
  
 Si vous voyez ce message d’erreur, vous pouvez essayé d’utiliser une requête paramétrable hiérarchique sur http. Services Bureau à distance ne vous permet pas d’utiliser des hiérarchies paramétrables à distance.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


