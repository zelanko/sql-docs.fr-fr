---
title: Exécution de l’Assistant Déploiement de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8fd34a7e614c1c1bb247f84846e090d22ea053e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073039"
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Exécution de l'Assistant Déploiement d'Analysis Services
  Lorsque vous utilisez l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant déploiement pour déployer un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, vous pouvez exécuter l’Assistant des manières suivantes :  
  
-   De **manière interactive** Lorsqu’il est exécuté de manière interactive [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , l’Assistant Déploiement génère un script de déploiement XML basé sur les fichiers d’entrée, tel qu’il a été modifié de manière interactive par l’entrée utilisateur. L'Assistant applique les modifications utilisateur uniquement au script de déploiement. Il ne modifie pas les fichiers d'entrée. Pour plus d’informations sur les fichiers d’entrée, voir [Précisions sur les fichiers d’entrée utilisés pour créer le script de déploiement](deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **À partir de l’invite de commandes** Lorsqu’il est exécuté à partir de l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] invite de commandes, l’Assistant Déploiement génère un script de déploiement XML for Analysis (XMLA) basé sur les commutateurs que vous utilisez pour exécuter l’Assistant. L'Assistant peut effectuer les opérations suivantes : vous demander une entrée utilisateur et modifier les fichiers d'entrée en fonction de cette entrée, exécuter un déploiement automatisé en mode silencieux en utilisant les fichiers d'entrée tels quels, ou créer un script de déploiement que vous pouvez utiliser ultérieurement.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Exécution de l'Assistant Déploiement d'Analysis Services de manière interactive  
 Lorsque vous exécutez l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de manière interactive, il lit les valeurs des fichiers d'entrée et affiche ces informations. Vous pouvez modifier ces valeurs d’entrée, telles que la destination de déploiement, les paramètres de configuration, les options de déploiement et les mots de passe de chaîne de connexion, ou les conserver en l’emplacement. Si vous changez les valeurs d'entrée, l'Assistant utilise ces modifications lors de la génération du script de déploiement XMLA. Toutefois, il ne modifie pas les valeurs du fichier d'entrée.  
  
> [!NOTE]  
>  Pour que l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifie les valeurs d'entrée, exécutez-le à partir de l'invite de commandes et configurez-le pour fonctionner en mode de fichier de réponses.  
  
 Après avoir vérifié les valeurs d'entrée et effectué les modifications appropriées, l'Assistant génère le script de déploiement XMLA. Vous pouvez exécuter ce script de déploiement immédiatement sur le serveur de destination ou l'enregistrer en vue d'une utilisation ultérieure.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>Pour exécuter l'Assistant Déploiement d'Analysis Services de manière interactive  
  
-   Dans le menu **Démarrer**, pointez successivement sur **Tous les programmes**, **Microsoft SQL Server**et **Analysis Services**, puis cliquez sur **Assistant Déploiement**.  
  
     -ou-  
  
-   Dans le dossier **projets** du [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, double-cliquez sur le * \<nom du projet>* fichier. asdatabase.  
  
    > [!NOTE]  
    >  Si vous ne trouvez pas le * \<nom du projet>* fichier. asdatabase, essayez d’utiliser la recherche et spécifiez *. asdatabase.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Exécution de l'Assistant Déploiement d'Analysis Services à partir de l'invite de commandes  
 Vous pouvez également exécuter l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de l'invite de commandes. Lorsque vous exécutez l'Assistant à l'invite de commandes, vous fournissez le chemin d'accès complet au fichier .asdatabase et exécutez l'Assistant en l'un des modes suivants :  
  
 **Mode de fichier de réponses**  
 Dans ce mode, l’Assistant permet de modifier de manière interactive les fichiers d’entrée générés à l’origine lors de la création du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. L'Assistant enregistre les fichiers d'entrée modifiés avant de générer le script de déploiement XMLA. Les fichiers d'entrée deviennent le nouveau point de départ de la prochaine exécution de l'Assistant.  
  
 Pour exécuter l’Assistant en mode fichier de réponses, utilisez le commutateur **/a** .  
  
 **Mode silencieux**  
 En mode silencieux, l'Assistant exécute un déploiement automatisé en fonction des informations qui se trouvent dans les fichiers d'entrée.  
  
 Pour exécuter l’Assistant en mode silencieux, utilisez le commutateur **/s** . Lorsque vous exécutez l'Assistant en mode silencieux, les messages sont affichés sur la console ou enregistrés dans un fichier journal (s'il en existe un).  
  
 **Mode de sortie**  
 En mode de sortie, l'Assistant génère un script de déploiement XMLA pour l'exécuter plus tard en fonction des fichiers d'entrée.  
  
 Pour exécuter l’Assistant en mode de sortie, utilisez le commutateur **/o** et fournissez un nom de fichier de sortie.  
  
 Pour plus d’informations sur les commutateurs de ligne de commande, voir [Déployer des solutions de modèle avec l’utilitaire de déploiement](deploy-model-solutions-with-the-deployment-utility.md).  
  
 La procédure suivante explique comment exécuter l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de l'invite de commandes.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Pour exécuter l'Assistant Déploiement d'Analysis Services à partir de l'invite de commandes  
  
1.  Ouvrez une invite de commandes et accédez au dossier C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.  
  
2.  Tapez **Microsoft.AnalysisServices.Deployment.exe** , suivi des commutateurs qui correspondent au mode dans lequel vous souhaitez exécuter l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Compréhension du script de déploiement Analysis Services](understanding-the-analysis-services-deployment-script.md)   
 [Deploy Model Solutions Using the Deployment Wizard](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
