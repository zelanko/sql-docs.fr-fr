---
title: Se connecter à un fichier plat (SSAS) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 288130652e609b65a4bbdaae8dea1f2647771aad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045272"
---
# <a name="connect-to-a-flat-file-ssas"></a>Connexion à un fichier plat (SSAS)
  Cette page de **l’Assistant Importation de table** vous permet de vous connecter à un fichier plat (.txt), un fichier séparé par des tabulations (.tab) ou un fichier séparé par des virgules (.csv). Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à un fichier plat, le fournisseur ACE doit être installé sur votre ordinateur. Pour plus d’informations, consultez [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'un fichier dans cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire le fichier sélectionné.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Chemin d'accès au fichier**  
 Spécifiez le chemin d'accès complet du fichier.  
  
 **Parcourir**  
 Accédez à un emplacement dans lequel un fichier est disponible.  
  
 **Séparateur de colonnes**  
 Effectuez une sélection dans une liste de séparateurs de colonnes disponibles. Choisissez un séparateur qu'il est peu probable de rencontrer dans le texte.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Tabulation (t)|Les colonnes sont séparées par une tabulation (t).|  
|Virgule (,)|Les colonnes sont séparées par une virgule (,).|  
|Point-virgule (;)|Les colonnes sont séparées par un point-virgule (;).|  
|Espace ( )|Les colonnes sont séparées par un espace ().|  
|deux-points (:)|Les colonnes sont séparées par un deux-points (:).|  
|Barre verticale (&#124;)|Les colonnes sont séparées par une barre verticale (&#124;).|  
  
 **Avancé**  
 Spécifiez les options de paramètres régionaux et d'encodage pour le fichier plat.  
  
 **Utiliser la première ligne comme en-têtes de colonnes**  
 Spécifiez s'il convient d'utiliser la première ligne de données comme en-têtes de colonnes de la table de destination.  
  
 **Aperçu des données**  
 Affichez un aperçu des données dans le fichier sélectionné et utilisez les options suivantes pour modifier l'importation de données.  
  
> [!NOTE]  
>  Seules les 50 premières lignes du fichier sont affichées dans cet aperçu.  
  
|Option|Description|  
|------------|-----------------|  
|**Case à cocher dans l’en-tête de colonne**|Activez la case à cocher pour inclure la colonne lors de l'importation des données. Désactivez la case à cocher pour supprimer la colonne lors de l'importation de données.|  
|**Bouton de flèche vers le bas dans l’en-tête de colonne**|Triez et filtrez les données dans la colonne.|  
  
 **Désactivez les filtres de lignes**  
 Supprimez tous les filtres appliqués aux données dans les colonnes.  
  
  