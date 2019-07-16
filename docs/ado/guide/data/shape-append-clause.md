---
title: Mettre en forme Clause APPEND | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], APPEND clause
- append clause [ADO]
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e09113b42f655a3b94ab3877ff81f2553a363931
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924181"
---
# <a name="shape-append-clause"></a>Clause APPEND de la commande SHAPE
La clause APPEND de commande shape ajoute une ou plusieurs colonnes à un **Recordset**. Souvent, ces colonnes sont des colonnes de chapitres qui font référence à un enfant **Recordset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list  
```  
  
## <a name="description"></a>Description  
 Les parties de cette clause sont les suivantes :  
  
 *parent-command*  
 Zéro ou un des éléments suivants (vous pouvez omettre le *parent-command* complètement) :  
  
-   Une commande fournisseur entre accolades («{}») qui retourne un **Recordset** objet. La commande est émise au fournisseur de données sous-jacent et sa syntaxe dépend de la configuration requise de ce fournisseur. Ce sera généralement le langage SQL, bien qu’ADO ne nécessite pas de n’importe quel langage de requête spécifique.  
  
-   Une autre commande shape placée entre parenthèses.  
  
-   Le mot-clé TABLE, suivi du nom d’une table dans le fournisseur de données.  
  
 *parent-alias*  
 Alias facultatif qui fait référence au parent **Recordset**.  
  
 *column-list*  
 Un ou plusieurs des opérations suivantes :  
  
-   Une colonne d’agrégation.  
  
-   Une colonne calculée.  
  
-   Une nouvelle colonne créée à l’aide de la nouvelle clause.  
  
-   Une colonne de chapitre. Une définition de colonne chapitre est placée entre parenthèses (« () »). Consultez la syntaxe suivante.  
  
```  
SHAPE [parent-command [[AS] parent-alias]]  
   APPEND (child-recordset [ [[AS] child-alias]   
      RELATE parent-column TO child-column | PARAMETER param-number, ... ])  
   [[AS] chapter-alias]   
   [, ... ]  
```  
  
## <a name="remarks"></a>Notes  
 *child-recordset*  
 -   Une commande fournisseur entre accolades («{}») qui retourne un **Recordset** objet. La commande est émise au fournisseur de données sous-jacent et sa syntaxe dépend de la configuration requise de ce fournisseur. Ce sera généralement le langage SQL, bien qu’ADO ne nécessite pas de n’importe quel langage de requête spécifique.  
  
-   Une autre commande shape placée entre parenthèses.  
  
-   Le nom d’un existant en forme **Recordset**.  
  
-   Le mot-clé TABLE, suivi du nom d’une table dans le fournisseur de données.  
  
 *alias-enfant*  
 Un alias qui fait référence à l’enfant **Recordset**.  
  
 *parent-column*  
 Une colonne dans la **Recordset** retourné par la *parent-command.*  
  
 *child-column*  
 Une colonne dans la **Recordset** retourné par la *commande enfant*.  
  
 *param-number*  
 Consultez [fonctionnement des commandes paramétrées](../../../ado/guide/data/operation-of-parameterized-commands.md).  
  
 *chapter-alias*  
 Un alias qui fait référence à la colonne de chapitre ajoutée au parent.  
  
> [!NOTE]
>  Le *»-colonne parente* TO *-colonne enfant «* clause est en fait une liste, où chaque relation définie est séparée par une virgule  
  
> [!NOTE]
>  La clause après le mot clé APPEND est en fait une liste, où chaque clause est séparée par une virgule et définit une autre colonne à ajouter au parent.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous construisez des commandes de fournisseur à partir de l’entrée d’utilisateur dans le cadre d’une commande SHAPE, SHAPE considère fournie par l’utilisateur une commande fournisseur comme une chaîne opaque et passe fidèlement au fournisseur. Par exemple, dans la commande suivante de la forme,  
  
```  
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 SHAPE exécute deux commandes : `select * from t1` et (`select * from t2 RELATE k1 TO k2)`. Si l’utilisateur fournit une commande composée se compose de plusieurs commandes fournisseur séparées par des points-virgules, forme n’est pas en mesure de distinguer la différence. Dans la commande suivante de la forme,  
  
```  
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 FORME exécute `select * from t1; drop table t1` et (`select * from t2 RELATE k1 TO k2),` sans réaliser que `drop table t1` est distinct et dans cette commande ici, dangereux, fournisseur. Les applications doivent toujours valider les entrées d’utilisateur pour empêcher ces attaques de pirates informatiques potentiels.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Fonctionnement des commandes non paramétrées](../../../ado/guide/data/operation-of-non-parameterized-commands.md)  
  
-   [Fonctionnement des commandes paramétrées](../../../ado/guide/data/operation-of-parameterized-commands.md)  
  
-   [Commandes hybrides](../../../ado/guide/data/hybrid-commands.md)  
  
-   [Clauses COMPUTE intermédiaires de la commande SHAPE](../../../ado/guide/data/intervening-shape-compute-clauses.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
