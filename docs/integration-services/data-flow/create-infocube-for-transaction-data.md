---
description: Créer un InfoCube pour les données de transaction
title: Créer un InfoCube pour les données de transaction | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18d7f3f10a2d7179d31e08e5a8e255df7295ca67
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457391"
---
# <a name="create-infocube-for-transaction-data"></a>Créer un InfoCube pour les données de transaction

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Utilisez la boîte de dialogue **Créer un InfoCube pour les données de transaction** pour créer un InfoCube pour les données de transaction dans le système SAP Netweaver BW.  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoCube pour les données de transaction** depuis la page **Gestionnaire de connexions** de **l’Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [Destination SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Créer un InfoCube pour les données de transaction**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **Créer des objets SAP BW** , sélectionnez **InfoCube**, puis cliquez sur **Créer**.  
  
## <a name="general-options"></a>Options générales  
 **Nom de l'InfoCube**  
 Entrez le nom du nouvel InfoCube.  
  
 **Description longue**  
 Entrez une description pour le nouvel InfoCube.  
  
 **Enregistrer et activer**  
 Enregistrez et activez le nouvel InfoCube.  
  
## <a name="infocube-transfer-structure-options"></a>Options de structure de transfert de l'InfoCube  
 La section de structure de transfert de l'InfoCube vous permet d'associer les colonnes de flux de données à des InfoObjects.  
  
 **PipelineElement**  
 Affiche la colonne dans la sortie du flux de données qui est connectée à la destination SAP BW.  
  
 **PipelineDataType**  
 Affiche le type de données de la colonne de flux de données.  
  
 **InfoObject**  
 Affiche le nom de l'InfoObject qui est associé à la colonne de flux de données.  
  
 **Type**  
 Affiche le type de l'InfoObject qui est associé à la colonne de flux de données. Le tableau suivant répertorie les valeurs possibles pour le type.  
  
|Value|Description|  
|-----------|-----------------|  
|CHA|Caractéristiques|  
|UNI|Unités|  
|KYF|Chiffres clés|  
|TIM|Caractéristiques de temps|  
  
 **Iobject - Rechercher**  
 Associez un InfoObject existant à la colonne de flux de données de la ligne actuelle. Pour effectuer cette association, cliquez sur **Rechercher**, puis utilisez la boîte de dialogue **Rechercher un InfoObject** pour sélectionner l’InfoObject existant. Pour plus d’informations sur cette boîte de dialogue, consultez [Rechercher un InfoObject](../../integration-services/data-flow/look-up-infoobject.md).  
  
 Après avoir sélectionné un InfoObject existant, le composant remplit les colonnes **InfoObject** et **Type** avec les valeurs sélectionnées.  
  
 **Iobject - Nouveau**  
 Créez un nouvel InfoObject et associez ce nouvel InfoObject à la colonne de flux de données de la ligne actuelle. Pour créer l’InfoObject, cliquez sur **Nouveau**, puis utilisez la boîte de dialogue **Créer un nouvel InfoObject** pour créer l’InfoObject. Pour plus d'informations sur cette boîte de dialogue, consultez [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).  
  
 Après avoir créé un InfoObject, le composant remplit les colonnes **InfoObject** et **Type** avec les nouvelles valeurs.  
  
 **Iobject - Supprimer**  
 Supprimez l'association entre l'InfoObject et la colonne de flux de données de la ligne actuelle. Pour supprimer cette association, cliquez sur **Supprimer**.  
  
## <a name="see-also"></a> Voir aussi  
 [Aide (F1) sur Microsoft Connector pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
