---
title: transform noise words (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
caps.latest.revision: 43
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 708333809439bcada782b72ce67890dc7b3d5799
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231939"
---
# <a name="transform-noise-words-server-configuration-option"></a>transform noise words (option de configuration de serveur)
  Utilisez le `transform noise words` option de configuration de serveur pour supprimer un message d’erreur si des mots parasites, autrement dit [mots vides](../../relational-databases/search/full-text-search.md), provoquent une opération booléenne sur une requête de recherche en texte intégral retourne zéro ligne. Cette option est utile pour les requêtes de texte intégral qui utilisent le prédicat CONTAINS dans lequel les opérations booléennes ou les opérations de proximité (NEAR) incluent des mots parasites. Les valeurs possibles sont décrites dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Les mots parasites (ou mots vides) ne sont pas transformés. Lorsqu'une requête de texte intégral contient des mots parasites, la requête retourne des lignes nulles, et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un avertissement. Il s'agit du comportement par défaut.<br /><br /> Notez que l’avertissement est un avertissement au moment de l’exécution. Par conséquent, si la clause de texte intégral dans la requête n'est pas exécutée, l'avertissement n'est pas généré. Pour une requête locale, un seul avertissement est généré, même lorsqu'il y a plusieurs clauses de requêtes de texte intégral. Pour une requête distante, le serveur lié peut ne pas relayer l'erreur ; par conséquent, l'avertissement peut ne pas être généré.|  
| 1|Les mots parasites (ou mots vides) sont transformés. Ils sont ignorés, et le reste de la requête est évalué.<br /><br /> Si des mots parasites sont spécifiés dans un terme de proximité, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les supprime. Par exemple, le mot parasite `is` est supprimé de `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, en transformant la requête de recherche en `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`. Notez que `CONTAINS(<column_name>, 'NEAR(hello,is)')` serait transformé en `CONTAINS(<column_name>, hello)` , car il n'existe qu'un seul terme de recherche valide.|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a>Effets du paramètre Transformer les mots parasites  
 Cette section illustre le comportement des requêtes qui contiennent un mot parasite, «`the`», sous les autres paramètres de `transform noise words`.  Il est supposé que les chaînes de la requête de texte intégral de l'exemple sont exécutées par rapport à une ligne de table qui contient les données suivantes : `[1, "The black cat"]`.  
  
> [!NOTE]  
>  Tous ces scénarios peuvent générer un avertissement de mot parasite.  
  
-   Avec transform noise words défini sur 0 :  
  
    |Chaîne de requête|Résultats|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|Aucun résultat (Le comportement est le même pour "`the`" AND "`cat`".)|  
    |"`cat`" NEAR "`the`"|Aucun résultat (Le comportement est le même pour "`the`" NEAR "`cat`".)|  
    |"`the`" AND NOT "`black`"|Aucun résultat|  
    |"`black`" AND NOT "`the`"|Aucun résultat|  
  
-   Avec transform noise words défini sur 1 :  
  
    |Chaîne de requête|Résultats|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|Accès à la ligne portant l'ID 1|  
    |"`cat`" NEAR "`the`"|Accès à la ligne portant l'ID 1|  
    |"`the`" AND NOT "`black`"|Aucun résultat|  
    |"`black`" AND NOT "`the`"|Accès à la ligne portant l'ID 1|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant affecte la valeur `1` à `transform noise words`.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)  
  
  
