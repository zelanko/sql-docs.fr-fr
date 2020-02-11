---
title: Générer des projets de Analysis Services (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], building
- Business Intelligence Development Studio, project building [Analysis Services]
ms.assetid: caac03cb-b2b4-4652-8913-3dd39c4b0127
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97e32b80d19675b3763101d1c226529a48e23e68
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076774"
---
# <a name="build-analysis-services-projects-ssdt"></a>Générer des projets Analysis Services (SSDT)
  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], la procédure de génération d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est semblable à celle que vous suivez pour générer un projet de programmation dans Visual Studio. Lorsque vous générez le projet, un ensemble de fichiers XML est créé dans le répertoire de sortie. Ces fichiers XML utilisent le langage ASSL (Analysis Services Scripting Language), qui correspond au dialecte XML utilisé par les applications clientes telles que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour communiquer avec une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] afin de créer ou de modifier des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Ils permettent de déployer des définitions d’objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans une instance spécifique d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="building-a-project"></a>Génération d'un projet  
 Si vous générez un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] génère un ensemble complet de fichiers XML dans le dossier de sortie contenant toutes les commandes ASSL nécessaires pour générer tous les objets de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans le projet. Si le projet a été généré précédemment et qu'un déploiement incrémentiel est spécifié pour la configuration active, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] créera également un fichier XML contenant les commandes ASSL pour effectuer une mise à jour incrémentielle des objets déployés. Ce fichier XML est écrit dans le dossier \obj\\<configuration_active\> du projet. Les générations incrémentielles permettent de gagner du temps lors du déploiement et du traitement d'une base de données ou d'un projet très volumineux.  
  
> [!NOTE]  
>  Vous pouvez utiliser la commande Régénérer tout pour ignorer la configuration de déploiement incrémentiel.  
  
 La génération d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide les définitions des objets dans le projet. La validation intègre les assemblys référencés. Les erreurs de build s'affichent dans la fenêtre Liste des tâches, ainsi que l'erreur AMO (Analysis Management Objects). Vous pouvez cliquer sur une erreur afin d'ouvrir le Concepteur nécessaire pour la corriger.  
  
 Une validation réussie ne garantit pas que les objets peuvent être créés sur le serveur de destination lors du déploiement ou traités une fois le déploiement terminé. Les problèmes ci-après peuvent empêcher le déploiement ou le traitement une fois le déploiement terminé :  
  
-   Des verrous empêchent le déploiement si les contrôles de sécurité du serveur ne sont pas effectués.  
  
-   Emplacements physiques non validés sur le serveur.  
  
-   Détails des vues de source de données non vérifiés dans la source de données actuelle sur le serveur de destination.  
  
 Une fois la validation terminée, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] génère les fichiers XML. Après la génération, le dossier de sortie contient les fichiers décrits dans le tableau suivant.  
  
|Fichiers (dans le dossier bin)|Description|  
|-----------------------------|-----------------|  
|*NomProjet*. asdatabase|Contient les éléments ASSL qui définissent les métadonnées des objets du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans un fichier de script de déploiement. Ce fichier est utilisé par le moteur de déploiement pour déployer les objets dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|*NomProjet*. configsettings|Contient les paramètres de configuration utilisés pendant le déploiement que vous pouvez modifier directement ou dans l’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (par exemple, la chaîne de connexion pour les sources de données).|  
|*NomProjet*. deploymenttargets|Contient les paramètres de destination utilisés lors du déploiement que vous pouvez modifier directement ou dans l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (par exemple, les noms de serveur et de base de données).|  
|*NomProjet*. deploymentoptions|Contient plusieurs paramètres utilisés pendant le déploiement que vous pouvez modifier directement ou dans l’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (par exemple, les emplacements de stockage).|  
|*AssemblyName*/*DllName.* dll|Les dossiers sont distincts pour chaque assembly référencé ; chaque dossier contient la DLL de l'assembly, l'assembly référencé et les fichiers .pdb associés pour les informations de débogage de la sortie.|  
  
|Fichiers (dans le dossier obj)|Description|  
|-----------------------------|-----------------|  
|\<Nom de configuration> \LastBuilt.xml|Contient le cachet temporel et le code de hachage qui identifient la dernière fois où le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a été généré.|  
  
 Ces fichiers XML ne contiennent \<pas les balises \<Create> et ALTER>, qui sont construites au cours du déploiement.  
  
 Les assemblys référencés (à l'exception des assembly système standard et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) sont également copiés dans le répertoire de sortie. S'il existe des références à d'autres projets d'une solution, ces projets sont créés en premier lieu, à l'aide des dépendances de génération et de configuration du projet approprié établies par les références au projet, puis copiées dans le dossier de sortie du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services&#41; référence du langage de script &#40;ASSL](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Déployer des projets Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  
