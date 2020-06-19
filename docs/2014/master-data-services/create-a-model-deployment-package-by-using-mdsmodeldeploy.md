---
title: Créer un package de déploiement de modèle à l’aide de MDSModelDeploy | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f26ef1429d24b93d3c2aa59d613a6ec37684a89
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971809"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Créer un package de déploiement de modèle à l'aide de MDSModelDeploy
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], utilisez l’outil MDSModelDeploy pour créer un package. Selon les commandes spécifiées, le package peut contenir :  
  
-   Des objets de modèle uniquement.  
  
-   Des objets de modèle et des données.  
  
 Si vous souhaitez déployer un package qui contient uniquement des objets de modèle, vous pouvez utiliser l'Assistant Déploiement de modèle dans l'application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] à la place. Pour plus d’informations, consultez [Créer un package de déploiement de modèle à l’aide de l’Assistant](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
> [!NOTE]  
> Cette version de l’outil MDSModelDeploy ne peut pas utiliser plus de gigaoctets (Go) de mémoire. Lorsque vous créez ou déployez des modèles volumineux à l’aide d' **objets de modèle et** de l’option de données, vous pouvez constater des erreurs de type « mémoire insuffisante » ou « flux trop long ». Pour résoudre ce problème, utilisez la mise en lots de MDS pour déployer les données. ou effectuez une mise à niveau vers MDS 2016 ou une version ultérieure, qui comprend la version mise à jour de l’outil MDSModelDeploy.
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
1.  Les autorisations de base nécessaires pour exécuter l'outil MDSModelDeploy sont les suivantes :  
  
    -   La même autorisation Windows que le gestionnaire de configuration MDS (administrateur Windows)  
  
    -   Autorisation DBA sur la base de données MDS.  
  
2.  Les autorisations nécessaires pour créer le package à l'aide de l'outil MDSModelDeploy sont les suivantes :  
  
    -   Autorisation d'administrateur de modèle MDS sur le modèle de données.  
  
    -   Autorisation de fonction Gestion de l'intégration MDS.  
  
3.  Les autorisations nécessaires pour déployer le package à l'aide de l'outil MDSModelDeploy sont les suivantes :  
  
    -   Autorisation de fonction Explorateur MDS  
  
    -   Autorisation de fonction Gestion de l'intégration MDS  
  
    -   Autorisation de fonction Administration de système MDS.  
  
4.  Les autorisations nécessaires pour répertorier les modèles à l'aide de l'outil MDSModelDeploy sont les suivantes :  
  
    -   Autorisation de fonction Explorateur MDS  
  
    -   Autorisation d'administrateur de modèle MDS sur le modèle de données pour voir le modèle dans la liste.  
  
 Un modèle doit exister pour que vous puissiez créer un package. Pour plus d’informations, consultez [Créer un modèle &#40;Master Data Services&#41;](create-a-model-master-data-services.md).  
  
 Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Pour créer un package de déploiement de modèle à l'aide de MDSModelDeploy  
  
1.  Ouvrez une invite de commandes.  
  
2.  Accédez à l'emplacement de MDSModelDeploy.exe.  
  
    -   Si MDS a été installé à l’emplacement par défaut, le fichier se trouve dans *lecteur*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
    -   Si MDS n'a pas été installé dans l'emplacement par défaut, recherchez MDSModelDeploy.exe sur l'ordinateur local.  
  
3.  facultatif. Consultez les options et l'aide.  
  
    -   Pour afficher toutes les options disponibles, tapez `MDSModelDeploy` et appuyez sur Entrée.  
  
    -   Pour afficher l’aide pour une option, tapez la commande suivante, où *OptionName* est le nom de l’option : `MDSModelDeploy help OptionName`.  
  
4.  facultatif. Si vous possédez plusieurs applications Web, déterminez le nom du service que vous allez déployer en entrant cette commande et en appuyant sur ENTRÉE :  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     Une liste de valeurs est retournée, par exemple `MDS1, Default Web Site, MDS`. La première valeur de cette liste (dans ce cas, `MDS1`) est nécessaire pour déployer le modèle.  
  
5.  Pour créer un package qui contient des objets de modèle et des données, tapez la commande suivante, où *ModelName*, *VersionName*, *ServiceName*et *PackageName* sont respectivement les noms du modèle, la version, le service et le fichier de sortie .pkg :  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     Si vous ne souhaitez pas inclure de données, n’utilisez pas les commutateurs `-version` et `-includedata` .  
  
6.  Appuyez sur Entrée. Quand le package est créé, un message indiquant que l’opération de MDSModelDeploy est terminée s’affiche.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Déployer un package de déploiement de modèle à l'aide de MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Options de déploiement de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)   
 [Déploiement de modèles &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
