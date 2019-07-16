---
title: Grammaire de la mise en forme formelle | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91bdf0cfbfe87075d2c9484bca7edd835a950ee6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925349"
---
# <a name="formal-shape-grammar"></a>Grammaire formelle de la commande SHAPE
Il s’agit de la grammaire formelle pour la création de n’importe quelle commande de la forme :  
  
-   Les termes grammaticaux obligatoires sont des chaînes de texte délimités par des crochets pointus (« <> »).  
  
-   Termes facultatifs sont délimités par des crochets (« [] »).  
  
-   Alternatives sont indiquées par une barre verticale («&#124;»).  
  
-   Extensibles alternatives sont indiquées par les points de suspension («... »).  
  
-   *Alpha* indique une chaîne de caractères alphabétiques.  
  
-   *Chiffre* indique une chaîne de nombres.  
  
-   *Chiffres Unicode* indique une chaîne de chiffres unicode.  
  
 Tous les autres termes sont des littéraux.  
  
|Terme|Définition|  
|----------|----------------|  
|\<shape-command>|FORME [\<table-exp > [[AS] \<alias >]] [\<forme-action >]|  
|\<table-exp >|{\<provider-command-text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> TABLE \<quoted-name >&#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|APPEND \<liste de champs d’un alias >&#124;<br /><br /> CALCUL \<liste de champs d’un alias > [BY \<liste de champs >]|  
|\<aliased-field-list>|\<champ d’un alias > [, \<alias-champ... >]|  
|\<aliased-field>|\<champ-exp > [[AS] \<alias >]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp > [[AS] \<alias >]<br /><br /> RELATE \<relation-cond-list >|  
|\<relation-cond-list>|\<cond-relation > [, \<cond-relation >...]|  
|\<relation-cond>|\<nom de champ > TO \<enfant-ref >|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMÈTRE \<-ref param >|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|Somme (\<qualified-champ-name >)&#124;<br /><br /> AVG (\<qualified-champ-name >)&#124;<br /><br /> MIN (\<qualified-champ-name >)&#124;<br /><br /> MAX (\<qualified-champ-name >)&#124;<br /><br /> NOMBRE (\<alias qualifié > &#124; \<nom qualifié >)&#124;<br /><br /> STDEV (\<qualified-champ-name >)&#124;<br /><br /> N’importe quel (\<qualified-champ-name >)|  
|\<calculated-exp>|CALC (\<expression >)|  
|\<qualified-field-name>|\<alias >. [\<alias >...] \<-nom du champ >|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<nom entre guillemets > [[AS] \<alias >]|  
|\<quoted-name>|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<name>|  
|\<qualified-name>|alias [.alias...]|  
|\<name>|alpha [alpha &#124; chiffre &#124; _ &#124; # &#124; : &#124; ...]|  
|\<number>|chiffre [chiffre...]|  
|\<new-exp>|NOUVELLE \<type de champ > [(\<nombre > [, \<nombre >])]|  
|\<field-type>|Un type de données OLE DB ou ADO.|  
|\<string>|Unicode-char [caractères unicode...]|  
|\<expression>|Une expression Visual Basic pour Applications dont les opérandes sont d’autres colonnes non calculées dans la même ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes dans un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Vue d’ensemble de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de forme](../../../ado/guide/data/shape-append-clause.md)   
 [En général, les commandes de forme](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clause COMPUTE de forme](../../../ado/guide/data/shape-compute-clause.md)   
 [Fonctions Visual Basic pour Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
