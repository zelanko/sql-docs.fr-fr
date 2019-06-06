---
title: En général les commandes Shape | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], shape commands
ms.assetid: 1fac7831-a187-4b15-9b43-aad380c5556c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f44063e4f1994e01f3685fdb2c7c47a5c41d4998
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704896"
---
# <a name="shape-commands-in-general"></a>Généralités sur les commandes SHAPE
Mise en forme des données définit les colonnes d’une forme **Recordset**, les relations entre les entités représentées par les colonnes et la façon dont le **Recordset** est rempli avec des données.  
  
 Une forme **Recordset** peut se composer des types de colonnes suivants.  
  
|Type de colonne|Description|  
|-----------------|-----------------|  
|données|Champs à partir d’un **Recordset** retournées par une commande de requête à un fournisseur de données, table, précédemment en forme ou **Recordset**.|  
|Chapitre|Une référence à un autre **Recordset**, appelée un *chapitre*. Colonnes de chapitres rendent possible de définir un *parent-enfant* relation où la *parent* est la **Recordset** qui contient la colonne de chapitre et la *enfant* est la **Recordset** représenté par le chapitre.|  
|agrégat|La valeur de la colonne est dérivée en exécutant un *fonction d’agrégation* sur toutes les lignes ou une colonne de toutes les lignes d’un enfant **Recordset**. (Consultez les fonctions d’agrégation dans la rubrique suivante, [fonctions d’agrégation, fonction CALC et le mot clé NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
|expression calculée|La valeur de la colonne est obtenue par le calcul d’une expression Visual Basic pour Applications sur les colonnes dans la même ligne de la **Recordset**. L’expression est l’argument de la fonction CALC. (Consultez Expression calculée dans la rubrique suivante, [fonctions d’agrégation, fonction CALC et le mot clé NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md) et dans [Visual Basic pour Applications Functions](../../../ado/guide/data/visual-basic-for-applications-functions.md).)|  
|new|Champs vides, fabriqués, qui peuvent être remplis avec des données à une date ultérieure. La colonne est définie avec le mot clé NEW. (Consultez le nouveau mot clé dans la rubrique suivante, [fonctions d’agrégation, fonction CALC et le mot clé NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md).)|  
  
 La commande shape peut contenir une clause qui spécifie une commande de requête à un fournisseur de données sous-jacent qui retournera un **Recordset** objet. Syntaxe de la requête dépend de la configuration requise du fournisseur de données sous-jacent. Il s’agit généralement de SQL, bien qu’ADO ne nécessite pas l’utilisation de n’importe quel langage de requête spécifique.  
  
 Commandes Shape peuvent être édités par **Recordset** objets ou en définissant le [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété de la [commande](../../../ado/reference/ado-api/command-object-ado.md) objet, puis en appelant le [Execute ](../../../ado/reference/ado-api/execute-method-ado-command.md) (méthode).  
  
 Vous pouvez utiliser une clause SQL JOIN pour lier les deux tables ; Toutefois, une liste hiérarchique **Recordset** peut représenter les informations plus efficacement. Chaque ligne d’un **Recordset** créé par une jointure d’informations se répète une des tables de façon redondante. Une liste hiérarchique **Recordset** n’a qu’un seul parent **Recordset** pour chacun des enfants plusieurs **Recordset** objets.  
  
 Commandes Shape peuvent être imbriquées. Autrement dit, le *parent-command* ou *commande enfant* ne peut être lui-même une autre commande de forme.  
  
 Le fournisseur shape retourne toujours un curseur client, même lorsque l’utilisateur spécifie un emplacement de curseur **adUseServer**.  
  
 Vous pouvez accéder à la **Recordset** composants de la forme **Recordset** par programmation ou via un contrôle visuel approprié.  
  
 Microsoft fournit un outil visuel qui génère des commandes shape (voir la [données environnement concepteur](https://go.microsoft.com/fwlink/?LinkId=5689) dans la documentation de Visual Basic 6) et une autre qui affiche des curseurs hiérarchiques (voir « à l’aide de la Microsoft hiérarchique Contrôle FlexGrid » dans la documentation de Visual Basic 6).  
  
 Pour plus d’informations sur la navigation dans une liste hiérarchique **Recordset**, consultez [accès aux lignes d’un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 Pour obtenir des informations détaillées sur les commandes de forme correcte, consultez [grammaire formelle de forme](../../../ado/guide/data/formal-shape-grammar.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Fonctions d’agrégation, fonction CALC et mot clé NEW](../../../ado/guide/data/aggregate-functions-the-calc-function-and-the-new-keyword.md)  
  
-   [Émission de commandes vers le fournisseur de données sous-jacent](../../../ado/guide/data/issuing-commands-to-the-underlying-data-provider.md)
