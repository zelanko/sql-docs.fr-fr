---
title: Créer un InfoCube pour les données de transaction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 167e799c873d586b06300a7e9433324391968d32
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62827926"
---
# <a name="create-infocube-for-transaction-data"></a>Créer un InfoCube pour les données de transaction
  Utilisez la boîte de dialogue **Créer un InfoCube pour les données de transaction** pour créer un InfoCube pour les données de transaction dans le système SAP Netweaver BW.  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoCube pour les données de transaction** depuis la page **Gestionnaire de connexions** de **l’Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [SAP BW Destination](sap-bw-destination.md).  
  
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
 Associez un InfoObject existant à la colonne de flux de données de la ligne actuelle. Pour réaliser cette association, cliquez sur **Rechercher**, puis utilisez la boîte de dialogue **Rechercher un InfoObject** pour sélectionner l’InfoObject existant. Pour plus d’informations sur cette boîte de dialogue, consultez [Rechercher un InfoObject](look-up-infoobject.md).  
  
 Après avoir sélectionné un InfoObject existant, le composant remplit les colonnes **InfoObject** et **Type** avec les valeurs sélectionnées.  
  
 **Iobject - Nouveau**  
 Créez un nouvel InfoObject et associez ce nouvel InfoObject à la colonne de flux de données de la ligne actuelle. Pour créer l’InfoObject, cliquez sur **Nouveau**, puis utilisez la boîte de dialogue **Créer un nouvel InfoObject** pour créer l’InfoObject. Pour plus d'informations sur cette boîte de dialogue, consultez [Create New InfoObject](create-new-infoobject.md).  
  
 Après avoir créé un InfoObject, le composant remplit les colonnes **InfoObject** et **Type** avec les nouvelles valeurs.  
  
 **Iobject - Supprimer**  
 Supprimez l'association entre l'InfoObject et la colonne de flux de données de la ligne actuelle. Pour supprimer cette association, cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
