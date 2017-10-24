---
title: "Utilisation de l’extraction pour récupérer la Source de données (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9470c5edd50bab3622ad73f3e3404a4747b07dd7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>Manipulation de données MDX - extraire à l’aide de l’extraction des données Source
  L’instruction MDX (Multidimensional Expressions) utilise l’instruction [DRILLTHROUGH](../../../mdx/mdx-data-manipulation-drillthrough.md)pour récupérer un ensemble de lignes à partir des données sources d’une cellule d’un cube.  
  
 Pour exécuter une instruction **DRILLTHROUGH** sur un cube, une action d’extraction doit être définie pour ce dernier. Pour définir une action d’extraction, dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], dans le Concepteur de cube, dans la barre d’outils du volet **Actions** , cliquez sur **Nouvelle action d’extraction**. Dans la nouvelle action d’extraction, spécifiez le nom de l’action, la cible, la condition et les colonnes retournées par une instruction **DRILLTHROUGH** .  
  
## <a name="drillthrough-statement-syntax"></a>Syntaxe de l'instruction DRILLTHROUGH  
 L’instruction **DRILLTHROUGH** utilise la syntaxe suivante :  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 La clause **SELECT** identifie la cellule du cube qui contient les données sources à récupérer. Cette clause **SELECT** est identique à une instruction **SELECT** MDX ordinaire, à la différence qu’un seul membre peut être spécifié sur chaque axe dans la clause **SELECT** . Si plusieurs membres sont spécifiés sur un axe, une erreur se produit.  
  
 La syntaxe `<Max_Rows>` spécifie le nombre maximum de lignes de chaque ensemble de lignes retourné. Si le fournisseur OLE DB utilisé pour la connexion à la source de données ne prend pas en charge **DBPROP_MAXROWS**, le paramètre `<Max_Rows>` est ignoré.  
  
 La syntaxe `<First_Rowset>` identifie la partition d’où l’ensemble de lignes est d’abord retourné.  
  
 La syntaxe `<Return_Columns>` identifie les colonnes de la base de données sous-jacente à retourner.  
  
## <a name="drillthrough-statement-example"></a>Exemple d'instruction DRILLTHROUGH  
 L’exemple suivant illustre l’utilisation de l’instruction **DRILLTHROUGH** . Dans cet exemple, l'instruction DRILLTHROUGH interroge les feuilles des dimensions Store, Product et Time le long de la dimension Stores (axe de découpage), puis retourne le groupe de mesures du service, l'ID de service et le prénom de l'employé.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manipulation de données &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  

