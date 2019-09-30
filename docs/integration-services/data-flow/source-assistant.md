---
title: Assistant Source | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sourceassistant.f1
- sql13.dts.designer.addNewSource.f1
ms.assetid: 5ca9d821-7d61-4727-9133-5f9cb485c7f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0312349652ad1854efdeacdbfc25726e1766862f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298037"
---
# <a name="source-assistant"></a>Assistant source

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant Assistant Source permet de créer un composant source et un gestionnaire de connexions. Le composant se trouve dans la section **Favoris** de la boîte à outils SSIS.  
  
> [!NOTE]  
>  L'Assistant Source remplace le projet de connexions Integration Services et l'Assistant correspondant.  
  
## <a name="add-a-source-with-source-assistant"></a>Ajouter une source à l’aide de l’Assistant Source
Cette section présente les étapes à suivre pour ajouter une nouvelle source à l’aide de l’Assistant Source. En outre, elle répertorie les options disponibles dans la boîte de dialogue **Ajouter une nouvelle source**, qui s’affiche quand vous effectuez un glisser-déplacer de l’Assistant Source vers le concepteur SSIS.  

1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auquel vous voulez ajouter un composant source.  
  
2.  Faites glisser le composant **Assistant Source** de la boîte à outils SSIS vers l'onglet **Flux de données** . Vous devez voir s'afficher la boîte de dialogue **Ajouter une nouvelle source** . La section suivante fournit des détails sur les options disponibles dans la boîte de dialogue.  
  
3.  Sélectionnez le type de la destination dans la liste **Types** .  
  
4.  Sélectionnez un gestionnaire de connexions existant dans la liste **Gestionnaires de connexions** ou sélectionnez **\<Nouveau>** pour en créer un.  
  
5.  Si vous sélectionnez un gestionnaire de connexions existant, cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une nouvelle destination** . Vous devez constater que la destination et les gestionnaires de connexions ont été ajoutés au flux de données.  
  
6.  Si vous cliquez sur **\<Nouveau>** pour créer un gestionnaire de connexions, vous devez voir s’afficher une boîte de dialogue **Gestionnaire de connexions** qui vous permet de spécifier les paramètres de la connexion. Une fois que vous avez fini de créer le gestionnaire de connexions, vous constatez que la destination et le gestionnaire de connexions figurent dans le concepteur SSIS.  

## <a name="add-new-source-dialog-box"></a>Boîte de dialogue Ajouter une nouvelle source
Le tableau suivant répertorie les options disponibles dans la boîte de dialogue **Ajouter une nouvelle source**.  
  
|Option|Description|  
|------------|-----------------|  
|Types|Sélectionnez le type de source auquel vous voulez vous connecter.|  
|Gestionnaires de connexions|Sélectionnez un gestionnaire de connexions existant ou cliquez sur **\<Nouveau>** pour en créer un.|  
|Afficher les éléments installés uniquement|Spécifiez s'il faut afficher uniquement les sources installées.|  
|OK|Cliquez pour enregistrer vos modifications et ouvrir les boîtes de dialogue suivantes permettant de configurer des options supplémentaires.| 
  
