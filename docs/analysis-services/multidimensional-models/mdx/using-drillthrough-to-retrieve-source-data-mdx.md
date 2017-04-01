---
title: "Utilisation de l&#39;instruction DRILLTHROUGH pour r&#233;cup&#233;rer des donn&#233;es sources (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "instruction DRILLTHROUGH"
  - "récupération des données"
  - "requêtes [MDX], instruction DRILLTHROUGH"
  - "récupération de données [MDX]"
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Utilisation de l&#39;instruction DRILLTHROUGH pour r&#233;cup&#233;rer des donn&#233;es sources (MDX)
  L’instruction MDX (Multidimensional Expressions) utilise l’instruction [DRILLTHROUGH](../Topic/DRILLTHROUGH%20Statement%20\(MDX\).md) pour récupérer un ensemble de lignes à partir des données sources d’une cellule d’un cube.  
  
 Pour exécuter une instruction **DRILLTHROUGH** sur un cube, une action d’extraction doit être définie pour ce dernier. Pour définir une action d’extraction, dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], dans le Concepteur de cube, dans la barre d’outils du volet **Actions**, cliquez sur **Nouvelle action d’extraction**. Dans la nouvelle action d’extraction, spécifiez le nom de l’action, la cible, la condition et les colonnes retournées par une instruction **DRILLTHROUGH**.  
  
## Syntaxe de l'instruction DRILLTHROUGH  
 L’instruction **DRILLTHROUGH** utilise la syntaxe suivante :  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 La clause **SELECT** identifie la cellule du cube qui contient les données sources à récupérer. Cette clause **SELECT** est identique à une instruction **SELECT** MDX ordinaire, à la différence qu’un seul membre peut être spécifié sur chaque axe dans la clause **SELECT**. Si plusieurs membres sont spécifiés sur un axe, une erreur se produit.  
  
 La syntaxe `<Max_Rows>` spécifie le nombre maximum de lignes de chaque ensemble de lignes retourné. Si le fournisseur OLE DB utilisé pour la connexion à la source de données ne prend pas en charge **DBPROP_MAXROWS**, le paramètre `<Max_Rows>` est ignoré.  
  
 La syntaxe `<First_Rowset>` identifie la partition d’où l’ensemble de lignes est d’abord retourné.  
  
 La syntaxe `<Return_Columns>` identifie les colonnes de la base de données sous-jacente à retourner.  
  
## Exemple d'instruction DRILLTHROUGH  
 L’exemple suivant illustre l’utilisation de l’instruction **DRILLTHROUGH**. Dans cet exemple, l'instruction DRILLTHROUGH interroge les feuilles des dimensions Store, Product et Time le long de la dimension Stores (axe de découpage), puis retourne le groupe de mesures du service, l'ID de service et le prénom de l'employé.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## Voir aussi  
 [Manipulation de données &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/manipulating-data-mdx.md)  
  
  