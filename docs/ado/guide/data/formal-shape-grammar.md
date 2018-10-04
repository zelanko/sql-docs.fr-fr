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
manager: craigg
ms.openlocfilehash: 3b26eaeb804f8d92a7122814641cadf5889b77b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789267"
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
|\<la commande Shape >|FORME [\<table-exp > [[AS] \<alias >]] [\<forme-action >]|  
|\<table-exp >|{\<texte de commande fournisseur >}&#124;<br /><br /> (\<la commande shape >)&#124;<br /><br /> TABLE \<quoted-name >&#124;<br /><br /> \<nom entre guillemets >|  
|\<action de la forme >|APPEND \<liste de champs d’un alias >&#124;<br /><br /> CALCUL \<liste de champs d’un alias > [BY \<liste de champs >]|  
|\<liste de champs d’un alias >|\<champ d’un alias > [, \<champ alias... >]|  
|\<champ d’un alias >|\<champ-exp > [[AS] \<alias >]|  
|\<field-exp>|(\<exp de relation >)&#124;<br /><br /> \<exp calculée >&#124;<br /><br /> \<agrégat-exp >&#124;<br /><br /> \<nouveau exp >|  
|< relation_exp >|\<table-exp > [[AS] \<alias >]<br /><br /> RELATE \<relation-cond-list >|  
|\<relation-cond-list>|\<cond-relation > [, \<cond-relation >...]|  
|\<cond-relation >|\<nom de champ > TO \<enfant-ref >|  
|\<enfant-ref >|\<nom de champ >&#124;<br /><br /> PARAMÈTRE \<-ref param >|  
|\<ref-param >|\<numéro >|  
|\<field-list>|\<nom de champ > [, \<-nom du champ >]|  
|\<aggregate-exp>|Somme (\<qualified-champ-name >)&#124;<br /><br /> AVG (\<qualified-champ-name >)&#124;<br /><br /> MIN (\<qualified-champ-name >)&#124;<br /><br /> MAX (\<qualified-champ-name >)&#124;<br /><br /> NOMBRE (\<alias qualifié > &#124; \<nom qualifié >)&#124;<br /><br /> STDEV (\<qualified-champ-name >)&#124;<br /><br /> N’importe quel (\<qualified-champ-name >)|  
|\<exp calculée >|CALC (\<expression >)|  
|\<nom de champ qualifié >|\<alias >. [\<alias >...] \<-nom du champ >|  
|\<alias >|\<nom entre guillemets >|  
|\<nom de champ >|\<nom entre guillemets > [[AS] \<alias >]|  
|\<nom entre guillemets >|«\<chaîne > »&#124;<br /><br /> '\<chaîne >'&#124;<br /><br /> [\<chaîne >]&#124;<br /><br /> \<Nom >|  
|\<nom qualifié >|alias [.alias...]|  
|\<Nom >|alpha [alpha &#124; chiffre &#124; _ &#124; # &#124; : &#124; ...]|  
|\<numéro >|chiffre [chiffre...]|  
|\<nouveau exp >|NOUVELLE \<type de champ > [(\<nombre > [, \<nombre >])]|  
|\<field-type>|Un type de données OLE DB ou ADO.|  
|\<chaîne >|Unicode-char [caractères unicode...]|  
|\<expression>|Une expression Visual Basic pour Applications dont les opérandes sont d’autres colonnes non calculées dans la même ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes dans un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Vue d’ensemble de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de forme](../../../ado/guide/data/shape-append-clause.md)   
 [En général, les commandes de forme](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clause COMPUTE de forme](../../../ado/guide/data/shape-compute-clause.md)   
 [Fonctions Visual Basic pour Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
