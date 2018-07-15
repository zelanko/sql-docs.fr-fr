---
title: Copier et coller des données (SSAS tabulaire) | Microsoft Docs
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
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83b7c0c4b3861ff18008580e60d0b508c1526fd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224659"
---
# <a name="copy-and-paste-data-ssas-tabular"></a>Copier et coller des données (SSAS Tabulaire)
  Vous pouvez copier des données de table depuis des applications externes et les coller dans une table nouvelle ou existante du générateur de modèles. Les données que vous collez à partir du Presse-papiers doivent être au format HTML, notamment les données copiées à partir d’Excel ou de Word. Le générateur de modèles détecte et applique automatiquement les types de données aux données collées. Vous pouvez également modifier manuellement le type de données ou la mise en forme d'affichage d'une colonne.  
  
 Contrairement aux tables avec une connexion de source de données, les tables collées n'ont pas de propriété Nom de la connexion ou Données source. Les données collées sont persistantes dans le fichier model.bim. Lorsque le projet ou le fichier model.bim est enregistré, les données collées le sont également.  
  
 Lorsqu'un modèle est déployé, les données collées sont également déployées avec lui, que le modèle soit traité ou non avec le déploiement.  
  
 Sections de cette rubrique :  
  
-   [Conditions préalables](#bkmk_prerequisites)  
  
-   [Coller des données](#bkmk_paste_data)  
  
-   [Boîte de dialogue Aperçu avant collage](#bkmk_paste_preview)  
  
##  <a name="bkmk_prerequisites"></a> Conditions préalables  
 Certaines restrictions s'appliquent lorsque vous collez des données :  
  
-   Les tables collées ne peuvent pas compter plus de 10 000 lignes.  
  
-   Les tables collées ne peuvent pas être partitionnées.  
  
-   Les tables collées ne sont pas prises en charge en mode DirectQuery.  
  
-   Les options **Coller par ajout** et **Coller par remplacement** sont disponibles uniquement lors de l'utilisation d'une table créée initialement en collant des données à partir du Presse-papiers. Vous ne pouvez pas utiliser **Coller par ajout** ou **Coller par remplacement** pour ajouter des données dans une table de données importées provenant d'un autre type de source de données.  
  
-   Lorsque vous utilisez **Coller par ajout** ou **Coller par remplacement**, les nouvelles données doivent contenir exactement le même nombre de colonnes que les données originales. De préférence, les colonnes de données que vous collez ou ajoutez doivent également être du même type ou d'un type de données compatible avec celui figurant dans la table de destination. Dans certains cas, vous pouvez utiliser un type de données différent, mais une erreur **Incompatibilité de type** peut s’afficher.  
  
##  <a name="bkmk_paste_data"></a> Coller des données  
  
#### <a name="to-paste-data-into-the-designer"></a>Pour coller des données dans le générateur  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Édition** , puis sur l'une des options suivantes :  
  
    -   Cliquez sur **Coller** pour coller le contenu du Presse-papiers dans une nouvelle table.  
  
    -   Cliquez sur **Coller par ajout** pour coller le contenu du Presse-papiers sous forme de lignes supplémentaires dans la table sélectionnée. Les nouvelles lignes sont ajoutées à la fin de la table.  
  
    -   Cliquez sur **Coller par remplacement** pour remplacer la table sélectionnée par le contenu du Presse-papiers. Tous les noms d'en-têtes de colonnes existants restent dans la table, et les relations sont conservées.  
  
##  <a name="bkmk_paste_preview"></a> Boîte de dialogue Aperçu avant collage  
 La boîte de dialogue **Aperçu avant collage** vous permet d'afficher un aperçu des données copiées dans la fenêtre du concepteur et de vérifier qu'elles sont correctement copiées. Pour accéder à cette boîte de dialogue, copiez les données basées sur une table au format HTML dans le Presse-papiers puis, dans le générateur, dans le menu **Modifier** , cliquez sur **Coller**, **Coller par ajout**ou **Coller par remplacement**. Les options **Coller par ajout** et **Coller par remplacement** sont disponibles uniquement lorsque vous ajoutez ou remplacez des données dans une table qui a été créée par copier-coller depuis le Presse-papiers. Vous ne pouvez pas utiliser **Coller par ajout** ou **Coller par remplacement** pour ajouter des données dans une table de données importées.  
  
 Les options proposées dans cette boîte de dialogue diffèrent selon que vous collez des données dans une table complètement nouvelle, collez des données dans une table existante et remplacez les données existantes par les nouvelles, ou ajoutez des données à une table existante.  
  
### <a name="paste-to-new-table"></a>Coller dans une nouvelle table  
 **Nom de la table**  
 Spécifiez le nom de la table qui sera créée dans le concepteur.  
  
 **Données à coller**  
 Affiche un exemple du contenu du Presse-papiers qui sera ajouté à la table de destination.  
  
### <a name="paste-append"></a>Coller par ajout  
 **Données existantes dans la table**  
 Affiche un exemple des données existantes dans la table afin que vous puissiez vérifier les colonnes, les types de données, etc.  
  
 **Données à coller**  
 Affiche un exemple de contenu du Presse-papiers. Les données existantes seront ajoutées par ces données.  
  
### <a name="paste-replace"></a>Coller par remplacement  
 **Données existantes dans la table**  
 Affiche un exemple des données existantes dans la table afin que vous puissiez vérifier les colonnes, les types de données, etc.  
  
 **Données à coller**  
 Affiche un exemple de contenu du Presse-papiers. Les données existantes dans la table de destination sont supprimées et les nouvelles lignes sont insérées dans la table.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données &#40;SSAS tabulaire&#41;](import-data-ssas-tabular.md)   
 [Sources de données prises en charge &#40;SSAS tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md)   
 [Définissez le Type de données d’une colonne &#40;SSAS tabulaire&#41;](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
