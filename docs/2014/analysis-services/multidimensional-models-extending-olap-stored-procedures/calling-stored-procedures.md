---
title: Appel de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c9da6edef576a6ab25c183cbc87ff95cc056845
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545378"
---
# <a name="calling-stored-procedures"></a>Appel des procédures stockées
  Les procédures stockées peuvent être appelées sur le serveur ou à partir d'une application cliente. Dans les deux cas, les procédures stockées s'exécutent toujours sur le serveur, soit dans le contexte du serveur, soit dans le contexte d'une base de données. Aucune autorisation spéciale n'est requise pour exécuter une procédure stockée. Lorsqu'une procédure stockée est ajoutée par un assembly dans le contexte du serveur ou de la base de données, tous les utilisateurs peuvent l'exécuter, à condition que leur rôle autorise les actions qu'elle effectue.  
  
 L'appel d'une procédure stockée via MDX s'effectue de la même façon que l'appel d'une fonction MDX intrinsèque. Pour une procédure stockée n'acceptant pas de paramètres, le nom de la procédure et une paire de parenthèses vide sont utilisés, comme ci-après :  
  
```  
MyStoredProcedure()  
```  
  
 Si la procédure stockée accepte un ou plusieurs paramètres, ces derniers sont fournis, dans l'ordre, séparés par des virgules. L'exemple suivant montre un exemple de procédure stockée incluant trois paramètres :  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a>Appel de procédures stockées dans les requêtes MDX  
 Dans toutes les requêtes MDX, la procédure stockée doit retourner le type correct du point de vue de la syntaxe requis par une expression MDX. Si une procédure stockée ne retourne pas le type correct, une erreur MDX se produit. Les exemples suivants présentent des procédures stockées qui retournent un jeu, un membre et le résultat d'une opération mathématique.  
  
### <a name="returning-a-set"></a>Retour d'un jeu  
 Les exemples suivants implémentent une procédure stockée, nommée MySproc, qui retourne un jeu. Dans le premier exemple, MySproc retourne directement le jeu dans l'expression SELECT. Dans les deux autres exemples, MySproc retourne le jeu comme un argument pour les fonctions Crossjoin et DrilldownLevel.  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a>Retour d'un membre  
 L'exemple suivant montre une fonction MySproc qui retourne un membre :  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a>Retour du résultat d'une opération mathématique  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a>Appel de procédures stockées avec l'instruction Call  
 Les procédures stockées peuvent être appelées en dehors du contexte d'une requête MDX à l'aide de l'instruction `Call` MDX.  
  
 Vous pouvez utiliser cette méthode pour instancier les effets secondaires d'une requête stockée ou pour que l'application obtienne les résultats d'une requête stockée. L'instruction `Call` est souvent utilisée pour que les objets AMO (Analysis Management Objects) effectuent les fonctions d'administration qui n'ont pas de résultat de retour. Par exemple, la commande suivante appelle une procédure stockée :  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 Le seul type pris en charge retourné à partir d'une procédure stockée dans une instruction `Call` est un ensemble de lignes. La sérialisation pour un ensemble de lignes est définie par XML for Analysis. Si une procédure stockée dans une instruction `Call` retourne un autre type, il est ignoré et n'est pas retourné en XML à l'application appelante. Pour plus d'informations sur les ensembles de lignes de XML for Analysis, consultez Ensembles de lignes de schéma XML for Analysis.  
  
 Si une procédure stockée retourne un ensemble de lignes .NET, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] convertit le résultat sur le serveur en ensemble de lignes XML for Analysis. L'ensemble de lignes XML for Analysis est toujours retourné par une procédure stockée dans la fonction `Call`. Si un dataset contient des fonctionnalités qui ne peuvent pas être exprimées dans l'ensemble de lignes XML for Analysis, un échec se produit.  
  
 Les procédures qui retournent des valeurs void (par exemple, des sous-routines dans Visual Basic) peuvent également être employées avec le mot clé CALL. Si, par exemple, vous souhaitez utiliser la fonction MyVoidFunction() dans une instruction MDX, utilisez la syntaxe suivante :  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
