---
title: Jointure de fusion, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.mergejointrans.f1
helpviewer_keywords:
- datasets [Integration Services]
- Merge Join transformation
- datasets [Integration Services], joining
- joining datasets [Integration Services]
- joins [SQL Server], SSIS
ms.assetid: cd8b0412-f83b-4bd2-b227-e53dcfd941a8
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d59d600d78aaf70a601382df1cacdea560db1073
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042945"
---
# <a name="merge-join-transformation"></a>transformation de jointure de fusion
  La transformation de jointure de fusion fournit une sortie générée par la réunion, à l'aide d'une jointure FULL, LEFT ou INNER, de deux ensembles de données triés. Par exemple, vous pouvez utiliser une jointure LEFT pour associer une table comprenant des informations sur des produits à une table indiquant le pays ou la région dans lesquels un produit a été fabriqué. Le résultat est une table qui répertorie tous les produits et leur pays ou région d'origine.  
  
 Vous pouvez configurer la transformation de jointure de fusion comme suit :  
  
-   Indiquez si la jointure est une jointure FULL, LEFT ou INNER.  
  
-   Spécifiez les colonnes utilisées par la jointure.  
  
-   Indiquez si la transformation traite les valeurs NULL comme des valeurs égales.  
  
    > [!NOTE]  
    >  Si les valeurs NULL ne sont pas traitées comme des valeurs égales, la transformation les gère de la même manière que le moteur de base de données SQL Server.  
  
 Cette transformation a deux entrées et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="input-requirements"></a>Spécifications relatives aux entrées  
 La transformation de jointure de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
## <a name="join-requirements"></a>Spécifications relatives à la jointure  
 La transformation de jointure de fusion requiert que les colonnes jointes aient des métadonnées correspondantes. Par exemple, vous ne pouvez pas joindre une colonne d'un type de données numérique à une colonne d'un type de données caractère. Si les données sont du type de données chaîne, la colonne de la deuxième entrée doit avoir une longueur inférieure ou égale à celle de la colonne de la première entrée avec laquelle elle est fusionnée.  
  
## <a name="buffer-throttling"></a>Limitation du nombre de tampons  
 Vous n’avez plus à configurer la valeur de la `MaxBuffersPerInput` propriété, car Microsoft a apporté des modifications qui réduisent le risque que la transformation de jointure de fusion consomme trop de mémoire. Ce problème s'est quelquefois produit lorsque plusieurs entrées de jointure de fusion produisaient des données à des taux irréguliers.  
  
## <a name="related-tasks"></a>Related Tasks  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme.  
  
 Pour plus d'informations sur la définition des propriétés de cette transformation, cliquez sur l'une des rubriques suivantes :  
  
-   [Étendre un dataset à l'aide de la transformation de jointure de fusion](merge-join-transformation.md)  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Transformation de jointure de fusion](../../merge-join-transformation-editor.md)   
 [Transformation de fusion](merge-transformation.md)   
 [Union All Transformation](union-all-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  