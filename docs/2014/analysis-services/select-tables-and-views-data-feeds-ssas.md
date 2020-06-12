---
title: Sélectionner des tables et des vues (flux de données) (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ee72d4347e85851388b4a4ab1f4d29b33a89134
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858124"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a>Sélectionner des tables et des vues (flux de données) (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de sélectionner les tables et les vues à partir desquelles vous voulez importer des données. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 L'apparence des tables et des vues dans cette page ne garantit pas que l'importation réussira. Si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée, l'importation échouera.  
  
 Pour les sources de données qui utilisent l'Authentification Windows, les informations d'identification de l'utilisateur actuel sont utilisées pour extraire les tables et les vues dans la boîte de dialogue Sélectionner des tables et des vues. Pour d'autres sources de données, les informations d'identification fournies dans la chaîne de connexion sont utilisées pour extraire les données.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **URL du flux de données**  
 Affiche l'URL pour le flux de données que vous avez sélectionné.  
  
 **Tables et vues**  
 Affiche la liste des tables et des vues dans la source des données. Activez la case à cocher en regard de chaque table et vue que vous souhaitez importer.  
  
 **Table source**  
 Spécifie le nom de la table source en fonction du type de source de données.  
  
 **Nom convivial**  
 Spécifie le nom convivial de la table source. Par défaut, la colonne affiche le nom de la table source qui apparaît dans la colonne **Table source** .  
  
 **Détails du filtre**  
 Affiche le filtre d’importation de données dans la boîte de dialogue **Détails du filtre** quand un filtre a été appliqué aux données importées. Pour plus d’informations, consultez [Détails du filtre &#40;SSAS&#41;](filter-details-ssas.md).  
  
 **Afficher un aperçu et filtrer**  
 Affiche la boîte de dialogue **Aperçu de la table sélectionnée** qui permet d’appliquer un filtre aux données importées. Pour plus d’informations, consultez [Aperçu de la table sélectionnée &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Sélectionner les tables associées**  
 Sélectionnez les tables associées aux tables et aux vues que vous avez sélectionnées.  
  
  
