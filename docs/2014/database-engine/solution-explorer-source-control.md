---
title: Contrôle de code source Explorateur de solutions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 788ce615f914dcc8a2a49fba7575061fff0df870
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62843104"
---
# <a name="solution-explorer-source-control"></a>Contrôle de code source de l'Explorateur de solutions
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Explorateur de solutions peut être intégré à un système de contrôle de code source distinct. Après intégration d'une solution ou d'un projet à un système de contrôle de code source, vous pouvez contrôler l'accès aux fichiers et les versions pour les scripts et les requêtes de vos projets.  
  
## <a name="solution-and-project-source-control"></a>Contrôle de code source de solution et de projet  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 Le contrôle de code source fait référence à un système dans lequel un logiciel serveur central stocke et effectue le suivi des versions de fichiers et contrôle l'accès aux fichiers. Un système de contrôle de code source comprend généralement un fournisseur de contrôle de code source et deux (voire plus) clients de contrôle de code source. 
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut être intégré à un service de contrôle de code source. Cela signifie que vous pouvez utiliser cet outil comme client pour votre fournisseur de contrôle de code source. Sans quitter votre environnement, vous êtes ainsi en mesure de gérer en toute facilité vos projets individuels et collaboratifs. Le fournisseur de contrôle du code source n'est pas inclus dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
#### <a name="to-select-a-source-control-provider"></a>Pour sélectionner un fournisseur de contrôle du code source  
  
1.  Installez la partie cliente de votre fournisseur de contrôle du code source.  
  
2.  Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], dans le menu **Outils** , cliquez sur **Options**.  
  
3.  Dans la boîte de dialogue **options** , développez **contrôle de code source**, puis cliquez sur la page **sélection du plug-** in.  
  
4.  Dans la zone plug-in de **contrôle de code source actuel** , sélectionnez le plug-in de contrôle de code source.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Présentation du contrôle de code source](../../2014/database-engine/source-control-basics.md)|Indique la terminologie de base du contrôle de code source et détermine les avantages présentés par les services de contrôle de code source dans le cadre d'un projet.|  
|[Ajouter des solutions et des projets au contrôle de code source](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|Explique comment utiliser l'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour ajouter des solutions et des projets au contrôle de code source.|  
|[Ouvrir des solutions et des projets à partir du contrôle de code source](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|Explique comment utiliser l'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour ouvrir des solutions et des projets sous contrôle de code source.|  
|[Gérer les extractions](../../2014/database-engine/manage-checkouts.md)|Indique le mode d'extraction de solutions et de fichiers du contrôle de code source.|  
|[Gérer les archivages](../../2014/database-engine/manage-checkins.md)|Indique le mode d'archivage de solutions et de fichiers dans le contrôle de code source.|  
|[Définir et récupérer des informations sur la version](../../2014/database-engine/set-and-retrieve-version-information.md)|Indique le mode de récupération de l'historique d'un projet ou d'un élément, le mode de récupération d'une copie locale d'un élément et le mode de comparaison de deux versions d'un élément.|  
|||  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de solutions](../ssms/solution/solution-explorer.md)   
 [Solutions &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)   
 [Projets &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md)   
 [Fichiers gérant les solutions et les projets](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
