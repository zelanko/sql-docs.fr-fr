---
title: Grammaire de forme formelle | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
author: rothja
ms.author: jroth
ms.openlocfilehash: ce65f6961502a5bfe43278e4a29a11c4210d4af8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758255"
---
# <a name="formal-shape-grammar"></a>Grammaire formelle de la commande SHAPE
Il s’agit de la grammaire formelle pour créer n’importe quelle commande de forme :  
  
-   Les termes de grammaire requis sont des chaînes de texte délimitées par des crochets pointus (« <> »).  
  
-   Les termes facultatifs sont délimités par des crochets ("[]").  
  
-   Les alternatives sont indiquées par un virgule (« &#124; »).  
  
-   Les alternatives répétées sont indiquées par des points de suspension (« ... »).  
  
-   *Alpha* indique une chaîne de lettres alphabétiques.  
  
-   *Digit* indique une chaîne de nombres.  
  
-   *Unicode-digit* indique une chaîne de chiffres Unicode.  
  
 Tous les autres termes sont des littéraux.  
  
|Terme|Définition|  
|----------|----------------|  
|\<> de commande de forme|SHAPE [ \< table-exp> [[As] \< alias>]] [ \< forme-action>]|  
|\<> table-exp|{ \< Provider-Command-text>} &#124;<br /><br /> ( \< Shape-command>) &#124;<br /><br /> \<Nom de la table entre guillemets> &#124;<br /><br /> \<nom entre guillemets>|  
|\<> d’action de forme|Ajouter \< un alias-field-list> &#124;<br /><br /> Compute \< Aliased-field-list> [par \< liste de champs>]|  
|\<> de liste de champs avec alias|\<Aliased-Field> [, \< alias-Field... >]|  
|\<> de champ avec alias|\<Field-exp> [[AS] \< alias>]|  
|\<field-exp>|( \< relation-exp>) &#124;<br /><br /> \<> &#124; calculé-exp<br /><br /> \<agrégat-exp> &#124;<br /><br /> \<New-exp>|  
|<relation_exp>|\<table-exp> [[AS] \< alias>]<br /><br /> \<Relation entre relations-cond-list>|  
|\<relation-cond-list>|\<relation-cond> [, \< relation-cond>...]|  
|\<relation-cond>|\<> de nom de champ en \<> de référence enfant|  
|\<> de référence enfant|\<nom de champ> &#124;<br /><br /> PARAMÈTRE \< param-ref>|  
|\<Param-Ref>|\<nombre>|  
|\<field-list>|\<Field-name> [, \< Field-name>]|  
|\<aggregate-exp>|SUM ( \< Qualified-Field-name>) &#124;<br /><br /> AVG ( \< Qualified-Field-name>) &#124;<br /><br /> &#124; MIN ( \< Qualified-Field-name>)<br /><br /> MAX ( \< Qualified-Field-name>) &#124;<br /><br /> COUNT ( \< Qualified-alias> &#124; \< Qualified-Name>) &#124;<br /><br /> ECARTYPE ( \< Qualified-Field-name>) &#124;<br /><br /> ANY ( \< Qualified-Field-name>)|  
|\<> calculé-exp|CALC ( \< expression>)|  
|\<Qualified-Field-name>|\<> d’alias. [ \< alias>...] \< nom de champ>|  
|\<alias>|\<nom entre guillemets>|  
|\<nom de champ>|\<quoted-Name> [[AS] \< alias>]|  
|\<nom entre guillemets>|\<&#124; string><br /><br /> \<&#124; « string> »<br /><br /> [ \< string>] &#124;<br /><br /> \<nom>|  
|\<nom qualifié>|alias [. alias...]|  
|\<nom>|alpha [chiffre &#124; alpha &#124; _ &#124; # &#124; : &#124;...]|  
|\<nombre>|chiffre [chiffre...]|  
|\<New-exp>|NEW \< Field-type> [( \< Number> [, \< Number>])]|  
|\<field-type>|Type de données OLE DB ou ADO.|  
|\<> de chaîne|Unicode-Char [Unicode-char...]|  
|\<expression>|Expression Visual Basic pour Applications dont les opérandes sont d’autres colonnes non CALCULées dans la même ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes d’un jeu d’enregistrements hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Présentation de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de la forme](../../../ado/guide/data/shape-append-clause.md)   
 [Mettre en forme les commandes en général](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape Compute, clause](../../../ado/guide/data/shape-compute-clause.md)   
 [Fonctions Visual Basic pour Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
