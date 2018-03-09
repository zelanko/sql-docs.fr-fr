---
title: Grammaire de mise en forme formelle | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9eb99feba381701f7e590add3906cd0285b2720
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="formal-shape-grammar"></a>Grammaire de mise en forme formelle
Il s’agit de la grammaire formelle pour la création de n’importe quelle commande de la forme :  
  
-   Les termes grammaticaux obligatoires sont des chaînes de texte délimité par des crochets (« <> »).  
  
-   Termes facultatifs sont délimités par des crochets (« [] »).  
  
-   Alternatives sont indiquées par une barre verticale (« &#124; »).  
  
-   Extensibles alternatives sont indiquées par les points de suspension («... »).  
  
-   *Alpha* indique une chaîne de caractères alphabétiques.  
  
-   *Chiffre* indique une chaîne de nombres.  
  
-   *Chiffres Unicode* indique une chaîne de chiffres unicode.  
  
 Toutes les autres conditions sont des littéraux.  
  
|Terme|Définition|  
|----------|----------------|  
|\<shape-command>|FORME [\<table-exp > [[AS] \<alias >]] [\<forme action >]|  
|\<table-exp>|{\<texte de commande fournisseur >} &#124;<br /><br /> (\<forme-commande >) &#124;<br /><br /> TABLE \<quoted-name > &#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|APPEND \<liste de champs d’un alias > &#124;<br /><br /> COMPUTE \<aliased-field-list> [BY \<field-list>]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<exp calculée > &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<relation-cond-list>|  
|\<relation-cond-list>|\<condition de relation > [, \<conditionnel de relation >...]|  
|\<relation-cond>|\<nom du champ > TO \<enfant-ref >|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMÈTRE \<param-ref >|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM (\<nom de champ qualifié >) &#124;<br /><br /> AVG (\<nom de champ qualifié >) &#124;<br /><br /> MIN (\<nom de champ qualifié >) &#124;<br /><br /> MAX (\<nom de champ qualifié >) &#124;<br /><br /> NOMBRE (\<alias qualifié > &#124; \<nom qualifié >) &#124;<br /><br /> STDEV (\<nom de champ qualifié >) &#124;<br /><br /> ANY(\<qualified-field-name>)|  
|\<calculated-exp>|CALC(\<expression>)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[AS] \<alias>]|  
|\<quoted-name>|"\<string>" &#124;<br /><br /> '\<chaîne >' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<name>|  
|\<qualified-name>|alias [.alias...]|  
|\<name>|alpha [alpha &#124; chiffre &#124; _ &#124; # &#124; : &#124;...]|  
|\<number>|chiffre [chiffres...]|  
|\<new-exp>|NEW \<field-type> [(\<number> [, \<number>])]|  
|\<field-type>|Un type de données OLE DB ou ADO.|  
|\<string>|Unicode-char [unicode-char...]|  
|\<expression>|Une expression Visual Basic pour Applications dont les opérandes sont d’autres colonnes non calculées dans la même ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès aux lignes dans un jeu d’enregistrements hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Vue d’ensemble de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de forme](../../../ado/guide/data/shape-append-clause.md)   
 [En général, les commandes de forme](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clause COMPUTE de forme](../../../ado/guide/data/shape-compute-clause.md)   
 [Fonctions Visual Basic pour Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
