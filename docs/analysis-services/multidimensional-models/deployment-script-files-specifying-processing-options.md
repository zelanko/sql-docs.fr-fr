---
title: "Spécification des Options de traitement | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a3b80d70cce0e2efeae9c9a239d9e6fc4b8ffcd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-script-files---specifying-processing-options"></a>Fichiers de Script de déploiement - spécification des Options de traitement
  Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de traitement de la \< *nom du projet*> .deploymentoptions fichier. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]utilise les options de traitement spécifiées sur la **déploiement** page de  *\<nom du projet >* **Pages de propriétés** boîte de dialogue pour créer le \< *nom du projet*> .deploymentoptions fichier.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Examen des options de traitement pour le déploiement  
 Les paramètres de configuration stockés dans le \< *nom du projet*> .deploymentoptions sont les suivantes :  
  
-   **Méthode de traitement** Ce paramètre contrôle si les objets déployés sont traités après le déploiement et le type de traitement à effectuer. Trois options de traitement sont possibles :  
  
    -   Traitement par défaut (option par défaut)  
  
    -   Traitement complet  
  
    -   Aucun  
  
-   **Options de table d'écriture différée** Si l'écriture différée est activée dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ce paramètre définit les modalités de l'écriture différée. Trois options de table d'écriture différée sont possibles :  
  
    -   Par défaut, s'il existe une table d'écriture différée, elle est utilisée. S'il n'existe pas de table d'écriture différée, une nouvelle table d'écriture différée est créée.  
  
    -   S'il existe déjà une table d'écriture différée, le déploiement échoue. S'il n'existe pas de table d'écriture différée, une nouvelle table d'écriture différée est créée.  
  
    -   Une nouvelle table d'écriture différée est créée dans tous les cas, même s'il en existe déjà une. Avec cette option, l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toute table existante et la remplace par une nouvelle table d'écriture différée.  
  
-   **Déploiement transactionnel** Ce paramètre contrôle si le déploiement de modifications de métadonnées et de commandes de processus s'effectue en une seule transaction ou en transactions distinctes.  
  
    -   Si cette option a la valeur **True** (valeur par défaut), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie toutes les modifications de métadonnées et toutes les commandes de processus en une seule transaction.  
  
    -   Si cette option a la valeur **False**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie les modifications de métadonnées en une seule transaction et déploie chaque commande de processus dans sa propre transaction.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Modification des options de traitement pour le déploiement  
 Toutefois, vous devez déployer le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de projet à l’aide des options de traitement différentes de celles stockées dans le \< *nom du projet*> .deploymentoptions fichier. Par exemple, vous pouvez souhaiter que tous les objets soient traités entièrement ou traités en utilisant l'option de traitement par défaut, ou encore qu'aucun traitement n'ait lieu. Si les cubes ou les dimensions sont activés en écriture, vous pouvez spécifier si une nouvelle table d'écriture différée ou une table existante doit être utilisée.  
  
 Pour modifier les options de traitement utilisées durant le déploiement, vous pouvez soit modifier et régénérer le projet, soit modifier les options de traitement dans le fichier d'entrée en utilisant l'une des méthodes décrites dans la procédure suivante.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Pour modifier des options de traitement après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif. Sur la page **Options de traitement** , spécifiez les options de traitement du projet à déployer.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —ou—  
  
-   Modifier la \< *nom du projet*> fichier .deploymentoptions à l’aide de n’importe quel éditeur de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de la cible d'installation](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Spécification des options de déploiement de partitions et de rôles](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  

