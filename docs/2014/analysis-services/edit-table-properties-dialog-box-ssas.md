---
title: Modifier la boîte de dialogue Propriétés Table (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd8e464967dbe4b2546f51889f2a2da49d81e4df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249589"
---
# <a name="edit-table-properties-dialog-box-ssas"></a>Modifier les propriétés de la table, boîte de dialogue (SSAS)
  La boîte de dialogue **Modifier les propriétés de la table** vous permet d'afficher et de modifier les propriétés des tables importées dans le générateur de modèles à l'aide de l'Assistant Importation de table. Pour accéder à cette boîte de dialogue, dans le générateur de modèles, sélectionnez une table, puis cliquez sur le menu **Table** , puis sur **Propriétés de la table**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Les options proposées dans cette boîte de dialogue diffèrent selon que vous avez initialement importé les données en sélectionnant des tables dans une liste ou en utilisant une requête SQL.  
  
## <a name="table-preview-mode"></a>Mode Aperçu de la table  
 **Nom de la table**  
 Affiche le nom de la table de données dans le modèle.  
  
> [!NOTE]  
>  Vous ne pouvez pas en modifier le nom à cet endroit. Toutefois, vous pouvez modifier le nom de la table en cliquant avec le bouton droit sur l'onglet de table en bas du générateur de modèles.  
  
 **Nom de la connexion**  
 Affiche le nom de la connexion qui est actuellement en cours d'utilisation.  
  
 **Nom de la source**  
 Affichez ou modifiez la table à partir de laquelle les données sont obtenues.  
  
 Si vous modifiez la source en une table qui comporte des colonnes différentes de la table actuelle, un message s'affiche pour vous avertir que les colonnes sont différentes. Vous devez ensuite sélectionner les colonnes que vous souhaitez placer dans la table actuelle et cliquer sur **Enregistrer**. Vous pouvez remplacer la table entière en activant la case à cocher située à la gauche de la table.  
  
> [!NOTE]  
>  Lorsque vous modifiez la source de données d'une table, vous remplacez essentiellement le contenu de la table actuelle par le contenu de la nouvelle table source.  
  
 **Noms de colonnes**  
 |||  
|-|-|  
|**Source**|Sélectionnez cette option pour remplacer les noms de colonnes actuels par les noms de colonnes de la table source sélectionnée.|  
|**Modèle**|Sélectionnez cette option pour utiliser les noms de colonne actuels tels qu'ils existent dans le modèle.|  
  
 **Actualiser l’aperçu**  
 Cliquez pour examiner les colonnes de données dans la table source actuellement sélectionnée.  
  
 **Basculer vers**  
 |||  
|-|-|  
|**Aperçu de la table**|Sélectionnez cette option pour afficher un aperçu de la table sélectionnée et un nombre limité de lignes de données.|  
|**Éditeur de requête**|Sélectionnez cette option pour examiner la requête sur la source de données sélectionnée. Cette option n'est pas disponible pour toutes les sources de données.|  
  
 **Case à cocher dans l’en-tête de colonne**  
 Activez la case à cocher pour inclure la colonne lors de l'importation des données. Désactivez la case à cocher pour supprimer la colonne lors de l'importation de données.  
  
 **Bouton de flèche vers le bas dans l’en-tête de colonne**  
 Filtrez les données dans la colonne.  
  
 **Filtres de lignes clair**  
 Cliquez pour supprimer tous les filtres qui ont été appliqués.  
  
 **OK**  
 Cliquez pour appliquer toutes les modifications que vous avez apportées, notamment le remplacement des colonnes.  
  
## <a name="query-design-mode"></a>Mode Conception de requête  
 **Nom de la table**  
 Affiche le nom de la table de données dans le modèle.  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier le nom ici ; toutefois, vous pouvez modifier le nom de la table en cliquant avec le bouton droit sur l'onglet de table en bas du concepteur.  
  
 **Nom de la connexion**  
 Affiche le nom de la connexion qui est actuellement en cours d'utilisation.  
  
 **Basculer vers**  
 |||  
|-|-|  
|**Aperçu de la table**|Sélectionnez cette option pour afficher un aperçu de la table sélectionnée et quelques lignes de données.|  
|**Éditeur de requête**|Sélectionnez cette option pour examiner la requête qui sera émise sur la source de données sélectionnée.|  
  
 **Instruction SQL**  
 Affiche l'instruction SQL émise sur la source de données actuelle afin de récupérer des lignes. Par défaut, toutes les lignes sont récupérées, mais vous pouvez récupérer un sous-ensemble de lignes, soit en concevant un filtre, soit en modifiant manuellement l'instruction SQL.  
  
 **Valider**  
 Cliquez pour vérifier que l'instruction est syntaxiquement correcte pour le fournisseur et la source de données sélectionnés.  
  
 **Conception**  
 Cliquez pour ouvrir un concepteur de requêtes visuel et générer une instruction de requête. Pour plus d'informations sur l'utilisation du concepteur, appuyez sur F1 dans le concepteur.  
  
 **OK**  
 Cliquez pour appliquer toutes les modifications que vous avez apportées, notamment le remplacement des colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes &#40;SSAS tabulaire&#41;](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
