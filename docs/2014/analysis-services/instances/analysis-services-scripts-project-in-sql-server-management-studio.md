---
title: Projet de Scripts dans SQL Server Management Studio Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Analysis Services]
- scripts [Analysis Services], projects
- projects [Analysis Services], Analysis Server Scripts project
- projects [Analysis Services], creating
- Analysis Server Scripts project
- items [Analysis Services]
ms.assetid: c4f5a06b-e2e4-4660-a3a8-6fd356742c02
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0bcc06655333dfef073757218d9a740c1dfb0dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66080355"
---
# <a name="analysis-services-scripts-project-in-sql-server-management-studio"></a>Projet de script Analysis Services dans SQL Server Management Studio
  Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez créer un projet Scripts Analysis Server dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour regrouper des scripts liés destinés au développement, à la gestion et au contrôle de code source. Si aucune solution n’est chargée dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], la création d’un nouveau projet Scripts Analysis Server crée automatiquement une solution. Vous pouvez également ajouter le projet Scripts du serveur d'analyse à la solution existante ou le créer dans une nouvelle solution.  
  
 Vous pouvez utiliser les étapes de base suivantes pour créer un projet Scripts du serveur d'analyse dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
1.  Dans le menu Fichier, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
     Sélectionnez le modèle de projet **Scripts Analysis Server** et spécifiez un nom et un emplacement pour le nouveau projet.  
  
2.  Cliquez avec le bouton droit sur **Connexions** pour créer une connexion dans le dossier Connexions du projet Scripts Analysis Server dans l’Explorateur de solutions.  
  
     Ce dossier contient les chaînes de connexion aux instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , sur lesquelles les scripts contenus dans le projet Scripts du serveur d'analyse peuvent être exécutés. Vous pouvez posséder plusieurs connexions dans un projet Scripts du serveur d'analyse et vous pouvez choisir une connexion pour laquelle exécuter un script contenu dans le projet au moment de l'exécution.  
  
3.  Cliquez avec le bouton droit sur **Requêtes** pour créer des scripts MDX (Multidimensional Expressions), DMX (Data Mining Extensions) et XMLA (XML for Analysis) dans le dossier Scripts du projet Scripts Analysis Server, dans l’Explorateur de solutions. Pour plus d’informations, consultez [Tâches d’administration à l’aide de scripts dans Analysis Services](../script-administrative-tasks-in-analysis-services.md).  
  
4.  Cliquez avec le bouton droit sur le projet, pointez sur **Ajouter**, puis sélectionnez **Élément existant** pour ajouter différents fichiers, comme des fichiers texte contenant des notes sur le projet, dans le dossier **Divers** du projet Scripts Analysis Server dans l’Explorateur de solutions. Ces fichiers sont ignorés par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="file-types"></a>Types de fichiers  
 Une solution [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut contenir plusieurs types de fichiers, en fonction des projets que vous avez inclus dans la solution et des éléments que vous avez inclus dans chaque projet pour cette solution. Pour plus d’informations sur les types de fichiers pour les solutions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Fichiers gérant les solutions et les projets](../../ssms/solution/files-that-manage-solutions-and-projects.md). En règle générale, les fichiers de chaque projet dans une solution [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sont stockés dans le dossier de la solution, dans un dossier distinct pour chaque projet.  
  
 Le dossier d'un projet Scripts du serveur d'analyse peut contenir les types de fichiers répertoriés dans le tableau ci-dessous.  
  
|Type de fichier|Description|  
|---------------|-----------------|  
|Fichier de définition de projet Scripts du serveur d'analyse (.ssmsasproj)|Contient des métadonnées sur les dossiers affichés dans l'Explorateur de solutions, ainsi que des informations qui indiquent quels dossiers doivent afficher les fichiers inclus dans le projet.<br /><br /> Le fichier de définition de projet contient également les métadonnées pour les connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenues dans le projet, ainsi que les métadonnées qui associent les connexions aux fichiers de script inclus dans le projet.|  
|Fichier de script DMX (.dmx)|Contient un script DMX inclus dans le projet.|  
|Fichier de script MDX (.mdx)|Contient un script MDX inclus dans le projet.|  
|Fichier de script XMLA (.xmla)|Contient un script XMLA inclus dans le projet.|  
  
## <a name="analysis-services-templates"></a>Modèles Analysis Services  
 Si vous ajoutez des scripts MDX, DMX ou XMLA à un projet Scripts Analysis Server, vous pouvez utiliser l’Explorateur de modèles pour rechercher les modèles [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , qui sont constitués d’un ensemble de scripts ou d’instructions prédéfinis qui montrent comment effectuer une action spécifique. L’Explorateur de modèles est accessible à partir du menu **Affichage** et intègre des modèles pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Pour plus d’informations, consultez [Utiliser des modèles Analysis Services dans SQL Server Management Studio](use-analysis-services-templates-in-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de modèles multidimensionnels à l’aide des Outils de données SQL Server &#40;SSDT&#41;](../multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [Référence MDX &#40;Multidimensional Expressions&#41;](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Référence DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Analysis Services Scripting Language &#40;ASSL&#41; référence](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Analysis Services Scripting Language &#40;ASSL&#41; référence](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)  
  
  
