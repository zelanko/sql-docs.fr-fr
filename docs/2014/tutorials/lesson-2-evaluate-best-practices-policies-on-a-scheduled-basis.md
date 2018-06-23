---
title: 'Leçon 2 : Évaluer les stratégies des meilleures pratiques de manière planifiée | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd4874e722c12813eb574d94c073cc069f72a4b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140859"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a>Leçon 2 : évaluer les stratégies des meilleures pratiques de façon planifiée
  Vous pouvez configurer des évaluations planifiées des stratégies des meilleures pratiques sur une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour configurer l'exécution des stratégies des meilleures pratiques de façon planifiée, vous devez importer les stratégies dans l'instance cible.  
  
 Pour déployer les stratégies planifiées vers plusieurs serveurs, vous pouvez importer les stratégies vers une instance, configurer les planifications pour chaque stratégie, exporter les stratégies planifiées vers un dossier, puis les déployer vers des instances cibles via des serveurs inscrits.  
  
> [!IMPORTANT]  
>  Les instances cibles doivent exécuter [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ou une version ultérieure. L'automation requiert que les stratégies soient stockées localement sur l'instance, ce qui n'est pas pris en charge par les versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui sont antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
 Dans cette leçon, vous effectuerez les opérations suivantes :  
  
-   Importer les stratégies des meilleures pratiques dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Configurer l'exécution des stratégies selon une planification.  
  
-   Déployer les stratégies des meilleures pratiques planifiées sur plusieurs instances via des serveurs inscrits.  
  
 Cette leçon contient les rubriques suivantes :  
  
-   [Importer les stratégies vers une Instance unique](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [Planifier les stratégies](../../2014/tutorials/schedule-the-policies.md)  
  
-   [Déployer des stratégies planifiées sur plusieurs Instances](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer plusieurs serveurs à l'aide de serveurs de gestion centralisée](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  