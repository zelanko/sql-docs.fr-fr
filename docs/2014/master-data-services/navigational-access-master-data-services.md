---
title: Accès de navigation (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3d775a3668d76c29cd6f2c10a3eeb53e46be39d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040176"
---
# <a name="navigational-access-master-data-services"></a>Accès de navigation (Master Data Services)
  L’accès de navigation s’applique à la sécurité de l’objet modèle, affectée sous l’onglet **Modèles**.  
  
 L'accès de navigation désigne l'accès aux niveaux supérieurs par rapport à ceux auxquels vous avez affecté une sécurité.  
  
 Dans cet exemple, les autorisations sont affectées à une entité, et donc l'accès de navigation est accordé au niveau du modèle.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entités**  
  
 Lorsque vous affectez une autorisation à une entité, ses membres feuilles ou ses membres consolidés, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres. Vous pouvez également lire le nom du modèle.  
  
 **Attributs**  
  
 Lorsque vous affectez une autorisation à un attribut, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres dans l'entité. Vous pouvez également lire le nom du modèle.  
  
 **Collections**  
  
 Lorsque vous affectez des autorisations aux collections, vous pouvez lire ou mettre à jour le nom, le code, la description et l'ID de propriétaire. Vous pouvez également lire le nom du modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les autorisations sont déterminées &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  