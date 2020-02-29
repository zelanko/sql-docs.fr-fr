---
title: Attributs basés sur un domaine (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: db0e312fabc039de2554f00b7e9f33a7a76ec584
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176058"
---
# <a name="domain-based-attributes-master-data-services"></a>Attributs basés sur un domaine (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un attribut basé sur un domaine est un attribut dont les valeurs sont remplies par les membres d'une autre entité. Vous pouvez considérer un attribut basé sur un domaine sous la forme d'une liste contrainte ; les attributs basés sur un domaine empêchent les utilisateurs d'entrer des valeurs d'attribut qui sont valides. Pour sélectionner une valeur d'attribut, l'utilisateur doit choisir dans une liste.

## <a name="domain-based-attribute-example"></a>Exemple d'attribut basé sur un domaine
 Dans l'image suivante, l'entité Product a un attribut basé sur un domaine appelé Subcategory. L'attribut Subcategory est rempli par les valeurs de l'entité Subcategory.

 L'entité Subcategory a un attribut basé sur un domaine appelé Category. L'attribut Category est rempli par les valeurs de l'entité Category.

 ![Attributs basés sur un domaine à une entité](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Attributs basés sur un domaine à une entité")

## <a name="use-same-entity-for-multiple-domain-based-attributes"></a>Utiliser des attributs basés sur un domaine dans la même entité
 Vous pouvez utiliser la même entité en tant qu'attribut basé sur un domaine de plusieurs entités. Par exemple, vous pouvez créer une entité appelée YesNoIndicator avec les membres : Yes, No et Maybe. Vous pouvez créer un attribut basé sur un domaine nommé InStock et utiliser l'entité YesNoIndicator comme source. Vous pouvez également créer un autre attribut basé sur un domaine nommé Approved et utiliser l'entité YesNoIndicator comme source. Lorsque vous voulez que les utilisateurs choisissent dans une liste des membres de l'entité YesNoIndicator, vous pouvez utiliser l'entité comme attribut basé sur un domaine.

## <a name="domain-based-attributes-form-derived-hierarchies"></a>Les attributs basés sur un domaine forment les hiérarchies dérivées
 Les relations d'attributs basés sur un domaine sont à la base des hiérarchies dérivées. Pour plus d’informations, consultez [Hiérarchies dérivées &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).

## <a name="related-tasks"></a>Tâches associées

|Description de la tâche|Rubrique|
|----------------------|-----------|
|Créer un attribut basé sur un domaine qui provient d'une entité existante.|[Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|Créez une entité.|[Créer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a>Contenu associé

-   [Hiérarchies dérivées &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)

-   [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)

-   [Entités &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)


