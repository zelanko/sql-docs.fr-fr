---
title: Instruction DRILLTHROUGH (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ee90d2c367fa289e8255a84e4eb6da19b37933e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68891205"
---
# <a name="mdx-data-manipulation---drillthrough"></a>Manipulation de données MDX - DRILLTHROUGH


  Extrait les lignes de la table sous-jacente qui ont été utilisées pour créer une cellule spécifiée dans un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Unsigned_Integer*  
 Valeur d'entier positif.  
  
 *Instruction SELECT MDX*  
 N'importe quelle instruction SELECT MDX (Multidimensional Expressions) valide.  
  
 *Set_of_Attributes_and_Measures*  
 Liste séparée par des virgules d'attributs de dimension et de mesures.  
  
## <a name="remarks"></a>Notes  
 L'extraction est une opération au cours de laquelle un utilisateur final sélectionne une cellule unique dans un cube et extrait un ensemble de résultats des données source de cette cellule pour se procurer des informations plus détaillées. Par défaut, un ensemble de résultats obtenus par extraction provient des lignes de la table qui ont été évaluées afin de calculer la valeur de la cellule sélectionnée dans le cube. Pour être en mesure de procéder à une extraction, les utilisateurs finaux doivent disposer de cette fonctionnalité sur leurs applications clientes. Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], les résultats sont récupérés directement à partir du stockage MOLAP, à moins que les partitions ou les dimensions ROLAP soient interrogées.  
  
> [!IMPORTANT]  
>  La sécurité de l'extraction est basée sur les options de sécurité générales définies dans le cube. Si un utilisateur ne parvient pas à se procurer des données via MDX, l'extraction limite aussi l'utilisateur exactement de la même manière.  
  
 Une instruction MDX spécifie la cellule concernée. La valeur spécifiée par l’argument **MaxRows** indique le nombre maximal de lignes qui doivent être retournées par l’ensemble de lignes obtenu.  
  
 Par défaut, le nombre maximal de lignes qui sont retournées est de 10 000 lignes. Cela signifie que si vous ne spécifiez pas **MaxRows** , vous obtiendrez 10 000 lignes ou moins. Si cette valeur est trop faible pour votre scénario, vous pouvez définir **MaxRows** sur un nombre plus élevé, tel `MAXROWS 20000`que. Si elle est trop faible, vous pouvez augmenter la valeur par défaut en modifiant la propriété du serveur **OLAP\Query\DefaultDrillthroughMaxRows** . Pour plus d’informations sur la modification de cette propriété, consultez [Propriétés du serveur dans Analysis Services](https://docs.microsoft.com/analysis-services/server-properties/server-properties-in-analysis-services).  
  
 Sauf indication contraire, les colonnes retournées incluent tous les attributs de granularité de toutes les dimensions (autres que les dimensions de type plusieurs à plusieurs) associées au groupe de mesures. Les dimensions du cube sont précédées du signe $ afin de distinguer les dimensions et les groupes de mesures. La clause **Return** est utilisée pour spécifier les colonnes retournées par la requête d’extraction. Les fonctions suivantes peuvent être appliquées à un seul attribut ou mesure par la clause **Return** .  
  
 Name(attribute_name)  
 Retourne le nom du membre d'attribut spécifié.  
  
 UniqueName(attribute_name)  
 Retourne le nom unique du membre d'attribut spécifié.  
  
 Key(attribute_name[, N])  
 Retourne la clé du membre d'attribut spécifié, où N spécifie la colonne dans la clé composite (le cas échéant). La valeur par défaut pour N est 1.  
  
 Caption(attribute_name)  
 Retourne la légende du membre d'attribut spécifié.  
  
 MemberValue(attribute_name)  
 Retourne la valeur de membre du membre d'attribut spécifié.  
  
 CustomRollup(attribute_name)  
 Retourne l'expression de cumul personnalisé du membre d'attribut spécifié.  
  
 CustomRollupProperties(attribute_name)  
 Retourne les propriétés de cumul personnalisé du membre d'attribut spécifié.  
  
 UnaryOperator(attribute_name)  
 Retourne l'opérateur unaire du membre d'attribut spécifié.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant spécifie la cellule du mois de juillet 2007 pour la mesure (mesure par défaut) Reseller Sales Amount (montant des ventes du revendeur) pour l'Australie. La clause RETURN précise que les valeurs sous-jacentes de cette cellule (valeurs concernant la date de chaque vente, le nom du modèle de produit, le nom de l'employé, le montant des ventes, le montant des taxes et le coût du produit) sont à retourner.  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de manipulation de données MDX &#40;&#41;MDX](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
