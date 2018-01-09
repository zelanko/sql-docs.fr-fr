---
title: "Créer un compte Finance de Dimension de type parent-enfant | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d634c9bc44141a904c5bd3041c30afb108dbbaf3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>Dimensions de la base de données - compte Finance de type parent-enfant
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une dimension de type de compte est une dimension dont les attributs représentent un graphique de comptes pour générer des rapports financiers.  
  
 Une dimension de comptes permet de gérer dans le temps et de manière sélective le comportement de l'agrégation dans les comptes. Un compte de dimensions permet également d'utiliser un mécanisme standard pour résoudre la plupart des problèmes d'agrégation non standard associés généralement aux solutions décisionnelles qui gèrent des données financières. Si vous ne disposiez pas d'un tel mécanisme standard, la résolution des problèmes d'agrégation non standard nécessiterait des formules de cumul personnalisées, des membres calculés ou des scripts d'expression multidimensionnelle (MDX, Multidimensional Expressions).  
  
 Pour définir une dimension sous la forme d’une dimension de comptes, affectez à la propriété **Type** de la dimension la valeur **Accounts**.  
  
## <a name="dimension-structure"></a>Structure de la dimension  
 Une dimension de comptes contient au moins deux attributs :  
  
-   Un attribut clé qui identifie les comptes individuels dans la table de la dimension de comptes.  
  
-   Un attribut de compte, un attribut parent qui décrit comment les comptes sont organisés hiérarchiquement dans la dimension de comptes.  
  
     Pour définir un attribut comme attribut de compte, affectez à la propriété **Type** de l’attribut la valeur **Account** et à la propriété **Usage** , la valeur **Parent**.  
  
 Les dimensions de comptes peuvent éventuellement contenir les attributs suivants :  
  
-   Un attribut de type de compte qui définit le type de chacun des comptes de la dimension. Les noms des membres de l’attribut de type de compte sont associés aux types de comptes définis pour la base de données ou le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , et indiquent la fonction d’agrégation utilisée par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour ces comptes. Vous pouvez également utiliser des opérateurs unaires ou des formules de cumul personnalisées pour déterminer le comportement d'agrégation des attributs de comptes, mais les types de comptes permettent d'appliquer aisément un comportement cohérent à un graphique de comptes sans avoir à modifier la base de données relationnelle sous-jacente.  
  
     Pour identifier un attribut de type de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountType**.  
  
-   Un attribut de nom de compte qui est utilisé pour générer des rapports. Pour identifier un attribut de nom de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountName**.  
  
-   Un attribut de numéro de compte qui est utilisé pour générer des rapports. Pour identifier un attribut de numéro de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountNumber**.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Ajout de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l’Assistant Business Intelligence pour ajouter des fonctions d’intelligence comptable, telles que l’identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d'attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Aide F1 l’Assistant Business Intelligence](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Types de dimensions](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
