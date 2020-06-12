---
title: Aperçu de la table sélectionnée (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84540071"
---
# <a name="preview-selected-table-ssas"></a>Aperçu de la table sélectionnée (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet d'afficher un aperçu des données dans la table sélectionnée, pour sélectionner les colonnes à inclure dans l'importation de données et pour filtrer des données dans les colonnes sélectionnées. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Les lignes de la table ne sont pas toutes affichées. Toutefois, les filtres que vous définissez sont appliqués à toutes les données de la table pendant l'importation.  
  
 Pour les sources de données qui utilisent l'Authentification Windows, les informations d'identification de l'utilisateur actuel sont utilisées pour extraire les données affichées dans la boîte de dialogue Afficher un aperçu et filtrer. Pour d'autres sources de données, les informations d'identification fournies dans la chaîne de connexion sont utilisées pour extraire les données.  
  
 L'apparence des données dans cette page ne garantit pas que l'importation réussira. Si le nom d'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire la base de données sélectionnée, l'importation échouera.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **Case à cocher dans l'en-tête de colonne**  
 Activez la case à cocher pour inclure la colonne lors de l'importation des données. Désactivez la case à cocher pour supprimer la colonne lors de l'importation de données.  
  
 **Bouton Flèche vers le bas dans l'en-tête de colonne**  
 Filtrez les données dans la colonne.  
  
 **Désactiver les filtres de lignes**  
 Supprimez tous les filtres appliqués aux données dans les colonnes.  
  
  
