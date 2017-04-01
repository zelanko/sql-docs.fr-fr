---
title: "Cr&#233;er un compte Finance de la dimension de type parent-enfant | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dimensions [Analysis Services], compte"
  - "dimensions de comptes [Analysis Services]"
  - "intelligence comptable, ajout"
  - "intelligence comptable [Analysis Services]"
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Cr&#233;er un compte Finance de la dimension de type parent-enfant
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une dimension de type compte est une dimension dont les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.  
  
 Une dimension de comptes permet de gérer dans le temps et de manière sélective le comportement de l'agrégation dans les comptes. Un compte de dimensions permet également d'utiliser un mécanisme standard pour résoudre la plupart des problèmes d'agrégation non standard associés généralement aux solutions décisionnelles qui gèrent des données financières. Si vous ne disposiez pas d'un tel mécanisme standard, la résolution des problèmes d'agrégation non standard nécessiterait des formules de cumul personnalisées, des membres calculés ou des scripts d'expression multidimensionnelle (MDX, Multidimensional Expressions).  
  
 Pour définir une dimension sous la forme d’une dimension de comptes, affectez à la propriété **Type** de la dimension la valeur **Accounts**.  
  
## Structure de la dimension  
 Une dimension de comptes contient au moins deux attributs :  
  
-   Un attribut clé qui identifie les comptes individuels dans la table de la dimension de comptes.  
  
-   Un attribut de compte, un attribut parent qui décrit comment les comptes sont organisés hiérarchiquement dans la dimension de comptes.  
  
     Pour définir un attribut comme attribut de compte, affectez à la propriété **Type** de l’attribut la valeur **Account** et à la propriété **Usage**, la valeur **Parent**.  
  
 Les dimensions de comptes peuvent éventuellement contenir les attributs suivants :  
  
-   Un attribut de type de compte qui définit le type de chacun des comptes de la dimension. Les noms des membres de l’attribut de type de compte sont associés aux types de comptes définis pour la base de données ou le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], et indiquent la fonction d’agrégation utilisée par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour ces comptes. Vous pouvez également utiliser des opérateurs unaires ou des formules de cumul personnalisées pour déterminer le comportement d'agrégation des attributs de comptes, mais les types de comptes permettent d'appliquer aisément un comportement cohérent à un graphique de comptes sans avoir à modifier la base de données relationnelle sous-jacente.  
  
     Pour identifier un attribut de type de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountType**.  
  
-   Un attribut de nom de compte qui est utilisé pour générer des rapports. Pour identifier un attribut de nom de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountName**.  
  
-   Un attribut de numéro de compte qui est utilisé pour générer des rapports. Pour identifier un attribut de numéro de compte, affectez à la propriété **Type** de l’attribut la valeur **AccountNumber**.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](../../analysis-services/multidimensional-models/configure-attribute-types.md).  
  
## Ajout de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l’Assistant Business Intelligence pour ajouter des fonctions d’intelligence comptable, telles que l’identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](../../analysis-services/multidimensional-models/add-account-intelligence-to-a-dimension.md).  
  
## Voir aussi  
 [Attributs et hiérarchies d'attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Aide (F1) de l'Assistant Business Intelligence](../Topic/Business%20Intelligence%20Wizard%20F1%20Help.md)   
 [Types de dimensions](../Topic/Dimension%20Types.md)  
  
  