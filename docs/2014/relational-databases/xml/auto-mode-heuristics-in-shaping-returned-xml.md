---
title: Heuristique du mode AUTO permettant de définir la forme des données XML renvoyées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91fa97c61734f378163fdac9adf1918caefabc7a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288911"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>Heuristique du mode AUTO permettant de définir la forme des données XML renvoyées
  Le mode AUTO détermine la forme des données XML renvoyées en fonction de la requête. Lors de la définition de l'imbrication des éléments, l'heuristique du mode AUTO compare les valeurs de colonnes de lignes adjacentes. Les colonnes de tous les types, sauf **ntext**, **text**, **image**et **xml**, sont comparées. Les colonnes de type **(n)varchar(max)** et **varbinary(max)** sont comparées.  
  
 L'exemple suivant illustre l'heuristique du mode AUTO qui détermine la forme des données XML obtenues :  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 Pour déterminer à quel endroit commence un nouvel élément <`T1`>, toutes les valeurs de colonne de T1, sauf **ntext**, **text**, **image** et **xml**, sont comparées si la clé de la table T1 n’est pas spécifiée. Ensuite, supposons que la colonne **Name** soit de type **nvarchar(40)** et que l’instruction SELECT renvoie l’ensemble de lignes suivant :  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 L'heuristique du mode AUTO compare toutes les valeurs de la table T1, les colonnes Id et Name. Étant donné que les deux premières lignes contiennent les mêmes valeurs pour les colonnes Id et Name, un élément \<T1> possédant deux éléments enfants \<T2> est ajouté au résultat.  
  
 Voici le document XML renvoyé :  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 Supposons maintenant que la colonne Name soit de type **text** . L'heuristique du mode AUTO ne compare pas les valeurs de ce type. Au lieu de cela, elle considère que les valeurs ne sont pas identiques. Cela aboutit à la génération de données XML suivante :  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [UTiliser le mode AUTO avec FOR XML](use-auto-mode-with-for-xml.md)  
  
  
