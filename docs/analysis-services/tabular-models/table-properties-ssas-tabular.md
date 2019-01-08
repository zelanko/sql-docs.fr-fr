---
title: Propriétés de la table de modèle tabulaire à Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5104eacafe60ab3fd1ea1ff29cc64b8453e4ff7
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072006"
---
# <a name="table-properties"></a>Propriétés de la table 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Cet article décrit les propriétés de la table modèle tabulaire. Les propriétés décrites ici sont différentes de celles figurant dans la boîte de dialogue Modifier les propriétés de la table, lesquelles définissent les colonnes importées de la source.  
  
 Sections de cette rubrique :  
  
-   [Propriétés de la table](#bkmk_properties)  
  
-   [Configurer les paramètres de propriété de table](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> Propriétés de la table  
 **De base**  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Nom de la connexion**|\<nom de la connexion >|Le nom de la connexion à la source de données de la table.<br /><br /> Pour modifier la connexion, cliquez sur le bouton.|  
|**Hidden**|False|Spécifie si la table est masquée dans les listes de champs de client de création de rapports.|  
|**Partitions**||Les partitions de la table ne peuvent pas être affichées dans la fenêtre **Propriétés** . Pour afficher, créer ou modifier des partitions, cliquez sur le bouton pour ouvrir le Gestionnaire de partition.|  
|**Données sources**||Les données sources de la table ne peuvent pas être affichées dans la fenêtre **Propriétés** . Pour afficher ou modifier les données sources, cliquez sur le bouton pour ouvrir la boîte de dialogue Modifier les propriétés de la table.|  
|**Description de la table**||Description textuelle de la table.<br /><br /> Dans [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], si un utilisateur positionne le curseur sur cette table dans la liste des champs, la description apparaît sous la forme d'une info-bulle.|  
|**Nom de la table**|\<nom convivial >|Spécifie le nom convivial de la table. Le nom de la table peut être spécifié lorsqu'une table est importée à l'aide de l'Assistant Importation de table ou à tout moment après l'importation. Le nom de la table dans le modèle peut être différent de la table associée à la source. Le nom convivial de la table s'affiche dans la liste de champs de l'application cliente de création de rapports ainsi que dans la base de données model dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
 **Propriétés de la création de rapports**  
  
 Pour une description détaillée et des informations de configuration pour les propriétés de création de rapports, consultez [propriétés de rapport Power View](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md).  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Ensemble de champs par défaut**|||  
|Comportement de la table|||  
  
##  <a name="bkmk_config_prop"></a> Configurer les paramètres de propriété de table  
  
1.  Dans le concepteur de modèles, dans la vue de données, cliquez sur une table (onglet) ou, dans la vue du diagramme, cliquez sur un en-tête de table.  
  
2.  Dans la fenêtre **Propriétés** , cliquez sur une propriété, puis tapez une valeur ou cliquez sur le bouton pour afficher des options de configuration supplémentaires.  
  
  
