---
title: Assistant Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.destinationassistant.f1
- sql13.DTS.DESIGNER.DESTINATIONASSIST.F1
ms.assetid: 10a40921-a2c2-4ac8-be28-311f8500fbf6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f302227746b0479f096fbfc29e50c328b61f114
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71292913"
---
# <a name="destination-assistant"></a>Assistant de destination

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant Assistant Destination permet de créer un composant de destination et un gestionnaire de connexions. Le composant se trouve dans la section **Favoris** de la boîte à outils SSIS.  
  
> [!NOTE]  
>  L'Assistant Destination remplace le projet de connexions Integration Services et l'Assistant correspondant.  

## <a name="add-a-destination-with-destination-assistant"></a>Ajouter une destination à l’aide de l’Assistant Destination
Cette rubrique indique les étapes à suivre pour ajouter une nouvelle destination via l’Assistant Destination. En outre, elle recense les options disponibles dans la boîte de dialogue **Ajouter une nouvelle destination** , qui s’affiche quand vous effectuez un glisser-déplacer de l’Assistant Destination vers le concepteur SSIS.  

1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auquel vous voulez ajouter un composant destination.  
  
2.  Faites glisser le composant **Assistant Destination** de la boîte à outils SSIS vers l'onglet **Flux de données** . Vous devez voir s'afficher la boîte de dialogue **Ajouter une nouvelle destination** . La section suivante fournit des détails sur les options disponibles dans la boîte de dialogue.  
  
3.  Sélectionnez le type de la destination dans la liste **Types** .  
  
4.  Sélectionnez un gestionnaire de connexions existant dans la liste **Gestionnaires de connexions** ou sélectionnez **\<Nouveau>** pour en créer un.  
  
5.  Si vous sélectionnez un gestionnaire de connexions existant, cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une nouvelle destination** . Vous devez constater que la destination et les gestionnaires de connexions ont été ajoutés au flux de données.  
  
6.  Si vous cliquez sur **\<Nouveau>** pour créer un gestionnaire de connexions, vous devez voir s’afficher une boîte de dialogue **Gestionnaire de connexions** qui vous permet de spécifier les paramètres de la connexion. Une fois que vous avez fini de créer le gestionnaire de connexions, vous constatez que la destination et le gestionnaire de connexions figurent dans le concepteur SSIS. 
  
## <a name="add-new-destination-dialog-box"></a>Boîte de dialogue Ajouter une nouvelle destination
Le tableau suivant répertorie les options disponibles dans la boîte de dialogue **Ajouter une nouvelle destination**.  
  
|Option|Description|  
|------------|-----------------|  
|Types|Sélectionnez le type de destination auquel vous voulez vous connecter.|  
|Gestionnaires de connexions|Sélectionnez un gestionnaire de connexions existant ou cliquez sur **\<Nouveau>** pour en créer un.|  
|Afficher les éléments installés uniquement|Spécifiez s'il faut afficher uniquement les destinations installées.|  
|OK|Cliquez pour enregistrer vos modifications et ouvrir les boîtes de dialogue suivantes permettant de configurer des options supplémentaires.|  
