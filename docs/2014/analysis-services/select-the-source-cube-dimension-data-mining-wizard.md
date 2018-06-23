---
title: Sélectionnez la Dimension de Cube Source (Assistant exploration de données) | Documents Microsoft
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
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ddd4affa954cf080cec3ad1ca37df82d494221e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038195"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a>Sélectionner la dimension de cube source (Assistant Exploration de données)
  Utilisez la page **Sélectionner la dimension de cube source** pour sélectionner la dimension du cube qui contient les cas à analyser. Par exemple, si vous créez un modèle qui analyse le comportement d'achat de clients en fonction de données démographiques, vous devez sélectionner la dimension Customer, qui contient généralement un enregistrement unique pour chaque client et différents attributs représentant des données démographiques, telles que le sexe, l'adresse ou le revenu. Ultérieurement dans l'Assistant, vous aurez la possibilité d'ajouter une table liée à cette table de cas : par exemple, vous pourrez ajouter une table imbriquée qui montre les produits que le client a achetés.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **À partir d’un cube existant** dans la page **Sélectionner la méthode de définition** de l’Assistant.  
  
## <a name="options"></a>Options  
 **Sélectionnez une Dimension de Cube Source**  
 Sélectionnez la dimension du cube qui fournira la source de données à votre structure d'exploration de données.  
  
## <a name="choosing-a-dimension"></a>Choix d'une dimension  
 Comme vous pouvez sélectionner une seule dimension à utiliser dans votre modèle, il est important que vous compreniez la structure du cube et que vous sélectionniez la dimension qui fournit les meilleures informations pour votre modèle. Si vous ne savez pas précisément quelle dimension utiliser, il peut être utile de parcourir le cube et de passer en revue les champs et les données qu'ils contiennent à l'aide du Concepteur de dimensions. Pour plus d’informations, consultez [Explorer les données d’une dimension dans le Concepteur de dimensions](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).  
  
 Si vous n’êtes pas familiarisé avec les dimensions en général, consultez [Présentation des dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 Pour plus d’informations sur le type d’informations généralement contenues dans une dimension unique, notamment les attributs et les mesures qui peuvent être utiles pour l’exploration de données, consultez [Relations de dimension](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Si la dimension que vous choisissez ne contient pas tous les attributs associés dont vous avez besoin pour générer le modèle d'exploration de données, vous devrez peut-être modifier la dimension. Pour plus d’informations, consultez [Définir un article](multidimensional-models/define-database-dimensions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Créer la Structure d’exploration de données &#40;Assistant exploration de données&#41;](create-the-data-mining-structure-data-mining-wizard.md)   
 [Sélectionnez la clé de cas &#40;Assistant exploration de données&#41;](select-the-case-key-data-mining-wizard.md)  
  
  