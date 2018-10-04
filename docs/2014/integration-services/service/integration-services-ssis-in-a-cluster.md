---
title: Integration Services (SSIS) dans un cluster | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 0216266d-d866-4ea2-bbeb-955965f4d7c2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0846c7bdb0728d79dc3538eb5a46797e1b77e3db
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095979"
---
# <a name="integration-services-ssis-in-a-cluster"></a>Integration Services (SSIS) dans un cluster
  Le clustering [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas recommandé, car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas un service cluster ou prenant en charge les clusters. De plus, il ne prend pas en charge le basculement d’un nœud de cluster à un autre. Par conséquent, dans un environnement cluster, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] doit être installé et démarré en tant que service autonome sur chaque nœud du cluster.  
  
 Même si le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas un service cluster, vous pouvez le configurer manuellement pour qu’il fonctionne en tant que ressource de cluster après avoir installé séparément [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur chaque nœud du cluster.  
  
 Toutefois, si en mettant en place un environnement matériel cluster, votre objectif est de bénéficier d'une haute disponibilité, vous pouvez y parvenir sans configurer le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en tant que ressource de cluster.  Pour gérer vos packages sur n’importe quel nœud du cluster à partir de n’importe quel nœud du cluster, modifiez le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur chaque nœud du cluster. Vous modifiez chacun des fichiers de configuration pour pointer vers toutes les instances disponibles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur lesquelles les packages sont stockés. Cette solution apporte la haute disponibilité dont la plupart des clients ont besoin, sans les problèmes potentiels rencontrés lorsque le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré en tant que ressource de cluster. Pour plus d’informations sur la modification du fichier de configuration, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md).  
  
 Il est essentiel de comprendre le rôle du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour prendre une décision informée sur la configuration du service dans un environnement cluster. Pour plus d’informations, consultez [Service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md).  
  
## <a name="understanding-the-disadvantages-of-configuring-integration-services-as-a-cluster-resource"></a>Inconvénients de la configuration d'Integration Services en tant que ressource de cluster  
 La configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en tant que ressource de cluster présente certains inconvénients potentiels, indiqués ci-dessous :  
  
-   Lorsqu'un basculement a lieu, l'exécution des packages ne redémarre pas. Vous pouvez récupérer des échecs de package en redémarrant les packages à partir des points de contrôle. Vous pouvez effectuer le redémarrage à partir des points de contrôle sans configurer le service en tant que ressource de cluster. Pour plus d'informations, consultez [Redémarrer des packages à l'aide de points de contrôle](../packages/restart-packages-by-using-checkpoints.md).  
  
-   Lorsque vous configurez le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans un groupe de ressources différent de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous ne pouvez pas utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] à partir d’ordinateurs clients pour gérer les packages stockés dans la base de données msdb. Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne peut pas déléguer d’informations d’identification dans ce scénario à deux tronçons.  
  
-   Lorsque plusieurs groupes de ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] incluent le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans un cluster, un basculement peut avoir des résultats inattendus. Examinez le scénario suivant. Groupe1, qui inclut le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , s’exécute sur le Nœud A. Groupe2, qui inclut également le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , s’exécute sur le Nœud B. Groupe2 bascule sur le Nœud A. La tentative de démarrage d’une autre instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le Nœud A échoue, car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un service à instance unique. Le fait que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] essayant de basculer sur le Nœud A échoue également ou non dépend de la configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans Groupe2. Si le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a été configuré pour affecter les autres services dans le groupe de ressources, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui procède au basculement échouera car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a échoué. Si le service a été configuré pour ne pas affecter les autres services dans le groupe de ressources, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pourra basculer sur le Nœud A. À moins que le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans Groupe2 n’ait été configuré pour ne pas affecter les autres services dans le groupe de ressources, l’échec du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui procède au basculement peut aussi provoquer l’échec du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui procède au basculement.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour obtenir des instructions détaillées sur la configuration du service Integration Services dans un cluster, consultez [Configurer le service Integration Services en tant que ressource de cluster](../configure-the-integration-services-service-as-a-cluster-resource.md).  
  
  
