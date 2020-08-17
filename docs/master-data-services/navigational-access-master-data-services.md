---
description: Accès de navigation (Master Data Services)
title: Accès de navigation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bd1879ee534a3f17de39b1b632a0fcaeb835abbf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88343115"
---
# <a name="navigational-access-master-data-services"></a>Accès de navigation (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  L’accès de navigation s’applique à la sécurité de l’objet modèle, affectée sous l’onglet **Modèles** .  
  
 L’accès de navigation désigne l’accès aux niveaux supérieurs par rapport à ceux auxquels vous avez affecté une sécurité.  
  
 Dans cet exemple, les autorisations sont affectées à une entité, et donc l'accès de navigation est accordé au niveau du modèle.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entités**  
  
 Lorsque vous affectez une autorisation à une entité, ses membres feuilles ou ses membres consolidés, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres. Vous pouvez également lire le nom du modèle.  
  
 **Attributs**  
  
 Lorsque vous affectez une autorisation à un attribut, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres dans l'entité. Vous pouvez également lire le nom du modèle.  
  
 **Regroupements**  
  
 Lorsque vous affectez des autorisations aux collections, vous pouvez lire ou mettre à jour le nom, le code, la description et l'ID de propriétaire. Vous pouvez également lire le nom du modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
