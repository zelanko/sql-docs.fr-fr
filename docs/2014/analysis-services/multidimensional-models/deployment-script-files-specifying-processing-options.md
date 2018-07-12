---
title: Spécification des Options de traitement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5f20e9061aae762eda6b773c7bdb345273fd1b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149100"
---
# <a name="specifying-processing-options"></a>Spécification d'options de traitement
  Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de traitement à partir de la \< *nom_projet*> .deploymentoptions fichier. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise les options de traitement spécifiées sur la **déploiement** page de  *\<nom_projet >* **Pages de propriétés** boîte de dialogue pour créer le \< *nom_projet*> .deploymentoptions fichier.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Examen des options de traitement pour le déploiement  
 Les paramètres de configuration stockés dans le \< *nom_projet*> .deploymentoptions fichier sont les suivantes :  
  
-   **Méthode de traitement** Ce paramètre contrôle si les objets déployés sont traités après le déploiement et le type de traitement à effectuer. Trois options de traitement sont possibles :  
  
    -   Traitement par défaut (option par défaut)  
  
    -   Traitement complet  
  
    -   None  
  
-   **Options de table d'écriture différée** Si l'écriture différée est activée dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ce paramètre définit les modalités de l'écriture différée. Trois options de table d'écriture différée sont possibles :  
  
    -   Par défaut, s'il existe une table d'écriture différée, elle est utilisée. S'il n'existe pas de table d'écriture différée, une nouvelle table d'écriture différée est créée.  
  
    -   S'il existe déjà une table d'écriture différée, le déploiement échoue. S'il n'existe pas de table d'écriture différée, une nouvelle table d'écriture différée est créée.  
  
    -   Une nouvelle table d'écriture différée est créée dans tous les cas, même s'il en existe déjà une. Avec cette option, l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toute table existante et la remplace par une nouvelle table d'écriture différée.  
  
-   **Déploiement transactionnel** Ce paramètre contrôle si le déploiement de modifications de métadonnées et de commandes de processus s'effectue en une seule transaction ou en transactions distinctes.  
  
    -   Si cette option est `True` (valeur par défaut), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie toutes les modifications de métadonnées et toutes les commandes de processus dans une transaction unique.  
  
    -   Si cette option est `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie les modifications de métadonnées dans une transaction unique et déploie chaque commande de traitement dans sa propre transaction.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Modification des options de traitement pour le déploiement  
 Toutefois, vous devrez peut-être déployer la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet à l’aide des options de traitement différentes de celles stockées dans le \< *nom_projet*> .deploymentoptions fichier. Par exemple, vous pouvez souhaiter que tous les objets soient traités entièrement ou traités en utilisant l'option de traitement par défaut, ou encore qu'aucun traitement n'ait lieu. Si les cubes ou les dimensions sont activés en écriture, vous pouvez spécifier si une nouvelle table d'écriture différée ou une table existante doit être utilisée.  
  
 Pour modifier les options de traitement utilisées durant le déploiement, vous pouvez soit modifier et régénérer le projet, soit modifier les options de traitement dans le fichier d'entrée en utilisant l'une des méthodes décrites dans la procédure suivante.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Pour modifier des options de traitement après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif. Sur la page **Options de traitement** , spécifiez les options de traitement du projet à déployer.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     —ou—  
  
-   Modifier le \< *nom_projet*> fichier .deploymentoptions à l’aide de n’importe quel éditeur de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant la cible d’Installation](deployment-script-files-specifying-the-installation-target.md)   
 [Spécification des partitions et des Options de déploiement de rôle](deployment-script-files-partition-and-role-deployment-options.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](deployment-script-files-solution-deployment-config-settings.md)  
  
  
